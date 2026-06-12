---
title: "Ethernet Problem -802.1x protected wired network"
date: 2010-02-16
forum: Networking &amp; Wireless
---

### Post by sfeeley on 2010-02-16
I just installed xubuntu (8.04) onto an old Sony vaio laptop and am a complete Linux newbie.  After playing around, it seems to be running well, except it is not detecting my wired Ethernet connection correctly.
   
  When I plug in the wire the connection icon spins for a few seconds and if I put cursor over it, it reads: “requesting a network address from the wire network.”  Eventually it stops and shows two computers connected.
   
  If I click on the icon it says “connect to 802.1x protected wired network”
   
  If I click on it, it gives a dialogue box asking for network name, EAP method, Phase 2 type, etc, etc.
   
   ***What is 802.1x protected wired network?  Any other computer (and this one, when I was running another OS) connected automatically as soon as I plugged in.  
   
  If I right click on the connection icon, it says Active Connection Information
  Interface : Ethernet (eth1)
  Speed: 100mb/s
  Driver: e100
  All the other entries (IP, Broadcast address, etc) are 0.0.0.0
   
Long story short, firefox, updates, anything requiring the intenet seems to fail.
  I’m completely new to linux, so please be gentle in any answers.  Thanks so much!

---

### Post by sfeeley on 2010-02-16
bump... 
-Sorry, I made the mistake of posting in the middle of the night.  I don't know if this is allowed (I looked at the forum etiquette page). thanks!

---

### Post by bkratz on 2010-02-16
Really don't have an idea, but found three old threads, this one at least looks like it is promising.

[http://ubuntuforums.org/showthread.php?t=958021](http://ubuntuforums.org/showthread.php?t=958021)

others
[http://ubuntuforums.org/showthread.php?t=895276](http://ubuntuforums.org/showthread.php?t=895276)
[http://ubuntuforums.org/showthread.php?t=833404](http://ubuntuforums.org/showthread.php?t=833404)


Hopefully something there helps.


Also this old bug report
[https://bugs.launchpad.net/ubuntu/+bug/208646](https://bugs.launchpad.net/ubuntu/+bug/208646)

---

### Post by bkratz on 2010-02-16
And another

[http://ubuntuforums.org/showthread.php?t=813076](http://ubuntuforums.org/showthread.php?t=813076)

---

### Post by sfeeley on 2010-02-16
Thanks-- I had looked around but didn't see the first one: 
[http://ubuntuforums.org/showthread.php?t=958021](http://ubuntuforums.org/showthread.php?t=958021)

It looks promising and I'll give it a try later on.

---

### Post by sfeeley on 2010-02-16
Tried one of the suggestions offered 
( [http://ubuntuforums.org/showthread.php?t=958021](http://ubuntuforums.org/showthread.php?t=958021) )

typed sudo dhclient eth1 (as per instructions)

The following scrolled:
Listening on LPF/eth1/08:00:46:06:e8:6c
sending on "    "
sending on socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
""  interval 8 and 8 and 11 and 1
No DHCPOFFERS received
No working leases in persistent database-sleeping

other suggestions? -Thanks

---

### Post by sfeeley on 2010-02-16
also tried the other suggestion that bkratz offered
( [http://ubuntuforums.org/showthread.php?t=813076](http://ubuntuforums.org/showthread.php?t=813076) )

Again no luck.  The other posts don't seem to have answers. Other suggestions?  Thanks.

---

