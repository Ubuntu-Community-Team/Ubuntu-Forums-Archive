---
title: "[SOLVED] Internet &amp;quot;lockup&amp;quot; problem"
date: 2008-12-13
forum: Networking &amp; Wireless
---

### Post by Ben Page on 2008-12-13
Hello guys!
As you can notice, im new to these boards.
Im a fresh linux user, downloaded Ubuntu 8.10 a few days ago. Took me about one day to adapt to the new gui, phylosophy, repositories, packages and stuff. Im a long term Windows user now at expert level, so being a complete noob to Ubuntu is a completly new experience. I must admit that I like this distribution (8.10), 3d cube is awesome, I have not noticed many bugs and the system is very stable, more stable than windows systems. Looking forward to making Linux my primary system (but later).

...thats for the introduction, here goes the question...

I have internet lockup problems, after installation the system recognized all my hardware, and configured it properly, even network and I could use internet right away, speeds are normal, but after some time or after some activity in the system (by me, like opening the terminal and VLC player and rotating the cube at the same time, or browsing  two pages at the same time and downloading the packages or torrent) internet just locks up, there is no flow in any direction, and when I try to "refresh" the connection, the network applet is doing something bu then it gives me a message that it cant get the ip adress from the network and thats it, i have to restart the system and then it works again?!
Im thinking this is due to my provider because I have this problem (but only sometimes) in Winblows, but then I go to networg managing , disable the network and reenable it and it reconnets, finds the adress, and all is good. So logicaly I tried the same thing in Linux, restart the network trough the terminal ( dont know the code I have it written down) but nothing happens eve though the terminal tells me it has restarted the network. I tried to find some kind of a device manager to disable and reenable the network there, but there is no windowslike DMgr.

..so how can I restart the network, or some process witch is loading the network while bootong (or stuff like that)? Tried to restart the applet but it a no-go.

This is the only problem I have with Ubuntu, and its the only thing its keeping me from making Ubuntu as my primary sys.

Network adapter is Realtek RTL8139/810x family, integrated on Foxconn ati amd MB, and im routing the connection through Aolynk DR814 ADSL2+ BB.

whoah, there is quite a lot of thext here! Anyways, this is a strange problem, so i had to explain it more, hope there can be a solution to this...

Thnx for reading

---

### Post by Ben Page on 2008-12-14
Nothing?! Not even a clue?](*,)

---

### Post by Ben Page on 2008-12-16
Unbelievable that nobody knows!
I seem to have found a solution, not for the lockups though, but I have found a Knetwork manager in app database witch gives me the possibility to restart the connection without having to restart the whole system.
So download the knetwork manager and replace the standard NM with it, if someone has similar problems...

---

### Post by Ben Page on 2008-12-17
I really feel like a loony now for talking to myself on my own thread (and probably 'am), but just wanted to let you know that after reboot, this problem presist, and i can't restart the network. Just to let you know, so you dont install and uninstall your software for nothing...

Still expecting a solution...if somebody knows...:confused:

---

### Post by Ben Page on 2009-01-08
All (my) internet issues are solved by doing a "real" installation of Ubuntu, this issue was regarding a wubi install (witch is a virtual install, and its tolerable as such).

---

