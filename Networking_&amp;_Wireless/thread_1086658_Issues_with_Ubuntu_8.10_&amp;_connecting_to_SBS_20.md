---
title: "Issues with Ubuntu 8.10 &amp; connecting to SBS 2003"
date: 2009-03-04
forum: Networking &amp; Wireless
---

### Post by ashpuk on 2009-03-04
HI all,

Recently installed Ubuntu 8.1 on a works computer, but having difficulties getting to work correctly with the network. 

Strangely it was working fine yesterday (Got Evolution to sync with exchange server & access shared folders fine) however I am having major issues with it today.

Network consists of:
1 x Windows SBS 2003(Wired)
2 x XP Pro Stations(1 Wired, 1 Wireless)
1 x Ubuntu 8.10(Wireless)
2 x printers
1 x dlink nas drive (used for backup)
Linked by a Netgear Wireless Router.

I have installed the most up to date version of samba (i think) and I have followed dmizers guide ([http://ubuntuforums.org/showthread.php?t=288534)to](http://ubuntuforums.org/showthread.php?t=288534)to) try and mount the network drive again (used Nautilus the first time which just seemed to spring into life after a bit). This did not work (said that I was not entereing the correct TCP address) so I decided to test the connection by pinging the server.

The server will not even respond to a ping from the Ubuntu computer! (of course it works with all the other comps..) however I can ping everything else on the network ok.

Since everything appeared to be working fine yesterday has anyone any ideas as to why this has happened?!

---

### Post by ashpuk on 2009-03-04
Glad nobody wasted any time with this - after a lot of faffing about I have realised it was a conflicting IP issue with a user VPNing into the network.

---

