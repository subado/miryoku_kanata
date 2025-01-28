# Copyright 2021 Manna Harbour
# https://github.com/manna-harbour/miryoku

source := $(wildcard *.kbd.cpp)

targets := $(source:%.kbd.cpp=build/%.kbd)

all: $(targets)

build/%.kbd: %.kbd.cpp FORCE
	cpp -P $(OPT_DEFS) $< | \
	sed \
	  -e "s/U_QUOT/'/g" \
	  -e "s/U_DQUO/S-'/g" \
	  -e 's/U_COMM/,/g' \
	  -e 's/U_LPRN/S-9/g' \
	  -e 's/U_RPRN/S-0/g' \
	  -e 's/U_PIPE/S-Backslash/g' \
	  -e 's/U_BKSL/Backslash/g' \
		-e 's/U_APSD/S-7/g' \
		-e 's/U_ASRK/S-8/g' \
		-e 's/U_COLN/S-;/g' \
		-e 's/U_DLLR/S-4/g' \
		-e 's/U_PERC/S-5/g' \
		-e 's/U_CRET/S-6/g' \
		-e 's/U_TLDA/S-`/g' \
		-e 's/U_EXCL/S-1/g' \
		-e 's/U_AT/S-2/g' \
		-e 's/U_HASH/S-3/g' \
		-e 's/U_USCR/S--/g' \
		-e 's/U_LBRK/S-[/g' \
		-e 's/U_RBRK/S-]/g' \
	  -e 's/[ ]*U_LF[ ]*/\n/g' \
	  -e 's/[ ]*U_TAB[ ]*/\t/g' \
	 > $@

FORCE: ;

test: build/miryoku_kanata.kbd
	kanata --check -c $<

include custom_rules.mk

include post_rules.mk
