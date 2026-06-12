---
title: "No picture when AV amp is off at PC startup"
date: 2010-02-17
forum: Mythbuntu
---

### Post by myth01 on 2010-02-17
Bear with me, this isn't as stupid as it sounds!

I have my mythbox connected by HDMI to my AV amp which is then connected to the TV (by HDMI again).

If the AV amp is off or on a different input when the mythbox is started (for a scheduled recording for example), no picture is displayed if you later switch to the myth input.  I can use gnome-do to log out and then the screen comes up with the log-in screen.

If however, the AV amp is on and on the correct input when the PC is started, the screen gets displayed as it should do.

I would like the screen to be working regardless of the state of the amp at startup.

Is this an EDID issue?  Or something else?  As usual, I shall expect it to be something simple I have overlooked...

---

### Post by turtle02 on 2010-02-18
I have the same problem and still have not found a fix for it.

---

### Post by myth01 on 2010-02-18
At least I'm not alone then.  There must be a fix... surely?!

---

### Post by Neon Dusk on 2010-02-18
Same problem here. Been meaning to look at it for while but have a button mapped on the remote to restart the X server which fixes it.

Anyway decided to investigate further and got a solution for my hardware (FE with HDMI (audio & video) connected directed to TV, different frontend with HDMI (audio & video) to amp  then to TV)

I've got my /etc/xorg.conf set-up similar to the one by jyavenard [here](http://avenard.com/media/Patches_%26_Add-Ons/Entries/2008/9/5_xorg.conf_and_specific_refresh_rates.html)

To get this to work when the amp/tv is turned on after the PC is started it's just a case of adding Option "ConnectedMonitor" "DFP-0" to the screen section of xorg.conf. See thread by SiHa [thread=913224]here[/thread]. (the ConnectedMonitor option may by DFP or DFP-0 if you open nvidia-settings it should tell you)

This worked but there was no sound through HDMI. To fix the sound you need to dump the EDID info (I put it in /etc/X11/edid.bin) using the nvidia-settings and then add the following to your xorg.conf screen section
```

Option         "CustomEDID" "DFP-0:/etc/X11/edid.bin"

```

---

### Post by myth01 on 2010-02-18
Cheers again Neon Dusk.

It worked like a charm.  Although I had to add both lines to my xorg.conf.  I only tried the ConnectedMonitor one first as I'm not using sound over HDMI yet (until I can figure out which pin is which on the motherboard SPDIF to connect it to my graphics card).  The screen came on but at a horrible resolution.  I then added the CustomEDID (which common sense suggests I should have done anyway) line.  

The two new lines in the Screen section of my xorg.conf:

```
Option    "ConnectMonitor" "DFP-1"
Option    "CustomEDID" "DFP-1:/etc/X11/edid.bin"
```

Good effort finding that, I had googled but it didn't produce anything I found useful.

---

