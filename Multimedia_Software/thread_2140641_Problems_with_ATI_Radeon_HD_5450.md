---
title: "Problems with ATI Radeon HD 5450"
date: 2013-04-30
forum: Multimedia Software
---

### Post by Pizzicatto on 2013-04-30
Hi!
I've got an Ubuntu 12.04 running with the mesa radeon open source video drivers. I don't really now why but yesterday the videocard started failing and couldn't log in an unity session properly.

I've tried installing the fgrlx driver from the Ubuntu repositories, as well as manually following [this directions]("http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers-fglrx/126513#126513"), but no luck...

Finally I've gone back to the open source drivers removing everything I did (hopefully). I get this error in syslog when the graphics drivers try to load Unity:


```

Apr 30 15:11:42 ftae22 kernel: [   25.730570] radeon 0000:01:00.0: GPU lockup CP stall for more than 10096msec
Apr 30 15:11:42 ftae22 kernel: [   25.730576] GPU lockup (waiting for 0x00000003 last fence id 0x00000001)
Apr 30 15:11:42 ftae22 kernel: [   25.731631] radeon 0000:01:00.0: GPU softreset 
Apr 30 15:11:42 ftae22 kernel: [   25.731632] radeon 0000:01:00.0:   GRBM_STATUS=0xF4001828
Apr 30 15:11:42 ftae22 kernel: [   25.731634] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0xC0000003
Apr 30 15:11:42 ftae22 kernel: [   25.731635] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0x00000007
Apr 30 15:11:42 ftae22 kernel: [   25.731637] radeon 0000:01:00.0:   SRBM_STATUS=0x200000C0
Apr 30 15:11:42 ftae22 kernel: [   25.739330] radeon 0000:01:00.0:   GRBM_SOFT_RESET=0x00007F6B
Apr 30 15:11:42 ftae22 kernel: [   25.739431] radeon 0000:01:00.0:   GRBM_STATUS=0x00003828
Apr 30 15:11:42 ftae22 kernel: [   25.739433] radeon 0000:01:00.0:   GRBM_STATUS_SE0=0x00000007
Apr 30 15:11:42 ftae22 kernel: [   25.739434] radeon 0000:01:00.0:   GRBM_STATUS_SE1=0x00000007
Apr 30 15:11:42 ftae22 kernel: [   25.739436] radeon 0000:01:00.0:   SRBM_STATUS=0x200000C0
Apr 30 15:11:42 ftae22 kernel: [   25.756873] radeon 0000:01:00.0: GPU reset succeed
Apr 30 15:11:42 ftae22 kernel: [   25.776523] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
Apr 30 15:11:42 ftae22 kernel: [   25.776597] radeon 0000:01:00.0: WB enabled
Apr 30 15:11:42 ftae22 kernel: [   25.792635] [drm] ring test succeeded in 1 usecs
Apr 30 15:11:42 ftae22 kernel: [   25.792639] [drm] ib test succeeded in 1 usecs
Apr 30 15:11:42 ftae22 kernel: [   26.374169] eth0: no IPv6 routers present

```

When unity tries to show the log window it just goes to a purple screen for some seconds and then the monitor stops recieving any signal.

I looked for it and found [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/986524"), if you scroll down to post #20 you car read thar there's a PPA repository: Updated and Optimized Open Graphics Drivers. This works for most of the people, but not me. I tried the PPA, and then remove it and go back to the regular repository packages. Any clue how to fix this?!?!

Thanx!

---

