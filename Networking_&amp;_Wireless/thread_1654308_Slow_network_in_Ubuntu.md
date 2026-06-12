---
title: "Slow network in Ubuntu"
date: 2010-12-28
forum: Networking &amp; Wireless
---

### Post by ubuking on 2010-12-28
I have just rewired my LAN using Cat 6 cables. Download- and Upload speeds to my main machine are great :

[[IMG]http://www.speedtest.net/result/1087702245.png[/IMG]](http://www.speedtest.net)

However, it seems my LAN speed is very slow. when I copy large files from my main desktop pc to my mediaplayer, I only reach a speed of 3,7 MB/s in Ubuntu 10.10 using SMB protocol to connect to mediaplayer. I use a Sitecom WL351 Router that works fine as far as I can see. Using my dualboot Windows 7 I can copy the same large files using same setup (same pc to same mediaplayer) I can copy with almost 10 MB/s. I appreciate a little protocol overhead in Ubuntu, but this seems to be a little too much. 
Any ideas how I can increase networkspeed in Ubuntu?

---

### Post by ubuking on 2011-01-16
> **ubuking said:**
> I have just rewired my LAN using Cat 6 cables. Download- and Upload speeds to my main machine are great :

[[IMG]http://www.speedtest.net/result/1087702245.png[/IMG]](http://www.speedtest.net)

However, it seems my LAN speed is very slow. when I copy large files from my main desktop pc to my mediaplayer, I only reach a speed of 3,7 MB/s in Ubuntu 10.10 using SMB protocol to connect to mediaplayer. I use a Sitecom WL351 Router that works fine as far as I can see. Using my dualboot Windows 7 I can copy the same large files using same setup (same pc to same mediaplayer) I can copy with almost 10 MB/s. I appreciate a little protocol overhead in Ubuntu, but this seems to be a little too much. 
Any ideas how I can increase networkspeed in Ubuntu?

Tweaking Samba did improve speed slightly. 
Moving to NFS did resolve the issue. Please continue to read [here for more details]("http://ubuntuforums.org/showthread.php?t=1612842").

---

