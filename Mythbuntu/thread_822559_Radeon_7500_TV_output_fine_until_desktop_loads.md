---
title: "Radeon 7500 TV output fine until desktop loads"
date: 2008-06-08
forum: Mythbuntu
---

### Post by ChrisMoose on 2008-06-08
I'm not sure how to even search for help with this issue, so if it's something obvious, I apologize. I'm also a Linux newb.

I'm running 8.04 on an old Athlon 1.3G box with a Radeon 7500 AGP video card. I hooked the S-video up to my ancient SD TV and started up the boot output info displayed fine, followed by the Mythbuntu splash screen with the "loading" bar. The first time I hooked it up, there was a "testing drivers" message and progress bar, which seemed to complete OK. This hasn't happened on subsequent restarts.)

Right after that, though, when the desktop came up, the TV went blank. I turned the machine off, hooked up a monitor to the VGA out on the card, and restarted. The boot info displayed to both the TV and the monitor; when the splash screen came up, the monitor went blank, and the TV displayed fine; and when the desktop came up, the TV went blank, and the monitor started displaying again.

MythTV continues to come up fine, albeit only on the monitor (GUI and playback).

Anyone have any ideas? Is this an issue with enabling TV-out on the video card? 

Thanks in advance!

---

### Post by rob3435 on 2008-06-08
Not sure if your running ati's binary release or the open source radeon driver in Hardy. But this is the xorg.conf setup I use for my mythbox running the big screen tv, using the opensource "radeon' driver.  At a minimal you'll just need the "ForceTVOut" and "TVStandard" options set

```
Section "Device"
        Identifier      "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Driver          "radeon"
        Option "ForceTVOut" "true"
        Option "TVStandard" "ntsc"
EndSection

Section "Monitor"
        Identifier      "S-Video"
EndSection


Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc RV350 AR [Radeon 9600]"
        Monitor         "S-Video"
EndSection

```

---

### Post by ChrisMoose on 2008-07-01
Sorry for the delayed response, rob3435. 

Your response helped me resolve the issue. After a couple of reinstalls, it turns out all I needed were the 

	Option "ForceTVOut" "true"
	Option "TVStandard" "ntsc"

options in my xorg.conf. (FWIW, I'm using the delivered open source ATI drivers.)

One thing I found was that if I had both a monitor (VGA) and TV (s-video) hooked up at startup, I got dual output, but at the monitor's resolution (which does _not_ look good on the telly). To fix that, I just detached the monitor and restarted.

Thanks again for the assist!

---

