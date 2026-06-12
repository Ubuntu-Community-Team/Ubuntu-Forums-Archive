---
title: "Crossfire and Dualhead with an ATI card"
date: 2009-07-12
forum: Multimedia Software
---

### Post by mambazo on 2009-07-12
Hi, I recently bought a new system, including ..

(1) an ATI Radeon HD4850x2.
(2) two identical monitors capable of 1920x1080x60.

I'd like to achieve two things in ubuntu that I have in windows:

(1) Run the card with dualhead and NO crossfire. This means I get support for connecting 4 monitors, which I'd put in a rectangular pattern.

(2) Run the card with dualhead AND crossfire. This means I get support for connecting 2 monitors, which I'd put side-by-side.

In windows I can easily switch between the above two by enabling/disabling crossfire in the CCC panel.

Could someone please help? A x.org file dump is fine, a sequence of aticonfig commands is fine, anything! I just want to be able to achieve the above two and, if possible, a quick way to switch between them.

Regards,
Loban

---

### Post by mambazo on 2009-07-13
Anybody? Here's what I've tried so far:

(1) I used "aticonfig -f --initial=dual-head --adapter=all". This seems to have worked since the xorg file contains 4 monitor sections. However, when I login, both monitors work, but both of them contain gnome-panels! And I cannot start or move any application window into the second desktop!!

(2) I used "aticonfig -f --initial=dual-head --crossfire=on --crossfire-add-chain --adapter=all". This produced an xorg file that looks correct, but doesn't have any mention of crossfire in it. Anyway, X crashes on startup.

So I'm still stumped.:confused:

---

### Post by mambazo on 2009-07-14
Nobody?

---

### Post by markbuntu on 2009-07-14
If you want to use the Catalyst Control Center to control your screens you need to first disable randr. There are two ways to do this. You can edit the file

/etc/ati/smdpcsdb

scroll down to the EnableRandR line and make it look like this

EnableRandR12=SFalse

Or you can add it as an option in xorg.conf in the Device Section after the Driver "fglrx" line. Option "EnableRandR12" "false"

Once you do that and reboot you should be able to use the Catalyst Control Center to configure your monitors and the xinerama option should now be available. Or you can use aticonfig.  I am pretty sure you will not be able to stretch one desktop across 4 monitors yet but you should be able to get two big desktops and xinerama should work so you can move windows across any monitors.

This will probably not work unless you are using the latest driver, 9.6.

The driver can get confused if you try to change more than one thing at a time so be very careful about that. If you update the driver you may have to disable randr again before you can use xinerama.


good luck.

---

### Post by mambazo on 2009-07-15
Thanks for the pointers, markbuntu. Will try it out tonight and post my results.

---

