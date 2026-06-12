---
title: "ubuntu 13.04 hp pavilion G series hdmi no sound"
date: 2013-10-01
forum: Multimedia Software
---

### Post by hunterkasy on 2013-10-01
I am having problems getting sound on my tv from my hp pavilion G series laptop, when I go to the sound setting their is no hdmi selection only speakers.  I am running 13.04 with full updates

---

### Post by hunterkasy on 2013-10-04
any help please

---

### Post by Bucky Ball on 2013-10-04
*Thread moved to **Multimedia & Video**.*

So you're attempting to get sound through a HDMI cable, presumably?

---

### Post by Yellow Pasque on 2013-10-05
If you have an ATI/AMD GPU and you're using the default/open-source radeon driver, see: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/864735)

Otherwise, please give more info: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

### Post by hunterkasy on 2013-10-05
i want to thank you for your help I did:

 === Workaround 1 ===

Edit /etc/default/grub and change this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

Now run "sudo update-grub", then reboot your computer.

now I see the hdmi in the sound setting but I have another problem.  when I hook up to the tv through the hdmi it wont work, the tv says something about the connected device wrong resolution or refresh rate  I have tried changing all of the resolutions but nothing but before I did have video

---

### Post by hunterkasy on 2013-10-05
[http://www.alsa-project.org/db/?f=15329129dd7a34c8984804641a8ebca4aead745e](http://www.alsa-project.org/db/?f=15329129dd7a34c8984804641a8ebca4aead745e)

---

### Post by hunterkasy on 2013-10-06
I got it working I did this:

=== Workaround 1 ===

Edit /etc/default/grub and change this line:

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to this line

GRUB_CMDLINE_LINUX_DEFAULT="quiet splash radeon.audio=1"

Now run "sudo update-grub", then reboot your computer.

then I installed AMD Catalyst Proprietary Display Driver - Linux x86 & Linux x86_64 now I have video and sound

---

