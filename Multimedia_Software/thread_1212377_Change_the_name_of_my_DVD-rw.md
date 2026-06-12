---
title: "Change the name of my DVD-rw"
date: 2009-07-13
forum: Multimedia Software
---

### Post by thijsvanhulten on 2009-07-13
When building my current system I thought it would be nice to have 2 DVD-RW drives, should make copying DVD's a bit quicker.
However I bought 2 identical drives. So now whenever I want to copy a DVD, let's say in GnomeBaker, I get a drop down box for both 'Reader' and 'Writer' that contain 2 identical entries, being 'LITE-ON DVDRW LH-20A1S'. And of course I always pick the wrong one for reader and or writer, very frustrating.
So I'd like to rename the devices in so that the name gives away the physical position of the drive, something like 'top_drive' and 'bottom_drive'.
Or maybe just a firmware hack that changes the drives designation. Anything to make them distinguishable.

---

### Post by thijsvanhulten on 2009-07-20
BUMP, anyone.....

---

### Post by thijsvanhulten on 2009-07-24
Solved my problem:

Because flashing DVD-drives under Linux is not properly supported I used my windows-xp installation to perform the following actions. 

- First I downloaded the latest stock firmware form the lite-on site. Since the firmware comes embedded in a flash application I decided it was easiest to first install the firmware in the drive and then extract it from the drive. Note that the installer only works if the drive contains stock firmware.

- Used the 'Flash_Utility-3.0.3' (downloaded from codeguys.rpc1.org) to save the firmware from the drive.

- Used HxD (hex editor) to edit the extracted firmware. The device-name ('LITE-ON DVDRW LH-20A1S') appears several times in the firmware. Some device-name entries are accompanied by a byte-swapped variant and these are the significant entries. In my case the second device-name pair did the trick. When editing the firmware make sure an device-name pair (normal and swapped name) are kept matching.

Before the change the 2nd device-name pair of both drives looked like this:
normal='LITE-ON DVDRW LH-20A1S', swapped='ILETO- NVDRD WHL2-A0S1'

After the change the 2nd device-name pair for my 1st drive looks like this:
normal='TOP     DVDRW LH-20A1S', swapped='OT P    VDRD WHL2-A0S1'

After the change the 2nd device-name pair for my 2nd drive looks like this:
normal='BOTTOM  DVDRW LH-20A1S', swapped='OBTTMO  VDRD WHL2-A0S1'

- Used the 'Flash_Utility-3.0.3' to load the modified firmware into the drives.

- After restarting Linux I tried GnomeBaker and still found the old device-names:confused:, but after I rescanned the devices (Preferences -> Devices -> Scan for Devices) the new device-names appeared:D.

So now I have 2 drives roughly called TOP and BOTTOM.

---

### Post by hansdown on 2009-07-24
Glad you fixed it thijsvanhulten. And I'd just like to add, that's pretty clever.

---

