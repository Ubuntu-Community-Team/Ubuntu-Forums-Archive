---
title: "Virgin Netbook: fn+f2 for wireless doesn't work"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by DougEdey on 2009-07-22
So I got myself one of the free Virgin Media Freedom Netbooks, it boots by default with Wireless Off (no there's no way to change this) and when I had Windows XP and Moblin V2 on the FN+F2 combination worked perfectly, however now I put UNR on it doesn't work. 

showkeys doesn't show a keycode or signal trapped when I press FN+F2. What can I do to get this enabled?

---

### Post by DougEdey on 2009-07-22
So I found the solution by installing the backports package.

---

### Post by Paulmartin77 on 2009-07-27
Can you explane exactly how you used backports to get it to work? :confused: Mine is arriving soon and I would prefer to use UNR than Winblows.

---

### Post by DougEdey on 2009-07-27
Certainly, connect via a cable (or download the package) and run

sudo aptitude install linux-backports-modules-jaunty

Reboot, jobs done, wireless will always be off on boot and takes upto 10s for the kernel to recognise the change. Only problem I have now is with the inbuilt speakers being dead quiet (I can just hear them over the HDD when I put my ear next to it :()

---

### Post by macstevejb on 2009-08-16
Thanks for the info re wireless for this netbook. All up and running pretty much out of the box with Jaunty. 

However, like you, I cant get the onboard speakers to work...tried everything including compiling and installing the latest alsa drivers.

Can anyone more knowledgeble throw any new light on this issue please?

Regards

---

### Post by leeagt on 2009-08-17
Thanks for the tips on the wireless mate. I also have the issue with the sound :( anyone know how to fix it  ?

---

### Post by DougEdey on 2009-08-18
I'm going to raise a new thread for it. Also, I recommend NOT plugging the wireless dongle into the LEFT USB port, you get noise from the speakers (same as if you were getting a mobile call).

---

### Post by JamieM69 on 2009-08-18
Think that would work for the Jaunty Jackalope that you can get sent out?

---

### Post by leeagt on 2009-08-24
has anyone managed to get the sound working yet ? I've been trying for hours and still unable to get it working

---

### Post by DougEdey on 2009-09-18
Anyone with sound issues look in the other thread I made:

[http://ubuntuforums.org/showthread.php?t=1243256](http://ubuntuforums.org/showthread.php?t=1243256)


I found the issue.

---

