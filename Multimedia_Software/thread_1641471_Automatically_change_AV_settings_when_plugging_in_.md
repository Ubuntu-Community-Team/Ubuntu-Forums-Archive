---
title: "Automatically change AV settings when plugging in external display"
date: 2010-12-09
forum: Multimedia Software
---

### Post by Cheesemaster64 on 2010-12-09
I am sorry if this has been posted somewhere else, but I searched the forums for a long time and could not found any relevant information.

I am new to ubuntu (10.10 64bit) and I just want to know if it is possible, like it is in win7 (sorry!), if I can plug in my hdmi cord and have the laptop speakers and display disable, and have the external display and its spears enabled.

---

### Post by Cheesemaster64 on 2010-12-11
> **Support teams dedicated to Windows users.**  Linux has a  very large support community, and specifically places like  [www.ubuntuforums.org](www.ubuntuforums.org) have teams dedicated to helping new users.   Recognizing that the majority of new Linux users come from Windows due  to Windows’ market share, and creating teams specifically geared toward  Windows’ users unique needs, should help their adjustment to Linux.

'nuff said.

---

### Post by efflandt on 2010-12-13
It would be tough for anyone to be real specific without knowing what hardware you have.

For example with ATI or Intel it is usually best to simply boot with the external display already connected.  The laptop usually defaults to the external display, but when X starts it may try to find a compromise resolution that it thinks will work on both displays mirrored (which may not be optimum for either one).  But not sure how that works for HDMI since my laptops only have VGA.  So I use a script run from launcher on panel or desktop with xrandr commands to turn off my laptop display, set proper resolution for external, and switch to external display.

Nvidia seems to default to the normal (laptop) display, so you have to use Nvidia X Server Settings to switch to external, and remember to change it back afterwards.  That could probably be scripted, but the only (old) laptop I have with nvidia has a broken display, so it is set to use external in nvidia settings.

If you connect a monitor/TV after X is running System > Preferences > Monitors may have a button to recognize it.  But otherwise if you log out of X and back in, the system should at least know it is there.

Configuring HDMI audio also depends what hardware you have.

The way to automate connection of hardware is scripts in /lib/udev/rules.d, but other than modifying some settings in scripts there, I have not written such scripts for automating video or audio hardware.  Although, I should figure out how to do that some day for wireless headset.

Post the "part" of the output of **sudo lspci -v** related to your video and audio devices, and someone may offer more help. Wrap that text in code tags to preserve its formatting by highlighting it and clicking **#** in top of message window.

---

