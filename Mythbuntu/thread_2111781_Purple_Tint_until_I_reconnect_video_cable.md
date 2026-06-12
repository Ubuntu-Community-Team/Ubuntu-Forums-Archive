---
title: "Purple Tint until I reconnect video cable"
date: 2013-02-02
forum: Mythbuntu
---

### Post by kingmoocow on 2013-02-02
I've been googling for a while trying to figure this one out to no avail, so hoping that someone here can point me in a direction to try to find a solution.   My linux experience is pretty minimal, so I appreciate any specifics that can be tossed out.

I'm running Mythbuntu 12.04, fresh install.   Every time I boot or reboot the computer, the whole desktop is tinted purple - especially the areas that should be black.   This continues on top of any and all applications that I run.  If I disconnect the HDMI cable, or even switch HDMI inputs on the TV to something else and back to the PC, the purple vanishes, and all looks normal.   Viewing in a VNC session shows blacks where they should be, and no purple tint.

This does NOT manifest ever when booting a live-stick of Ubuntu 12.04 or Mythbuntu 12.04.   It never manifests if I boot into windows.  It's only when booting to the new installation of Mythbuntu on the local hdd.   This has happened since first installed, and has never changed as I have run updates/changed nvidia drivers, etc.

This leads me to think it's an HDCP handshake thing that's going slightly wrong, but I have no idea where to start digging.

Any help would be appreciated, this is the last stumbling block to having my MythTV box running as desired.

Thanks!

Setup (yea, it's old, it does the job)
Asus P5LD2-VM board
2.13ghz c2d
2gb ram
GeForce 9600 GSO

---

### Post by kingmoocow on 2013-02-10
Bump.

---

### Post by Sef on 2013-02-10
Moved to Mythbuntu subforum.

---

### Post by PhilWig on 2013-02-12
I risk sounding like the child with a hammer who sees the world as a nail because I've just replied to Steve666 who has another Nvidia issue:

"A silly question probably but when you fitted your Nvidia card, did you invoke the drivers?
On my 12.04 system I needed 
Mythtv control centre 
> launch restricted drivers manager 
> nvidia accelerated graphics driver (version current) [recommended]
"

Best wishes
Phil

---

### Post by BicyclerBoy on 2013-02-12
My work winXP & LG24" LCD (HDMI but not a TV panel) used to do something similar..wrong colour-space on booting..Had to fiddle with the monitor OSD after every reboot.
HDMI supports RGB & YUV colour-spaces.

You could try running "nvidia-settings" and see if changing the colour-space & studiolevels (colour range) causes the same colour shift..

You could post your /var/log/Xorg.0.log file **after** booting & fixing the colour shift..

---

### Post by kingmoocow on 2013-02-13
> **PhilWig said:**
> I risk sounding like the child with a hammer who sees the world as a nail because I've just replied to Steve666 who has another Nvidia issue:

"A silly question probably but when you fitted your Nvidia card, did you invoke the drivers?
On my 12.04 system I needed 
Mythtv control centre 
> launch restricted drivers manager 
> nvidia accelerated graphics driver (version current) [recommended]
"

Best wishes
Phil

Not silly, but it's the first thing I checked.  I tried all of the variants there listed as well, initially thinking it was a driver issue, since I didn't have the issue in vanilla ubuntu's live-stick, it seemed that drivers made sense.

Since I originally posted this, I actually have reformatted and reinstalled mythbunty 12.04 for self-inflicted issues, and the issue still persists, though it should be on the OOtB nvidia driver now.

> **BicyclerBoy said:**
> My work winXP & LG24" LCD (HDMI but not a TV panel) used to do something similar..wrong colour-space on booting..Had to fiddle with the monitor OSD after every reboot.
HDMI supports RGB & YUV colour-spaces.

You could try running "nvidia-settings" and see if changing the colour-space & studiolevels (colour range) causes the same colour shift..

You could post your /var/log/Xorg.0.log file **after** booting & fixing the colour shift..

I changed the colorspace from RGB to the other one and rebooted, it still came up purple.   Disconnected and reconnected the HDMI, looks normal now.  Log here:
[http://pastebin.com/R89QeBmy](http://pastebin.com/R89QeBmy)

---

### Post by BicyclerBoy on 2013-02-14
Nothing in the Xorg.0.log to suggest any hot-plug event occurred..
Is there any clues in "dmesg" output after the hot-plug fix?

---

### Post by kingmoocow on 2013-02-14
> **BicyclerBoy said:**
> Nothing in the Xorg.0.log to suggest any hot-plug event occurred..
Is there any clues in "dmesg" output after the hot-plug fix?

I looked at dmesg before and after plugging and unplugging the cable and I didn't notice anything new in there.   

Could there be any difference because I'm using a DVI to HDMI adapter that would cause it not to notice that i've been connecting or disconnecting the video?

---

### Post by BicyclerBoy on 2013-02-15
Re-plugging the video cable should cause hot-plug events..especially HDMI.
There should be events in dmesg (about ELD HDA stuff) & Xorg.0.log.

The common DVI-HDMI adapter is a passive single link cable.
Like I said before, the windows driver had problems with incorrect colour-space some time back.
But we do not know if colour-space is the problem.

Note HDMI is == single link DVI & limited to 1920x1200@60.

---

