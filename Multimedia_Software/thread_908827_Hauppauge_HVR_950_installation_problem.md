---
title: "Hauppauge HVR 950 installation problem"
date: 2008-09-02
forum: Multimedia Software
---

### Post by jacobcolbert on 2008-09-02
Hi, I know there have been many topics on this, but I have been unable to resolve my problems with any posts or googling. I recently installed the HVR 950 following these instructions [http://u32.net/MythTV/WinTV-HVR-950/](http://u32.net/MythTV/WinTV-HVR-950/) I have tried hooking it up to analog cable and the component input (both the output of a fios box) I then tried testing it with TvTime. The analog cable does not work at all (scanning finds no channels, and channel 3, the one that it should work on is blank). Switching to component, the video is fine, but there is no audio. I know this is a common problem, but the conventional sox fix didn't work. This is because /dev/dsp1 doesn't exist. A lot of this seems partially explained by the results of dmesg|grep -A 5 -B 5 TV

```
[   32.928877] AC97 audio (5 sample rates)
[   32.928880] 500mA max power
[   32.928882] Table at 0x24, strings=0x1e82, 0x186a, 0x0000
[   32.943994] tveeprom 0-0050: Hauppauge model 65201, rev A1C0, serial# 1915368
[   32.944001] tveeprom 0-0050: tuner model is Xceive XC3028 (idx 120, type 71)
[   32.944008] tveeprom 0-0050: TV standards PAL(B/G) PAL(I) PAL(D/D1/K) ATSC/DVB Digital (eeprom 0xd4)
[   32.944013] tveeprom 0-0050: audio processor is None (idx 0)
[   32.944016] tveeprom 0-0050: has radio
[   33.013322] intel8x0_measure_ac97_clock: measured 54139 usecs
[   33.013328] intel8x0: clocking to 48000
[   33.018770] tuner' 0-0061: chip found @ 0xc2 (em28xx #0)
--
[   33.855257] cs: IO port probe 0x820-0x8ff: clean.
[   33.855734] cs: IO port probe 0xc00-0xcf7: clean.
[   33.856535] cs: IO port probe 0xa00-0xaff: clean.
[   33.923538] tvp5150 0-005c: tvp5150am1 detected.
[   34.071755] em28xx #0: V4L2 device registered as /dev/video0 and /dev/vbi0
[   34.071759] em28xx #0: Found Hauppauge WinTV HVR 950
[   34.071784] usbcore: registered new interface driver em28xx
[   34.337389] xc2028 0-0061: attaching existing instance
[   34.337394] xc2028 0-0061: type set to XCeive xc2028/xc3028 tuner
[   34.337396] em28xx #0/2: xc3028 attached
[   34.337398] DVB: registering new adapter (em28xx #0)

```

The audio processor is None. And it seems to not be able to process NTSC, like an analog cable source. Any advice or links would be greatly appreciated!

Also, i plan on setting up MythTV once i eventually get this working, so any general links on setting that up too would be great as well. :)

---

### Post by jacobcolbert on 2008-09-03
Just curious if anyone has any ideas. Been searching all day, but can't find anything.

---

### Post by jacobcolbert on 2008-09-04
I tried again using the instructions from [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950), using the linuxtv drivers. Now the analog video works, but it is still without sound. I tried the instructions here, [http://ubuntuforums.org/showthread.php?t=763249](http://ubuntuforums.org/showthread.php?t=763249), but when i do sudo cat /proc/asound/cards all i see is ```
 0 [ICH6           ]: ICH4 - Intel ICH6

                      Intel ICH6 with unknown codec at irq 18
```
So it is clearly no sound device is installed at all. Thanks for any help you can provide.

---

### Post by kirkster86 on 2008-09-16
> **jacobcolbert said:**
> I tried again using the instructions from [http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950](http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-950), using the linuxtv drivers. Now the analog video works, but it is still without sound. I tried the instructions here, [http://ubuntuforums.org/showthread.php?t=763249](http://ubuntuforums.org/showthread.php?t=763249), but when i do sudo cat /proc/asound/cards all i see is ```
 0 [ICH6           ]: ICH4 - Intel ICH6

                      Intel ICH6 with unknown codec at irq 18
```
So it is clearly no sound device is installed at all. Thanks for any help you can provide.


I'm having the exact same problem that you are. I tried in July to get it to work, but couldn't. I broke it out again last night using the website that you used first, but to no avail.

---

