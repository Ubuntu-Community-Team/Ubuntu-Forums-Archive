---
title: "Why do Broadcom wireless drivers affect my screen resolution"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by slumbergod on 2009-12-17
A couple of hours ago I wrote a solved post regarding getting Broadcom wireless drivers working on an HP 2133 netbook, given that Karmic doesn't load them and I there is no wired connection. All good and done; the wireless drivers do work.

But, there is a weird catch that I can't figure out...

Loading either the official Broadcom drivers or the Ubuntu Karmic ones at boot time causes the screen display to get stuffed up. The resolution is normally something like 1368x768 and looks great when you don't load the drivers with the boot. If you do, the resolution doesn't change but the LCD screen seems unable to fit everything in so you get maybe a quarter. 

Remove the wireless drivers, and reboot, and the screen fits everything. If I manually load the wl.ko after boot is finished I can then get wireless.

What I can't understand is how wireless and screen resolution are related. No one else seems to have this issue so I know it is an HP netbook (and crappy Via chrome video drivers) issue.

Any suggestions? There isn't even an xorg.conf file to look at. I tried configuring one from recovery but that didn't work at all.

---

### Post by slumbergod on 2009-12-17
I have discovered that by adding modeset=0 as a kernel parameter, Karmic will boot with both wireless and the correct display resolution (i.e. the correct desktop resolution scaled to fit on the smaller netbook dispay).

That is an advancement because it allows me to use the default Ubuntu Karmic drivers for the Broadcom wireless chipset.

I still have an issue though when I log out of one account and into another - suddenly the display scales itself so that the full desktop no longer fits.

Someone must have an idea why this is happening. I am convinced it is to do with the new way Karmic uses the latest modesetting with xorg which is fine for Intel but this netbook uses Via's Chrome chipset.

Suggestions? 

If I can't get this working I will just give up on Karmic. It was hell getting my main laptop configured (wireless is still unstable and that is with Intel wireless!). I understand now why so many people got angry with Karmic. Most definitely not ready for the mainstream!

---

### Post by slumbergod on 2009-12-18
The fix is to create an xorg.conf to override the incorrectly "guessed" settings:

sudo nano /etc/X11/xorg.conf

adding just the following:

  Section "Device"
      Identifier "Configured Video Device"
      Option "PanelSize" "1024x600"
  EndSection

---

