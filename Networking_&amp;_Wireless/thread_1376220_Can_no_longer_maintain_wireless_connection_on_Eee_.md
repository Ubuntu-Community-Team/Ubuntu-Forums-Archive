---
title: "Can no longer maintain wireless connection on Eee 1005HA"
date: 2010-01-08
forum: Networking &amp; Wireless
---

### Post by n125 on 2010-01-08
Alright, so I formatted and redid my Ubuntu 9.10 partition. This is a completely fresh install, using kernel 2.6.31.14-generic i686. I have done nothing to this install, yet.

I first installed this version of Ubuntu near the end of December. My wireless connected immediately and I had absolutely no problems.

Yesterday morning, I was able to firmly connect to my home wireless network, and to my university's wireless network later on. But when I returned home, I found that I suddenly could no longer maintain a stable connection to my home network.

The netbook is in a dual boot Windows XP/Ubuntu set-up. When using the Windows on it, it has no problem establishing and maintaining a wireless connection; my desktop has no issues either. Since my other systems aren't having any problems, I assumed that I did something to Ubuntu, so I formatted the partition it was on and reinstalled the OS. Going back to square one didn't help. I don't understand why it worked just fine THEN, but not anymore NOW, with the exact same version.

What happens is that when the OS loads, it will connect and work for a random period of time; usually less than 5 minutes. Eventually I'll get extreme packet loss, which is SOMETIMES followed by a clean disconnect; if an outright disconnect doesn't happen (Network Manager icon still shows as connected), I'll just indefinitely fail to resolve everything. Trying to browse the Internet or update packages seems to expedite this occurrence. I may be able to reconnect at this point, but this will continue happening until I'll eventually no longer be able to reconnect--Network Manager will just keep asking me for my network key, no matter how many times I supply it. At this point, a reboot is required.

Anyway, I'd appreciate some help, as I've been really enjoying my time with Ubuntu, and would like to continue if possible.

I've appended logs from all of the tests recommended by the sticky topic. There are two sets--one made after I've lost connection and can no longer connect, and the other after a reboot and (temporarily) connected.


Ubuntu 9.10, 2.6.31.14-generic 1686
D-Link Dir-625
Atheros AR9285 Wireless Network Adapter (PCI-Express) on a Eee PC 1005HA


Thanks.

---

### Post by n125 on 2010-01-10
Bumping this. I rewrote the first post since I formatted and am still experiencing the same problem. Would appreciate some suggestions.

---

### Post by acascianelli on 2010-01-10
I too am experiencing this problem on my 1005HA.  By chance, do you have the kernel backport modules installed to fix the microphone problem?

---

### Post by n125 on 2010-01-10
> **acascianelli said:**
> I too am experiencing this problem on my 1005HA.  By chance, do you have the kernel backport modules installed to fix the microphone problem?

Nah, I never bothered setting up any of those devices since I don't use them.


But speaking of backports, before I formatted, I tried installing (going by memory)

> linux-backports-modules-karmic-generic
linux-backports-wireless-modules-karmic-genericto fix the disconnect problem. After rebooting, Firefox 3.5.7-something would no longer start, so that needed to be reinstalled. Once that was working, my connection was stable for about an hour and everything suddenly seemed to be back to normal, that is until my display shut off (as I had it set to do). When that happened, the system froze and needed a hard reboot. After that, it was back to the usual disconnects.

---

### Post by Aidam on 2010-01-13
I am having these problems on my Eee 1005-HA aswell. Bumpity!

---

### Post by renanfs on 2010-01-22
Same Problem as well guys... Need some help, please. I love ubuntu 9.10 and would like to continue using it. Thanks !

---

### Post by bkratz on 2010-01-22
> **renanfs said:**
> Same Problem as well guys... Need some help, please. I love ubuntu 9.10 and would like to continue using it. Thanks !

Here is a similar thread with a possible direction

[http://ubuntuforums.org/showthread.php?t=1367644&highlight=Eee+1005HA](http://ubuntuforums.org/showthread.php?t=1367644&highlight=Eee+1005HA)

---

### Post by n125 on 2010-01-23
Well, I solved my problem, but I didn't actually do anything; it kind of solved itself. 

I had to jump back to my Windows XP partition for a week or so, simply because I didn't have the time to work at this connectivity problem. In Windows, my wifi connection was rock-solid, but I eventually noticed that it was extremely slow after I tried downloading a file. I did a speedtest and found that I was getting less than 1000 kbps down/up, which was not right, and FAR below my ethernet speeds. By this point I figured that there was never anything wrong with Ubuntu in the first place and it was all my wifi's fault; and I was right.

I don't know how, but the speed fixed itself after a few days. I switched back to Ubuntu and my connection was once again very stable. It's been going strong for a few days now.

> **bkratz said:**
> Here is a similar thread with a possible direction

[http://ubuntuforums.org/showthread.php?t=1367644&highlight=Eee+1005HA](http://ubuntuforums.org/showthread.php?t=1367644&highlight=Eee+1005HA)

Looking at this, it seems that this individual also narrowed it down to the wifi network/router itself.

I guess if you're having connectivity problems then it might be worthwhile testing the wifi network itself rather than starting with the OS.

---

