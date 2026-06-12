---
title: "Will not boot to gnome after loading Nvidia drivers"
date: 2008-12-23
forum: Multimedia Software
---

### Post by mushii on 2008-12-23
So, I searched the forums and could not find anyone having the same problem I did.  Forgive me if I missed that particular post, I am very, very new to linux, and am unsure of some of the terminology.

My problem.  I loaded Ubuntu 8.10 onto my new computer, installed a few minor programs, as well as EvE Online, when I went to run EvE it told my my graphics card (GeForce 8600GT) was failing the 3D acceleration test.  I installed the new proprietary drivers via the built in hardware manager, restarted the computer, and the computer will not boot back into gnome.

What I get is as follows:
It starts go load GRUB.
Goes to the Ubuntu loading bar.
Pops up a black screen with the following text.

Loading, please wait...
usplash: Setting mode 1152x864 failed
usplash: using mode 1024x768
19+0 records in
19+0 records out
kinit: name_to_dev_t(/dev/disk/by-uuid/a2ad4324-24b9-4af0-8297-863113046e5a)=dev(8,5)
kinit: trying to resume from /dev/disk/by-uuid/a2ad4324-24b9-4af0-8297-863113046e5a
kinit: No resume image, doing normal boot...

After which it boots to a terminal prompt asking me for my login, etc.

I have tried a variety of random fixes I have found to no avail.  I ran the "sudo dpkg-reconfigure gdm" (not sure if that is exactly right, I am typing it from memory, suffice to say, I had it written down in front of me when I tried it), as well as the reconfigure of the xserver.xorg.

I have already reinstalled the OS 5 times and I would really like to get this video card running.

Any suggestions?

---

### Post by mushii on 2008-12-25
Small bump for help.

---

