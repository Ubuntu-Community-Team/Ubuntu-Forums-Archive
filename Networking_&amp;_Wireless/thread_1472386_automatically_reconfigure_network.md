---
title: "automatically reconfigure network"
date: 2010-05-04
forum: Networking &amp; Wireless
---

### Post by pernest on 2010-05-04
Hi

I having a look at some of the item in the Ubuntu software centre, I installed Avogadro but when I tried to launch it, the system locked completely. No ctrl+alt+F3, not even a response to caps lock (10.04 really is getting close to windows functionality :)).

When I rebooted the network just would not work, no ping, no internet address listed for eth0 with ifconfig. I found a solution on the net (other machine), when I looked in /etc/network/interfaces it only contained

auto lo
iface lo inet loopback

I added 

auto eth0
iface eth0 inet dhcp

at the top of the file and then did a network restart and now the internet works again.

What I would like to know is, 
1) What should a /etc/network/interfaces look like, have I missed anything?
2) Is there any way to reinstall networking so that if any other config files are messed up then they will be sorted out?

---

### Post by pernest on 2010-05-04
I've just noticed that the network manager applet has also disappeared. When I go to system>preferences>Network connections, no network connections of any sort are show, even though I am connected to the internet.

---

### Post by pernest on 2010-05-04
Hi, I originially posted this in the general forum, but it sank without getting a reply.

Hi

Had a complete hardware lockup and when I rebooted networking wouldn't work, no ping, no internet  address listed for eth0 with ifconfig. I found a solution on the net  (using my other machine), when I looked in /etc/network/interfaces it only  contained

auto lo
iface lo inet loopback

I added 

auto eth0
iface eth0 inet dhcp

at the top of the file and then did a network restart and now the  internet works again.

What I would like to know is, 
1) What should a /etc/network/interfaces look like, have I missed  anything?
2) Is there any way to reinstall networking so that if any other config  files are messed up then they will be sorted out?

Also system>preferences>Network connections, does not show any network connection of  any sort are show, even though I am connected to the internet.

---

### Post by Iowan on 2010-05-04
Threads merged.
Three hours is a bit premature to panic and start another thread.

A Network Manager-controlled machine will have only the two lines defining "lo". There are some other threads around that give some options about getting NM-applet back. I'll need to look around for one...

---

### Post by pernest on 2010-05-04
Sorry about that, I just saw my post sink onto page 6 without a reply and thought that nobody would ever see it.

I think I'm just going to reinstall because I have no idea which configuration files were corrupted during the crash. If I could find out which files are suspect and a way to fix them, then I would give that a go. As I have my home and data partitions separate from root then I should be able to reinstall relatively painlessly.

Cheers

---

### Post by Iowan on 2010-05-04
Now that I'm not on company time...
[Here]("http://ubuntuforums.org/showthread.php?t=1471824") is a (solved) thread about restoring nm-applet, and here's [another]("http://ubuntuforums.org/showthread.php?t=1074132"). 
Hope one of them will help!

---

### Post by pernest on 2010-05-05
Thanks for the reply Iowan, but those threads weren't really relevant to my problem, it wasn't just that the newtwork manager was missing. There were some configuration files that got buggered when there was a hardware lock and I wanted to for the system to reconfigure networking as if it was a fresh install.

Anyway, I've reinstalled and am trying to get things back to the way I like them.

thanks for trying

---

