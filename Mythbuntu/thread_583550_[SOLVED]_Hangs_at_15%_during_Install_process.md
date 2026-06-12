---
title: "[SOLVED] Hangs at 15% during Install process"
date: 2007-10-20
forum: Mythbuntu
---

### Post by johnsto on 2007-10-20
I'm trying to install Mythbuntu 7.10 on a VIA M10000 via a DVD drive.

Problem is, it keeps hanging at 15% during the installation, as it hits the "Detecting drives" stage!

I've left it for up to an hour and it didn't move a bit. Also tried using the guided partitioner and also the manual one. Memory and HDD checked, neither have any errors. Tried partitioning and formatting the HDD in the terminal before install, but of course the installer insists on reformatting it... which I think might be the problem.

System goes very slow on the run up to 15%, so it's hard to switch to a console and get any debug output, unfortunately :(

Any ideas?

---

### Post by ghostwalker50 on 2007-10-21
some with me. i redownloaded an new image. than might help...

---

### Post by johnsto on 2007-10-21
Not sure how that would help. I've already verified my ISO is correct using the md5sum. In addition, I've tried installing both off a burnt DVD, and also from a usb stick, and had the same problem each time. 

So I don't think it's the source media.

---

### Post by artir on 2007-10-21
Same happened to me. Maybe its because i dont have /dev/sda1 in ntfs(windows partition)
I waites 3 hours!! and then ow! it was intalling. yeah! another half hour  and i got my gutsy installed. Im going to file a bug against ubiquity!

---

### Post by johnsto on 2007-10-21
Ok, well I'm going to leave it running until lunchtime. Right now it's sat at 15%, accessing the DVD drive every 4 or 5 seconds. Over and over again!

---

### Post by johnsto on 2007-10-21
Looks like it's running out of memory:

```
[43707.812000] ubiquity invoked oom-killer: gfp_mask=0x201d2, order=0, oomkilladj=0
[43707.812000]  [<c0161f65>] out_of_memory+0x185/0x1c0
[43707.812000]  [<c0163934>] __alloc_pages+0x2e4/0x340
[43707.812000]  [<ce890bb7>] atapi_output_bytes+0x27/0x60 [ide_core]
[43707.812000]  [<c01653d9>] __do_page_cache_readahead+0x109/0x250
[43707.812000]  [<ce8eee81>] ide_do_rw_cdrom+0x4c1/0x660 [ide_cd]
[43707.812000]  [<c01610a5>] filemap_nopage+0x155/0x340
[43707.812000]  [<ce88f5b0>] ide_do_request+0x410/0xa00 [ide_core]
[43707.812000]  [<c016ccd8>] __handle_mm_fault+0x148/0xb00
[43707.812000]  [<c010320a>] __switch_to+0xaa/0x1d0
[43707.812000]  [<c02f5b36>] do_page_fault+0x126/0x690
[43707.812000]  [<c0140326>] do_gettimeofday+0x36/0x100
[43707.812000]  [<c02f5a10>] do_page_fault+0x0/0x690
[43707.812000]  [<c02f4292>] error_code+0x72/0x80
[43707.812000]  =======================
[43707.812000] Mem-info:
[43707.812000] DMA per-cpu:
[43707.812000] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
[43707.812000] Normal per-cpu:
[43707.812000] CPU    0: Hot: hi:   90, btch:  15 usd:  33   Cold: hi:   30, btch:   7 usd:   6
[43707.812000] Active:23935 inactive:16501 dirty:0 writeback:0 unstable:0
[43707.812000]  free:679 slab:2858 mapped:24 pagetables:464 bounce:0
[43707.812000] DMA free:956kB min:136kB low:168kB high:204kB active:2448kB inactive:88kB present:16256kB pages_scanned:26180 all_unreclaimable? yes
[43707.812000] lowmem_reserve[]: 0 206 206
[43707.812000] Normal free:1760kB min:1764kB low:2204kB high:2644kB active:93292kB inactive:65916kB present:211268kB pages_scanned:456268 all_unreclaimable? yes
[43707.812000] lowmem_reserve[]: 0 0 0
[43707.812000] DMA: 1*4kB 1*8kB 1*16kB 1*32kB 0*64kB 1*128kB 1*256kB 1*512kB 0*1024kB 0*2048kB 0*4096kB = 956kB
[43707.812000] Normal: 0*4kB 0*8kB 4*16kB 1*32kB 0*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1760kB
[43707.812000] Swap cache: add 27090, delete 27090, find 483/771, race 0+0
[43707.812000] Free swap  = 0kB
[43707.812000] Total swap = 0kB
[43707.812000] Free swap:            0kB
[43707.828000] 57328 pages of RAM
[43707.828000] 0 pages of HIGHMEM
[43707.828000] 1539 reserved pages
[43707.828000] 12449 pages shared
[43707.828000] 0 pages swap cached
[43707.828000] 0 pages dirty
[43707.828000] 0 pages writeback
[43707.828000] 24 pages mapped
[43707.828000] 2858 pages slab
[43707.828000] 464 pages pagetables
```

I guess 256MB (minus 32MB for video) just isn't enough.

---

### Post by johnsto on 2007-10-21
...although, thinking about it, if there's a process that keeps sucking up memory, even if I upgrade to 4GB, it'll still fail :confused:

---

### Post by superm1 on 2007-10-21
You may consider adding your logs from /var/log/installer on the resultant system to this bug:

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/155280](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/155280)

---

### Post by johnsto on 2007-10-21
Think that might be a slightly different issue. My installer logs don't give any indication of failure or error at all beyond normal debugging output. Only the kernel output shows any problems.

I've got more memory on the way, so if that fixes the problem, hopefully we'll know that was the issue. 

If that doesn't work, I'll pop this into launchpad as advised.

---

### Post by johnsto on 2007-10-25
Well I popped in 512MB today, and it worked like a charm first time. Stopped only at 15% for about 10 seconds, and then started formatting the drive. 

Exact same settings as had failed upteen times during the weekend.

So anyone else having this problem - make sure you have at least 512MB of RAM!

---

