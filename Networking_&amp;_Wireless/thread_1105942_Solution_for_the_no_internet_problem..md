---
title: "Solution for the no internet problem."
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by yarivm on 2009-03-25
I have looked in to the problem and I myself had it about 2 hours ago, I have reinstalled the entire system on my netbook and the internet "magiclly" started to work.

I am _NOT_ telling you to reinstall, but I am telling you to run a system recovery from either the CD or the GRUN while the computer is loading.
(hit any key to enter the grub menu when it shows the 3 seconds count down.)

Enter the recover session or option according to what it will say and check to see if you have internet connection.

I managed to rescue my second computer like that and avoid reinstalling the entire system.

ALWAYS consult the online documents before doing any major system changes and make full use of UbuntuForums and ask all the questions you want to know before any major action.

It appears that has been some kind of unknown bug in the last update that caused some kind of problem with the DNS resolving.

I have checked all my system.log files and dmesg files and I foudn that it did not search in /etc/resolv.conf when it wanted to go to the internet.
There for something might have been changed accidently.
So just run a short system recovery and it will change that setting back.

I hope I helped,
Yariv.

---

