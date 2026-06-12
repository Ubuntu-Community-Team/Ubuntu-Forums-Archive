---
title: "No internet after Dapper upgrade"
date: 2006-06-15
forum: Networking &amp; Wireless
---

### Post by Curlydave on 2006-06-15
I recently intalled Dapper clean from the install/live CD. It worked fine, with the exception of the too-low resolution issue which was more of an annoyance than anything else. (went away after I finished the installer and setup video card drivers.)

My brother had been using Breezy, and he was recently prompted to upgrade to the new version if he wanted. He did it and the install went ok, but killed his internet and we can't get it back. We're using a DSL connection, but through a router, so the computers see the connection as DHCP. What's up?

If I boot it up from the install/live disc, it has internet, but not when booting to the HD install.

---

### Post by Kilz on 2006-06-15
[QUOTE=Curlydave]I recently intalled Dapper clean from the install/live CD. It worked fine, with the exception of the too-low resolution issue which was more of an annoyance than anything else. (went away after I finished the installer and setup video card drivers.)

My brother had been using Breezy, and he was recently prompted to upgrade to the new version if he wanted. He did it and the install went ok, but killed his internet and we can't get it back. We're using a DSL connection, but through a router, so the computers see the connection as DHCP. What's up?

If I boot it up from the install/live disc, it has internet, but not when booting to the HD install.[/QUOTE]
You may want to take a look at this page to help you.
[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643)

---

### Post by connellr on 2006-06-20
For what its worth I had the exact same problem you mentioned.

I have 2 computers:
1) A custom AMD PC I built
2) Your standard P4 Dell machine.

I installed Dapper on The AMD machine as a fresh install and had no problems.  Everything worked like a charm.

In order to not loose some data I tried doing an upgrade on the Dell machine, and it seemed that everything was going to work, but there was no network connection. (The network connection works fine when booting to the Live CD).

The command ifconfig shows only the loopback connection, but no eth0.  The command 'sudo /etc/init.d/networking start' gives an error saying something to the extent of "SIOCSIFADDR: No such device".  When I look in Gnome's networking configuration wizard I see an Eth1 but no Eth0 ... the Eth1 is not configured.  I tried to configure it for DHCP, but had no luck.

I have seen someone sugest changing the MAC address given for eth0 in /etc/iftab to match the MAC address of my network card to fix this problem ,but I havent had time to test this yet.

Changing all instances of eth0 in /etc/network/interfaces to eth1 may also work, but I would rather have my connection be called eth0. ](*,)

---

### Post by TimJ on 2006-06-20
I had a similar sounding problem but fixed by this suggestion in thread [http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

May not work but worth a look.

---

