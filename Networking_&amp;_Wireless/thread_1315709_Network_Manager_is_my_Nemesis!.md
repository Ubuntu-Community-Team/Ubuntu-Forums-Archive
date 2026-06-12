---
title: "Network Manager is my Nemesis!"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by deparvius on 2009-11-05
I've had problems before with interface switching, and thought I had it beat:

[http://ubuntuforums.org/showthread.php?t=1312938](http://ubuntuforums.org/showthread.php?t=1312938)

After removing and reinstalling PulseAudio to fix the sound problem after update (since sound doesn't quite work in Karmic with Kubuntu), the problem came back, and I cannot fix it.  Only this time, boot time is extended by a minute or two as boot delays at the console login screen before X windows loads up.

The setup:  
On eth0 (when working) is run  a fileserver using Avahi to my local LAN, and on eth1 is the internet line from the local router.

The problem:
Again, the problem is that at somepoint during boot, Network Manager swaps eth1 and eth0 and then deletes one of the interfaces.  

Troubleshooting:
If I swap them manually in /etc/udev/rules.d, Network Manager doesn't swap them, but of course this doesn't work for me.  If I swap the cables as well, internet works.  Network manager does insist on this layout, even though I'd much prefer to use the gigabit card for local LAN fileserver and the 100 MB card for internet.

Network Manager seems like wonderful magic when it works, but when it doesn't, it is a giant broken black box of misery.

---

