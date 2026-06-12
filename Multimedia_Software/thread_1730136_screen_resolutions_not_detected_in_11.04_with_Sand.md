---
title: "screen resolutions not detected in 11.04 with Sandy Bridge"
date: 2011-04-15
forum: Multimedia Software
---

### Post by nLinked on 2011-04-15
My motherboard is an Intel Sandy Bridge one. I'm running a fully updated Ubuntu 11.04 beta 2.

My monitor is a Dell 27" connected via DVI. In Monitors, the monitor is detected but some of its capable resolutions aren't. The highest native resolution is displayed (1920 x 1200). This is too big for me, so I want 1440 x 900, but that isn't listed.

In Ubuntu 10.10 with the same monitor but different motherboard and NVIDIA graphics, 1440 x 900 and some others were automatically listed. Now I'm using the same monitor on a Sandy Bridge motherboard with Intel graphics, but those smaller native resolutions aren't there.

I am currently using this script at startup to force a res change:
```
#!/bin/sh
xrandr --newmode "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
xrandr --addmode HDMI1 1440x900_60.00
```

But this slows down startup. How can I add that res permanetly into the Monitors drop down menu? If I don't use the above as a startup script, the resolution disappears after a restart and a message says **could not apply the stored configuration for monitors**.

---

### Post by hutch120 on 2011-10-17
Found the answer.

Set them to run on startup in /etc/gdm/Init/Default just before "initctl ..."
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

For my Dell 2711 I ran these two lines:

xrandr --newmode "1920x1200_60.00" 193.25 1920 2056 2256 2592 1200 1203 1209 1245 -hsync +vsync
xrandr --addmode HDMI1 "1920x1200_60.00"
(Not sure why it thinks I'm connected to HDMI, when it is actually connected to Display Port via DVI converter, perhaps that's why it's confused about the resolution options)

BTW: This article talks about why the boot up might be slow after adding a startup script.
[https://help.ubuntu.com/community/UbuntuBootupHowto](https://help.ubuntu.com/community/UbuntuBootupHowto)
"Some people on the mailinglist complained on boot-delays because of the NTP-Server sync."

---

### Post by BicyclerBoy on 2011-10-18
@OP Why waste the resolution by doing this ?
Running an digital monitor at non-native resolution looks terrible & is very hard on the eyes.

Just scale up all the desktop widgets/typefaces/icons..

Only windows (pre win7) can't scale its desktop..

The modeline is not the optimal reduced vertical blanking timing for DVI/HDMI/DP 60Hz mode.
Could try cvt -r 1920 1200

HDMI is equivalent to single link DVI-D.
DP is quite a different beast..

---

### Post by nLinked on 2011-10-18
> **BicyclerBoy said:**
> @OP Why waste the resolution by doing this ?
Running an digital monitor at non-native resolution looks terrible & is very hard on the eyes.

Just scale up all the desktop widgets/typefaces/icons..

Only windows (pre win7) can't scale its desktop..

The modeline is not the optimal reduced vertical blanking timing for DVI/HDMI/DP 60Hz mode.
Could try cvt -r 1920 1200

HDMI is equivalent to single link DVI-D.
DP is quite a different beast..

Thanks. I just find running at a lower res is easier on my eyes otherwise text gets too small. It's just easier to lower the res than go through each prog to change font sizes.

I have just replaced my Dell 27" with an Acer 22" and all the Acer's resolutions automatically appeared. Both DVI. It seems as though the Dell doesn't send the resolutions through to the OS.

---

### Post by BicyclerBoy on 2011-10-18
Were you using a displayport adaptor cable like "hutch120" ?

Could have been the cause of EDID problem..
DVI-DP adaptor cable has different capabilities/limits to DVI or DP.

The Apple 27" DP screen is problematic for non-apple systems.

---

### Post by nLinked on 2011-10-18
> **BicyclerBoy said:**
> Were you using a displayport adaptor cable like "hutch120" ?

Could have been the cause of EDID problem..
DVI-DP adaptor cable has different capabilities/limits to DVI or DP.

The Apple 27" DP screen is problematic for non-apple systems.

No just normal DVI. In fact I'm using the same exact DVI cable on this Acer monitor because I couldn't be bothered re-cabling.

---

