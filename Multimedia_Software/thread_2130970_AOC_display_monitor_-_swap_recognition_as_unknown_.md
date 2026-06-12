---
title: "AOC display monitor - swap recognition as unknown and as AOC"
date: 2013-03-31
forum: Multimedia Software
---

### Post by sp3cktator on 2013-03-31
Hello forum,

I recently bought a AOC E2250swnk LED Monitor 21,5''. 
Ubuntu started but in 1280x768 resolution.
I opened displays menu to change the resolution and then the monitor started to blink once in 1920x1080 and right away changed back to 1280.... after 8-9 resolution swaps, stopped in 1920. Note that every time i reboot it does the same and sometimes stops at 1280x768 too.
During these changes i noticed that when 1280 was applied the monitor was recognized as "unknown" and when 1920 was... ubuntu recognized the monitor as AOC 22" which is the correct model name.

Anybody knows how to fix this?

thnx in advance.

Edit: My Ubutntu version is 12.04LTS and Video Card is ATI 5770

---

### Post by cwsnyder on 2013-03-31
It sounds like sometimes your monitor EDID is not read properly by the Video card, or your video card is losing it.  You could try a different video cable and see if that fixes things (or at least check the connections between the video card and monitor).  Your video card could be having problems (check to make sure the video card is seated properly if it is a desktop machine).  Or you could try reading this thread: [http://ubuntuforums.org/showthread.php?t=2008395](http://ubuntuforums.org/showthread.php?t=2008395) to correct your EDID.

You can try  the Linux terminal commands  in [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution) to fix it temporarily, or write a shell script from that guidance in which you include the full path to the script in your startup commands, as well.

---

### Post by sp3cktator on 2013-03-31
thnx a lot cwsnyder!!

You were right! 

I tried the method you said before and it worked but i also tried to change the cable and it was fixed.

For the record, that was my syslog...

```
kernel: [ 3789.699445] radeon 0000:01:00.0: DVI-I-2: EDID block 0 invalid.kernel: [ 3789.699452] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
kernel: [ 3789.796017] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 112
kernel: [ 3789.796020] Raw EDID:
kernel: [ 3789.796022]      00 ff ff ff ff ff ff 00 05 e7 ff ff ff ff ff ff
kernel: [ 3789.796024]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796025]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796026]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796027]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796029]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796030]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.796031]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847220] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 157
kernel: [ 3789.847222] Raw EDID:
kernel: [ 3789.847222]      00 ff ff ff ff ff ff 00 05 e3 50 22 00 00 00 00
kernel: [ 3789.847224]      00 15 01 03 68 30 1b 78 2a 9d 80 a2 59 54 9e 27
kernel: [ 3789.847225]      0e 50 54 bf ef 00 a3 ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847226]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847227]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847228]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847230]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.847231]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.898421] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 34
kernel: [ 3789.898422] Raw EDID:
kernel: [ 3789.898423]      00 ff ff ff ff ff ff 00 05 e3 50 22 00 00 00 00
kernel: [ 3789.898425]      00 15 01 03 68 30 1b 78 2a 9d 80 a2 59 54 9e 27
kernel: [ 3789.898426]      0e 50 54 bf ef 00 d1 c0 b3 00 95 00 81 80 81 40
kernel: [ 3789.898427]      83 ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.898428]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.898429]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.898431]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.898432]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950186] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 147
kernel: [ 3789.950188] Raw EDID:
kernel: [ 3789.950189]      00 ff ff ff ff ff ff 00 05 e3 50 22 00 00 00 00
kernel: [ 3789.950190]      00 15 01 03 68 30 1b 78 2a 9d 80 a2 59 54 9e 27
kernel: [ 3789.950191]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950192]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950194]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950195]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950196]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950197]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3789.950201] radeon 0000:01:00.0: DVI-I-2: EDID block 0 invalid.
kernel: [ 3789.950203] [drm:radeon_dvi_detect] *ERROR* DVI-I-2: probed a monitor but no|invalid EDID
kernel: [ 3790.050199] [drm:drm_edid_block_valid] *ERROR* EDID checksum is invalid, remainder is 226
kernel: [ 3790.050202] Raw EDID:
kernel: [ 3790.050204]      00 ff ff ff ff ff ff 00 05 e3 50 22 01 ff ff ff
kernel: [ 3790.050205]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050206]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050207]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050209]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050210]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050211]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
kernel: [ 3790.050212]      ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
```

---

