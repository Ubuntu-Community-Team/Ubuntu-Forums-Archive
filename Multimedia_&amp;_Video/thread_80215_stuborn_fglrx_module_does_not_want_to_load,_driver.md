---
title: "stuborn fglrx module does not want to load, driver 8.18 ATI Mobility 9700SE"
date: 2005-10-21
forum: Multimedia &amp; Video
---

### Post by BungaMan on 2005-10-21
Normally X wouldn't start but by adding ChipID 0x4E50 it loads and gives me 1280X800 so I'm happy as far as 2D is concerned
3D is a different story
I've tried the hexedit driver hack to replace 4E52 by 4E50 in file libfglrx_ip.a.GCC3 but it cannot find 4E52 so maybe all attempts are useless after all because there is no support?  Though it is able to find 4E50...

xorg log:
```

(II) fglrx(0): doing DRIScreenInit
[drm] failed to load kernel module "fglrx"
(II) fglrx(0): [drm] drmOpen failed
(EE) fglrx(0): DRIScreenInit failed!
(WW) fglrx(0): ***********************************************
(WW) fglrx(0): * DRI initialization failed!                  *
(WW) fglrx(0): * (maybe driver kernel module missing or bad) *
(WW) fglrx(0): * 2D acceleraton available (MMIO)             *
(WW) fglrx(0): * no 3D acceleration available                *
(WW) fglrx(0): ********************************************* *

```
lspci```

lspci | grep ati
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10]
lspci -n
0000:01:00.0 0300: 1002:4e52

```
fglrx module is not loaded while running X
lsmod | grep fglrx shows nothing

In the attachment you can find my xorg.conf, you'll find the option NoDRI on but it doesn't make a difference if this is on or off or commented out :(
My portable is a Fujitsu-Siemens Amilo M1424 and I'm about to kill ATI for their great linux driver.  Do they still think there's just a few 100 using linux???

small edit for the completeness:
dmesg shows
```

[4294832.417000] [fglrx] Maximum main memory to use for locked dma buffers: 432 MBytes.
[4294832.417000] [fglrx:firegl_init] *ERROR* Device not found!

```
and modprobe
```

sudo modprobe fglrx
FATAL: Error inserting fglrx (/lib/modules/2.6.12-9-386/kernel/drivers/char/drm/fglrx.ko): No such device

```
One more thing, I don't know if this is important but the ATI Control panel works fine but of course shows Mesa for OpenGL

---

### Post by BungaMan on 2005-10-23
anyone with a suggestion? something that can help me 1 step further? with a working driver and the same laptop?

---

### Post by BungaMan on 2005-10-25
Is there anyone who has 3D working on a mobility 9700SE (procid aka chipid 4E52)?  If so I'd like to receive a copy of your fglrx driver.

---

### Post by Zeroedout on 2005-10-26
go to /usr/share/fglrx and open fglrx-install.log with gedit or whatever, and see if their are any errors when compiling the module. If you cant comprehend the file, just post it here and i'll see if i can spot the error. Whenever i've had a problem with fglrx, it's always been a problem with compilation.

---

### Post by BungaMan on 2005-10-27
Tfor the help but I've got it working now.  The compilation was already correct.  lspci finds 4E52 so it searches for this in the driver but couldn't find it before the hexedit.  I tried to replace 4E52 with 4E50 which was of course the reverse of what I was supposed to do :p

---

### Post by scoica on 2005-11-02
hi about your solved problem can you tell me how can I solve mine? I have the same problem

lspci | grep ATI
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 02)

lspci -n
..
01:00.0 Class 0300: 1002:4c66 (rev 02)
...

can you tell me please what to do next?
thank you

---

