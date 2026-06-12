---
title: "Copying DVD [not ripping]"
date: 2009-04-14
forum: Multimedia Software
---

### Post by neon100 on 2009-04-14
If i have some CD or DVD with a lot of scratches then it makes it difficult to copy. In windows, i would simply make a briefcase. and copy the video file into it. The file would be copied till it can read from CD/DVD. If the DVD gets a little warmer during the copying then it makes it difficult to read the scratched parts. So i would give the rom some break and copy same file in same briefcase. It would start copying from where it left the file.

 But in Ubuntu the file is copied till the CD is readable. and  reading the scratched part is difficult because when i start copying again from start, the CD gets warmer and it stops when it reaches the scratched part of CD. Here if the CD cooler then it would be easier to copy. 

Any solution in Ubuntu?

---

### Post by cariboo on 2009-04-14
Have you tried making an .iso of the cd/dvd? Open an Applications-->Accessories-->Terminal and type:

```
sudo dd if=/dev/scd0 of=copy.iso
```

the above command will create an iso image of the cd /dvd.

Jim

---

### Post by mc4man on 2009-04-14
You may also try dvdisaster
While the intent of it is to create ecc files prior to a dvd or cd becoming damaged, it can be used in just the read mode to dump an .iso

By default it will just try 1 read retry per sector which is good for the first pass.

If there are unreadable sectors running dvddisaster again will only attempt to read the sectors skipped previously, not the whole disk.

For subsequent attempts you could up the re tries to 5 -10 attempts, you can re run as many times as you wish.

It also by default will not read commercial dvd's, though there is a workaround there.

For commercial dvd's (dvd movies) you need to authenticate the drive first. This is done by first opening the disk in a player, pausing, then opening dvdisaster, then closing the player.

The first time you use it there will be a pop up about rs02, you want to skip/cancel that

---

### Post by 0cton on 2009-04-14
Hm maybe using a software (brasero,K3B)to copy it as an image
and put the read speed at lowest witch will guarantee a good copying and no overheat (just an idea)
edit: apparently i havent saw there were alreayd replies :P
i opened the thread went to eat and came back and posted hehe it ended up funny :P

---

### Post by neon100 on 2009-04-14
sugesstions are good but i dont want to make ISO. it just lengthens the process?
Isnt there any software which is _expert in copying scratched CDs_ *without* making ISO or any other format.

---

### Post by neon100 on 2009-04-14
i found ddrescue. Its a good software. But i dont know how to use its options. I found following somewhere on internet

Options

-h, --help
    display this help and exit 
-V, --version
    output version information and exit 
-b, --block-size=<bytes>
    hardware block size of input device [512] 
-B, --binary-prefixes
    show binary multipliers in numbers [default SI] 
-c, --cluster-size=<blocks>
    hardware blocks to copy at a time [128] 
-C, --complete-only
    do not read new data beyond logfile limits 
-d, --direct
    use direct disc access for input file 
-D, --synchronous
    use synchronous writes for output file 
-e, --max-errors=<n>
    maximum number of error areas allowed 
-F, --fill=<types>
    fill given type areas with infile data (?*/-+) 
-g, --generate-logfile
    generate approximate logfile from partial copy 
-i, --input-position=<pos>
    starting position in input file [0] 
-n, --no-split
    do not try to split or retry error areas 
-o, --output-position=<pos>
    starting position in output file [ipos] 
-q, --quiet
    quiet operation 
-r, --max-retries=<n>
    exit after given retries (-1=infinity) [0] 
-R, --retrim
    mark all error areas as non-trimmed 
-s, --max-size=<bytes>
    maximum size of data to be copied 
-S, --sparse
    use sparse writes for output file 
-t, --truncate
    truncate output file 
-v, --verbose
    verbose operation



can somebody write some example of full command with paths using any of these options? please write with --r option.

---

