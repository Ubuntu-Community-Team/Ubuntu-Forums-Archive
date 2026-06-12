---
title: "no audio via HDMI connection"
date: 2020-04-24
forum: Multimedia Software
---

### Post by inappropriate on 2020-04-24
Hello. I'm running lubuntu 18 via an intel compute stick (althought I tried this on Ubuntu 18 via HDMI and the same issue persists). I have no audio from the HDMI. Video of course works fine. When I run pavucontrol via the command line and check output and configuration tabs there is no option for HDMI. When I run VLC there is no option for anything HDMI related. I tried pulseaudio -k and then ran pavucontrol as some suggested but to no avail. I'm wondering why I can't send audio from the OS through the HDMI in the TV.

Under volume control, in the Output Devices tab, there is only analog output under the port. In the Configuration tab, there is Stereo Output, Multichannel Output and Off for profiles.

---

### Post by Autodave on 2020-04-25
Forgetting about the OS, are you sure that your cable is good?  Some of the very early HDMI cables did not have the ability to transmit audio.

---

### Post by Yellow Pasque on 2020-04-25
[https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

> Forgetting about the OS, are you sure that your cable is good?

You've got it backwards. You need to have an HDMI audio device in the OS before you can worry about the cable. If you had an HDMI audio device that appeared to play sound (or claimed it was unplugged), then you might worry about the cable.

---

### Post by CelticWarrior on 2020-04-25
> **Yellow Pasque said:**
> [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)



You've got it backwards. You need to have an HDMI audio device in the OS before you can worry about the cable. If you had an HDMI audio device that appeared to play sound (or claimed it was unplugged), then you might worry about the cable.

Agreed. And I never noticed such problems with HDMI and I'm using it since it became a *de facto* standard if not before.

The problem here is likely related with the Intel hardware. There are different [Intel Compute Sticks]("https://www.intel.com/content/www/us/en/products/boards-kits/compute-stick.html"), the expensive ones should be great but the cheap ones are likely crap. Crap that works acceptably only with Windows, to be clear. The "Cherry Trail" based devices will have the same issues all other similar computers have, WiFi (now sort of supported, I guess) and... Audio. That's all.

---

### Post by ubfan1 on 2021-03-29
Even the small 1GB ram/8GB storage Intel Compute Sticks came with working HDMI audio (original kernel 3.13, 3.16).  Upgrading to the 4.4 kernel killed the audio because the Intel (Canonical Engineering in the comments) driver would not compile -- an error in the kernel headers Canonical supplied.  Looks like Canonical grabbed a release candidate, and did not notice the final version of i915_component.h was changed. An edit of the header allowed the 4.4 kernel compliation to succeed, and HDMI audio to work. (Until kernel 142 when an api change hit, and I never bothered to see if the driver was updateable)  Later kernels used after 16.04 should not have this problem since the Canonical driver is no longer needed.  Bluetooth was the last problem area of the ICS until kernel 4.19, when everything worked.    (Although Bluetooth seems to not work in several 5.x kernels). Check what driver you are using, maybe the old Canonical one is hanging around causing problems.

---

### Post by CelticWarrior on 2021-03-29
> **ubfan1 said:**
> Even the small 1GB ram/8GB storage Intel Compute Sticks came with working HDMI audio (original kernel 3.13, 3.16).  Upgrading to the 4.4 kernel killed the audio because the Intel (Canonical Engineering in the comments) driver would not compile -- an error in the kernel headers Canonical supplied.  Looks like Canonical grabbed a release candidate, and did not notice the final version of i915_component.h was changed. An edit of the header allowed the 4.4 kernel compliation to succeed, and HDMI audio to work. (Until kernel 142 when an api change hit, and I never bothered to see if the driver was updateable)  Later kernels used after 16.04 should not have this problem since the Canonical driver is no longer needed.  Bluetooth was the last problem area of the ICS until kernel 4.19, when everything worked.    (Although Bluetooth seems to not work in several 5.x kernels). Check what driver you are using, maybe the old Canonical one is hanging around causing problems.

Really nice to know all this inside info.
Unfortunately the OP hasn't logged on the forum since posting this laconic thread.

---