### Post by BungaMan on 2005-11-02
On this site you can check for a chipid that is compatible with the card you have:
[http://pci-ids.ucw.cz/iii//?i=1002](http://pci-ids.ucw.cz/iii//?i=1002)

Once you found your compatible chipid you can hexedit (not the best prog but you can try ghex2) the file under /lib/modules/fglrx/build_mod/lib...something...GCC3 (i'm typing this out of my head).  Search for that chipid in the file (ex. 4C65) and replace it with 4C66.  You should find the id close to the end of the file.  Also search switching the first two with the last two (654C according to our example) depending on little endian or big endian.

then recompile et voila

---

### Post by Cuppa-Chino on 2005-11-02
[QUOTE=BungaMan]On this site you can check for a chipid that is compatible with the card you have:
[http://pci-ids.ucw.cz/iii//?i=1002](http://pci-ids.ucw.cz/iii//?i=1002)

Once you found your compatible chipid you can hexedit (not the best prog but you can try ghex2) the file under /lib/modules/fglrx/build_mod/lib...something...GCC3 (i'm typing this out of my head).  Search for that chipid in the file (ex. 4C65) and replace it with 4C66.  You should find the id close to the end of the file.  Also search switching the first two with the last two (654C according to our example) depending on little endian or big endian.

then recompile et voila[/QUOTE]

thanks for this BungaMan - unfortunately it does not help me (I have a similar problem [http://ubuntuforums.org/showthread.php?t=84680](http://ubuntuforums.org/showthread.php?t=84680) ) and cannot execute your idea form above

a) where do I find that file in Breezy, just do not have any luck
b) do I replace all of the entry's that match my card currently radeon 9500 (pro) AD 4144 and I want to change to radeon 9700 (pro) AE 4145 or 4146 AF
I presumably also have to replace the secondary 4164 with the equivalent 4165/4166

how do I recompile afterwards?

---

### Post by Cuppa-Chino on 2005-11-02
I have seen in some forums that cards are overwritten by editing /etc/X11/xorg.conf and inserting a ChipID into that has anybody had any success with this?

from [http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_9800xt](http://odin.prohosting.com/wedge01/gentoo-radeon-faq.html#4_9800xt)

[FONT=Verdana][SIZE=2]**_Question 4.12_**: *[COLOR=Red]I have a Radeon 9800XT, and direct rendering doesn't work. How can I fix it?[/COLOR]*
The current versions of the driver appear to have problems with the 9800 XT, possibly because it's a relatively new card. This problem may be indicated by all 3D programs failing with a "Trace/breakpoint trap" message on startup. Until ATI fixes the driver, the best solution seems to be to add the following line to the "Device" section of your [FONT=Courier][COLOR=Blue]/etc/X11/XF86Config-4[/COLOR][/FONT] file: 
[FONT=Courier][COLOR=Purple]ChipID	0x4e48[/COLOR][/FONT]
and restart X.
What this does is override the chipset ID autodetection mechanism, which is normally how the type of card you have is determined. Adding this setting forces your card to be treated as a Radeon 9800/9800 Pro. This does not seem to have any impact on performance, and should allow you to run 3D applications normally.
**UPDATE:** I believe this problem should be fixed in all recent driver versions.  [/SIZE][/FONT]

---

### Post by BungaMan on 2005-11-03
This is only when lspci shows you something like "Unknown VGA-compatible card".
The hexedit is in case your card is not supported by the driver but it does contain a compatible card.  Ex. mine is 4E52, 4E50 is compatible with my card so I changed the 4E50 entry in the driver with 4E52.  That of course makes my custom driver not support 4E50 anymore but I don't have to care about that :)

---

### Post by Cuppa-Chino on 2005-11-03
managed to get it to work (at least using the fglrxconfig produced xorg.conf file) as per instructions added:

rather towards the end of the file, I added the ChipID:
    BusID "PCI:1:0:0"    # vendor=1002, device=4144
    **_ChipID 0x4E45_**  

it has worked because now ATI - Panel recognises my card as a radeon 9700 and my fps have increased:> ~$ glxgears -printfps
17527 frames in 5.0 seconds = 3505.246 FPS
17717 frames in 5.0 seconds = 3543.341 FPS
17718 frames in 5.0 seconds = 3543.481 FPS
17716 frames in 5.0 seconds = 3543.020 FPS
17718 frames in 5.0 seconds = 3543.590 FPS

had been in the 2600range as radeon 9500 with 8.18.08 ati driver before

---

### Post by mg_x on 2005-11-19
**BungaMan**
I edited lib*.GCC3 file, and it helped.
 - Glxinfo shows:"Direct Rendering: Yes"
- X.logs contains: "DRI successfuly installed"
- etc. Everything seems to be OK.

**HOWEVER** when i run 3D app then X process is eating CPU (70%, 80%).. Games
are not playable, moving mouse is very hard...

Do you have the same symptoms?

Regards
mg_x

---

### Post by BungaMan on 2005-12-12
[QUOTE=mg_x]**BungaMan**
I edited lib*.GCC3 file, and it helped.
 - Glxinfo shows:"Direct Rendering: Yes"
- X.logs contains: "DRI successfuly installed"
- etc. Everything seems to be OK.

**HOWEVER** when i run 3D app then X process is eating CPU (70%, 80%).. Games
are not playable, moving mouse is very hard...

Do you have the same symptoms?

Regards
mg_x[/QUOTE]
I'm off internet for a while hence the late reply :(
One thing you have now is a working fglrx driver, next you have to check if X loads it and if it is using the driver to render 3D iso the mesa library.  It is probably using mesa which would explain the heavy load.  There is enough info on this forum to fix that so a little search and a lot of reading will help you I hope :)

---

