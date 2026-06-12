---
title: "hdmi out not working to external monitor"
date: 2013-06-25
forum: Multimedia Software
---

### Post by WaNaBePi on 2013-06-25
(ubuntu 12.04) my samsung rf510 hdmi signal sometimes won't show up on my external gateway LP2417 monitor, depending I believe, on kernel updates. Right now it's not working. I usually just use previous kernel until a new version works, but that doesn't really solve the problem.

If there is any way to make the hdmi work more steadily through updates that would be great.

I'm nearly certain it's not a hardware issue because all is well when I use the icky windows partition on the same laptop.

Let me know what commands and outputs need to be used and posted.

Thanks in advance.

---

### Post by WaNaBePi on 2013-06-28
Bump?

---

### Post by Mark Phelps on 2013-06-28
You're right, it's not a hardware issue -- it's an issue of the version of the video driver being incompatible with the version of the kernel.

If you're using open-source drivers, you should not be having this problem.

If you're using restricted drivers, and you installed them from a website -- you will continue to have this problem because you have to "remake" the drivers for every kernel update.

If you, instead, install the restricted drivers through Additional Drivers, that installs them differently, such that, when you update the kernel, the drivers get updated automatically.

I don't use Additional Drivers myself, so I don't have the commands handy.

---

### Post by WaNaBePi on 2013-06-29
Delete?

---

### Post by WaNaBePi on 2013-06-29
Thank you Mark,

If I recall correctly there are no open source drivers for the samsung rf510, it has a nvidia graphics card that's not supported. 

To anyone who has the commands handy, what commands would show the specs of my video card and drivers so that I can look for driver updates that will work for the kernel that is out now?

Or how do I remake the drivers that I have, so that they work with this kernel? That sounds complicated.

Thank you for the info.

---

### Post by SeijiSensei on 2013-06-29
Try "lspci | grep VGA".

---

### Post by WaNaBePi on 2014-06-10
"NVIDIA Corporation GT216M [GeForce GT 330M] (rev a2)" This is the out put from "lspci | grep VGA." I still have this problem with the latest updates. Monitor on laptop also appears to be in low res mode on newest kernel.

also in update manager i have had "NVIDIA binary xorg driver, kernel module and VADPAU library- nvidia-304 (size 68.3mb)" it has been unelectable for a while. I vaguely remember putting in a command to do something with the video updates so i would not have the graphics issues on new updates, but that fix does not seem to be working any more.

let me know if I should post any other info.

Thanks internet/ubuntu users.

---

### Post by WaNaBePi on 2014-06-17
Bump? I also have the "nvidia-graphics-drivers-304_304.117.orig.tar.gz" now.

I don't know how to correctly install it -can't find a good walk through for my level of knoledge- or if it will solve my problem in any way.

---

### Post by SeijiSensei on 2014-06-17
What happens if you run

```
sudo apt-get install nvidia-current
```

That should download the appropriate driver and the software required to compile the necessary hooks between the driver and kernel.

I've never had to do anything else on a machine with an NVIDIA card like the one I'm typing on now.

---

