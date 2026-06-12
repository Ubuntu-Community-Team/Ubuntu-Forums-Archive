---
title: "Can't upgrade from Lucid to Maverick (Nvidia X-problem?)"
date: 2010-08-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by andersja on 2010-08-30
Hi all, 

I am hoping the resolution to my problem will be found here: After upgrading from 10.04 to 10.04.1 my PC doesn't boot anymore (fsck gives an error on the old kernel, new kernel just hangs completely). This behabiour is documented in  [Bug# 573356]("https://bugs.launchpad.net/ubuntu/+bug/573356")I am (boldly/foolishly?) hoping that upgrading to Maverick will fix this (as well as allowing me to participate in the testing...)

When I run **gksudo update-manager -d**, all seems to be working well, until, just after the third party sources warning, I am presented with a prompt saying **Could not determine the upgrade** and some text about an unresolvable problem while calculating the upgrade: 

E: Error pkgProblemResolver::Resolve generated breaks, this may be caused by held packages

It goes on to say this may be caused by trying to upgrade to a pre-release version of Ubuntu (which is indeed true), and tells me to report it as a bug if not.

Does anyone have an idea of how I could resolve this? From the logs, it looks like it could be related to the nouveau / nVidia video drivers?

```
$ tail -30 apt.log 
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 85 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 18
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 85 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 18
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 85 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Investigating libdrm-nouveau1
Package libdrm-nouveau1 has broken Breaks on xserver-xorg-video-nouveau
  Considering xserver-xorg-video-nouveau 2 as a solution to libdrm-nouveau1 18
  Upgrading xserver-xorg-video-nouveau due to Breaks field in libdrm-nouveau1
Investigating xserver-xorg-video-nouveau
Package xserver-xorg-video-nouveau has broken Depends on xorg-video-abi-8.0
  Considering xserver-xorg-core 85 as a solution to xserver-xorg-video-nouveau 2
  Holding Back xserver-xorg-video-nouveau rather than change xorg-video-abi-8.0
Done

```

main.log shows:
```
2010-08-30 11:33:57,114 DEBUG running doUpdate() (showErrors=True)
2010-08-30 11:34:13,774 DEBUG openCache()
2010-08-30 11:34:13,774 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-08-30 11:34:17,370 DEBUG /openCache(), new cache size 32926
2010-08-30 11:34:17,371 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2010-08-30 11:34:28,283 ERROR Dist-upgrade failed: 'E:Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.'
2010-08-30 11:34:28,283 DEBUG abort called
2010-08-30 11:34:28,286 DEBUG openCache()
2010-08-30 11:34:28,286 DEBUG failed to SystemUnLock() (E:Not locked) 
2010-08-30 11:34:31,391 DEBUG /openCache(), new cache size 30925
2010-08-30 11:34:31,391 DEBUG enabling apt cron job

```

---

### Post by dino99 on 2010-08-30
update your synaptic repo tab with "maverick", and deactivate third party repo if any, then update

---

### Post by andersja on 2010-08-30
Thanks for this - sounds like it will work but it's a bit 'hacky' - I remember others' installations breaking when doing similar shortcuts in the past. Is the current update-manager in lucid broken? 

Thanks for your help!

---

### Post by andersja on 2010-09-01
Actually- anyone experiencing similar problems should note this is actually a bug that's being worked on and following the "hack" mentioned above would not resolve it:

[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/614993")

---

### Post by evilkastel on 2010-09-01
I actually had this same bug, and since i was in a hurry, had to do a clean install of alpha3. Glad to see it's reported, tough.

---

