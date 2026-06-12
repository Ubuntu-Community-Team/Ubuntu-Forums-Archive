---
title: "Karmic and MTRR"
date: 2009-11-23
forum: Multimedia Software
---

### Post by instant on 2009-11-23
Hi guys!

I've just made a fresh installation of ubuntu 9.10 and it seems that my old friend the mtrr-issue is back.

Surprisingly I haven't found any relevant information regarding this in Karmic, is there really no one out there with the same issue?

Tried reverting back to GRUB legacy and adding the enable_mtrr_cleanup flag but to no avail. Any other ideas?

I also tried running the fixmtrr.sh script but that didn't work either.

cat /proc/mtrr shows:

```

reg00: base=0x0c0000000 ( 3072MB), size= 1024MB, count=1: uncachable
reg01: base=0x000000000 (    0MB), size= 4096MB, count=1: write-back
reg02: base=0x100000000 ( 4096MB), size= 1024MB, count=1: write-back
reg03: base=0x0bf700000 ( 3063MB), size=    1MB, count=1: uncachable
reg04: base=0x0bf800000 ( 3064MB), size=    8MB, count=1: uncachable
```

As you can see no write-combining.

I'm sorry to say this really pisses me off since I love ubuntu.

Hope someone can help me.

/instant

---

### Post by Tobis87 on 2010-01-15
Hi,

Run this script:
```
#!/bin/sh
address=`lspci -v \
	| grep -A 7 VGA\
	| grep -F " prefetchable"\
	| awk 'BEGIN{OFS="";ORS=""}
	      {print $3
	      i = length($3)
	      while(i<8){
	      		print 0
	       		i++
	       }}'`

hsize=`lspci -v \
	| grep -A 7 VGA \
	| grep -F " prefetchable" \
	| awk '{print $6}' \
	| sed 's/[^0-9]//g' \
	| awk 'BEGIN {OFS = "";ORS=""}
	       { printf "%x" , $1
		 i = length($1)
		 while (i<8) {
		 	print 0
		 	i++
		 } }'`

echo "base=0x$address size=0x$hsize type=write-combining"
```

And add the detected write-combing area to this boot script:
```
#! /bin/sh
echo "disable=0" > /proc/mtrr
echo "disable=1" > /proc/mtrr
echo "base=0x00000000 size=0x80000000 type=write-back" >| /proc/mtrr
echo "base=0x80000000 size=0x40000000 type=write-back" >| /proc/mtrr
echo "base=DETECTED size=DETECTED type=write-combining" >| /proc/mtrr
```

---

