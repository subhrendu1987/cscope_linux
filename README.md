# Configure cscope

## Prerequisties and Assumptions
* cscope installed `sudo apt install cscope`
* Download Linux kernel from [here](https://www.kernel.org/)
* Kernel sources directory `/home/subhrendu/linux-5.18.5`
* cscope config directory `/home/subhrendu/cscope`

## Start configuration
Use the following commands to configure cscope
* `LNX=/home/subhrendu/linux-5.18.5`
* `CSCOPE_REPO=/home/subhrendu/cscope/`
* `mkdir -p $CSCOPE_REPO`
* `cd /`
* `find  $LNX                                                                \
	-path "$LNX/arch/*" ! -path "$LNX/arch/i386*" -prune -o               \
	-path "$LNX/include/asm-*" ! -path "$LNX/include/asm-i386*" -prune -o \
	-path "$LNX/tmp*" -prune -o                                           \
	-path "$LNX/Documentation*" -prune -o                                 \
	-path "$LNX/scripts*" -prune -o                                       \
	-path "$LNX/drivers*" -prune -o                                       \
        -name "*.[chxsS]" -print > "$CSCOPE_REPO/cscope.file"`
* `cat "$CSCOPE_REPO/cscope.file"`
* `cd "$CSCOPE_REPO"`
* `cscope -b -q -k -i cscope.file`


### For other Projects
`find /my/project/dir -name '*.java' >/my/cscope/dir/cscope.files`