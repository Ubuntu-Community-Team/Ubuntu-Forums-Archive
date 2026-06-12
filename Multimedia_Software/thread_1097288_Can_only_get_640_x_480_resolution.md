---
title: "Can only get 640 x 480 resolution"
date: 2009-03-15
forum: Multimedia Software
---

### Post by Alhazred on 2009-03-15
Hi guys. I've read a couple of other posts on this problem, but they do not seem relevant to my situation. It's like I am stuck in safe graphics mode.

I have an older Dell Optiplex GX260 desktop, with an Intel 8245G video card. The display was a bit flaky under Hardy, but mostly OK. However, since installing Intrepid I can't get out of 640 X 480.

When I run lspci, the graphics card shows as:
VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)

However, when doing System > Preferences > Screen Display, only 640 x 480 is an option. Clicking on the Detect Displays button does nothing.

When I run sudo dpkg-reconfigure xserver-xorg, the wizard asks me about my keyboard, but I am never asked to configure the display. The devices portion of my xorg.conf file looks like this:
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

Mick

---

### Post by Alhazred on 2009-03-16
OK, this one is solved. Well, I _think_ I know what I did to solve it. I added this simple section to xorg.conf:

Section "Device"
	Identifier	"Configured Video Device"
        Driver          "intel"
EndSection

I then rebooted. (Actually before rebooting I shut down the desktop via sudo /etc/init.d/gdm stop, but I'm not sure if that had any helpful effect.)

When it came back up, the display was a thing of beauty.

What is weird is that I had previously edited xorg.conf with similar lines, but it always reverted back to the text that I mentioned above.

Mick

---

