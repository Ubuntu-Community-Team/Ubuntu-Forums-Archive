---
title: "Wireless connection regularily drops with torrents"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by agestrada on 2011-04-24
My wireless connection drops after a while when downloading torrents. I have to reconnect manually. Current configuration is Macbook Pro 5.5 with Broadcom card and Lucid. I've tried with Transmission and KTorrent. It's not a network problem as my Win laptop works smoothly and with higher transfers rates (i.e. 1MB/s in Win vs. 300KB/s at most in Ubuntu).

Anyone with the same symptoms?

Thanks,

---

### Post by SeijiSensei on 2011-04-24
Usually you have too many simultaneous connections (note, not bandwidth).  Consumer routers don't have enough memory to masquerade the dozens of TCP connections that BT creates.  Usually pulling the power cable out and waiting ten seconds will clear the memory and things will flow smoothly again.  Reduce the number of simultaneous connections in your client.  In KTorrent, for instance, it's in Settings > Configure > Network.  I have a global limit of 50.

---

### Post by agestrada on 2011-05-04
Thanks for your reply, I've tried that without luck. Although I understand what you said, that doesn't explain however why it works flawlessly in Windows with utorrent and a limit of 200 connections. I am sure the problem is with Ubuntu as the same machine and network work OK with MacOSX and WinXP_SP2.

Any other idea/explanation?.

Thanks,

---

### Post by agestrada on 2011-05-08
Any news regarding this problem?

---

### Post by rlklee on 2011-06-06
Bump. Same exact problem here. Perfect behavior on Windows. Same broken behavior on Fedora 14 and 15 and the current and previous Ubuntu release.

Because the problem is cross-distro, I am thinking it is a driver or kernel issue, but I'm not knowledgeable enough to either verify or falsify that.

---

### Post by nbound on 2011-06-07
I'm having same problem on an Atheros device here.

[http://ubuntuforums.org/showthread.php?t=1775726](http://ubuntuforums.org/showthread.php?t=1775726)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/793397](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/793397)

---

### Post by rlklee on 2011-06-07
Nbound's solution worked for me. Thanks for the info Nbound, it's a great help to get this problem solved. It's been bugging me for months. I figured it was a driver issue, but I'm still wondering exactly how the problem even came to be...

**Edit**: Never mind, problem persists. I spoke too soon. My torrent connection dropped the wifi after about an hour.

---

### Post by nbound on 2011-06-07
> **rlklee said:**
> Nbound's solution worked for me. Thanks for the info Nbound, it's a great help to get this problem solved. It's been bugging me for months. I figured it was a driver issue, but I'm still wondering exactly how the problem even came to be...

**Edit**: Never mind, problem persists. I spoke too soon. My torrent connection dropped the wifi after about an hour.

Sorry the solution I posted is only for faster speeds on applicable devices, but after its done I have a similar issue as everyone else hete

---

