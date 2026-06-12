---
title: "new nvidia drivers locking firefox?"
date: 2011-08-29
forum: Multimedia Software
---

### Post by chet9119 on 2011-08-29
Hi all - 

I loaded the new NVIDIA driver today (280.xxx) and am having trouble using hulu.  getting complete lock-ups after commercial breaks, and when changing the "quality" option (480p, etc).  all mediabuntu items are installed (went there first).

anyone else having this issue?  I also installed flash-aid and upgraded to firefox 6, thinking I somehow manually installed the incorrect version of flash, or firefox was the issue.  no effect.

version:  lucid
hardware:  zotac ionitx (ion)

---

### Post by Dlambert on 2011-08-29
Im not having this problem. Wierd

---

### Post by lovinglinux on 2011-08-29
First, make sure you get [Flash-Aid 2.2.1]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/versions/"), because version 2.1.1 has a bug that only affects Firefox 6.

I was experiencing low performance in Firefox when scrolling some pages, while using with nVidia 280 on Ubuntu 11.04. Problem is gone since I installed version 173 of the nvidia driver.

---

### Post by beew on 2011-08-29
I have the Nvidia 280.XX on Maverick. I have experienced no problem with FireFox but Opera freezes on Youtube by going from fullscreen to normal size. I think that may also have something to do with Flash and Opera (and Nvidia) as the beta version of Flash from  Adobe lab doesn't have that problem, it only happens with the stable version from the repository. However the beta version doesn't use vdpau while the stable version does, so for the moment I only use FireFox for flash videos. I installed all my flash versions with Lovinglinux's Flash-aid addon.

In 11.04 I have Nvidia 285.03 (beta driver installed via the xorg-edgers ppa) It is working fine though still have same problem that beta version of flash doesn't use vdpau and the stable version crashes Opera on exit (though not as acute as in 10.10 with Nvidia 280.XX, going from full screen to normal size is fine)

On another 11.04 install I use nouveau and the latest open source graphic drivers (from xorg-edgers) and there is no problem.

So it seems that there are problems with  the mix Opera + flash+ Nvida. However Firefox appears to be working well in all configurations (I am using FF6)

---

### Post by lovinglinux on 2011-08-29
> **beew said:**
> I have the Nvidia 280.XX on Maverick. I have experienced no problem with FireFox but Opera freezes on Youtube by going from fullscreen to normal size. I think that may also have something to do with Flash and Opera (and Nvidia) as the beta version of Flash from  Adobe lab doesn't have that problem, it only happens with the stable version from the repository. However the beta version doesn't use vdpau while the stable version does, so for the moment I only use FireFox for flash videos. I installed all my flash versions with Lovinglinux's Flash-aid addon.

In 11.04 I have Nvidia 285.03 (beta driver installed via the xorg-edgers ppa) It is working fine though still have same problem that beta version of flash doesn't use vdpau and the stable version crashes Opera on exit (though not as acute as in 10.10 with Nvidia 280.XX, going from full screen to normal size is fine)

On another 11.04 install I use nouveau and the latest open source graphic drivers (from xorg-edgers) and there is no problem.

So it seems that there are problems with  the mix Opera + flash+ Nvida. However Firefox appears to be working well in all configurations (I am using FF6)

Noveau worked great for me too, however card temperature went from 65 C to 90 C.

I must note that I am using Flash 11 Beta and have no problems whatsoever. My performance problems affected video on smplayer while scrolling some particularly slow pages in Firefox.

---

### Post by beew on 2011-08-29
> **lovinglinux said:**
> Noveau worked great for me too, however card temperature went from 65 C to 90 C.

I must note that I am using Flash 11 Beta and have no problems whatsoever. My performance problems affected video on smplayer while scrolling some particularly slow pages in Firefox.

Yeah, noveau is not very efficient and it is a given that it doesn't use hardware acceleration, I am just trying to figure out if Nvidia has a part in causing the problem.

The beta version of Flash doesn't crash Opera but it doesn't use vdpau either so for the same Youtube clip the beta version of flash would use 60-70% of cpu while the stable version of flash would use only ~10% ( in Maverick with Nvidia 280.XX) to ~5% (in Natty with Nvidia285.03)

P.S.   I think the newer version of Nvidia may not be responsible for the improvement in cpu usage of Natty over Maverick. Natty seems to actually uses less resources on videos than Maverick even before I updated the Nvidia driver, --this is contrary to claims by some people that Natty uses more resources)

**EDITED: **I should note that I did all the tests on the same machine, though the two Natties are installed in an external harddrive.

---

### Post by chet9119 on 2011-08-29
thanks for the comments.  to revert to the old driver is it as simple as choosing a prior version from the ppa?  (in trying to fix this I purged all the nvidia drivers and reinstalled the current).  I blacklisted nouveu at some point because it was causing problems in mythtv.

I never really used flash on this machine due to the sound issues with firefox.  with the verizon strike, I figured I would try it out.  so it appears I fixed the sound and broke the flash video  (although myth playback still looks great with the new nvidia drivers using vdpau).  

I didn't realize that the beta version of flash didn't use hardware acceleration, good info.

---

### Post by chet9119 on 2011-08-29
Think I figured it out.  Turns out that by installing the 173 driver I lost sound.  When I reactivated the nvidia-current (in the hardware window) and installed the right version of flash-aid, things seems to operate normally.  also made some tweaks to the nvidia-settings, like turning on v-sync and turning on "prefer maximum performance."  (the latter doesn't seem to stick after reboots).

thanks for the tips all.  flash-aid is highly recommended, as I was struggling trying to install manually.  But, I don't think I will be updating drivers any time soon after all this.

---

### Post by lovinglinux on 2011-08-30
> **chet9119 said:**
> Think I figured it out.  Turns out that by installing the 173 driver I lost sound.  When I reactivated the nvidia-current (in the hardware window) and installed the right version of flash-aid, things seems to operate normally.  also made some tweaks to the nvidia-settings, like turning on v-sync and turning on "prefer maximum performance."  (the latter doesn't seem to stick after reboots).

thanks for the tips all.  flash-aid is highly recommended, as I was struggling trying to install manually.  But, I don't think I will be updating drivers any time soon after all this.

Great news. 

Thanks for the comments about Flash-Aid.

---

