---
title: "Will 9.04 work with my Atheros AR5007EG?"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by Izula on 2009-04-24
Without alot of fiddling around, will Jaunty work with AR5007EG?

I'm ready to leave windos....but couldn't get it to work previously.

---

### Post by t0mppa on 2009-04-24
No personal experience about this, but from a quick search, it looks like if you have a 32-bit system, it shouldn't be too big of a hassle, but for a 64-bit system, it might take quite a bit of time and trying different things out. Incidentally, the same seems to apply for XP, so it's not a Linux-only eccentrity. :)

My Atheros card (different chip) worked nicely after the upgrade, without any need to set things up further, after I had it working on 8.10. Unlike my display drivers, which are giving me a headache now.

---

### Post by dummiebeginner on 2009-04-25
I will follow this thread because I have the same wifi card and same problem.

Even worse, when trying to install some drivers following some instructions given somewhere it meesed up with my wire connection and now I am writing from Windows because I have no internet from Ubuntu at all.

I have this Fujitsu Siemens Esprimo V5535 with wifi Atheros AR5007EG and so far nothing that I have tried could make it work.

If anyone knows how can I fix my ethernet connection (driver sis191) I will appreciate it.

---

### Post by Jpedros2 on 2009-04-25
In my **hp Pavilion dv7-1110es** with **Atheros AR5007**, wifi works without ndiswrapper perfectly.
But I don't know if AR5007 is the same of AR5007EG.
--
Jesús

---

### Post by duderoth on 2009-04-26
I just tried it(Kubuntu 9.04) and No it doesn't on mine I have Acer Aspire 5315 with a AR5007EG.
 It doesn't register the driver and the wireless indicator stays off even when you press the button to start it up.
 It does look like people have had success with ndis wrapper but it's not effortless.
I've downloaded several cd bootable distros and the only one I have gotten to work is
Mandriva. I'm sure Ubuntu will catch up eventually. 


            Duderoth

---

### Post by tensop on 2009-04-26
acer 5315 and AR5007EG working out of the box here.

WIFI light does not work. however the wifi does turn on / off with the button control.

---

### Post by woopud on 2009-04-26
Toshiba satellite L305 with Atheros AR5007EG works right out of the box with Ubuntu 9.04, no fiddling needed.

---

### Post by duderoth on 2009-04-27
Ok I downloaded Ubuntu 9.04 and cd booted it.
The wireless works fine (acer aspire 5315-2142 with ar5007eg wifi)

Previously downloaded kubuntu 9.04 yesterday that didn't work(*shrug).
But Ubuntu works :P

---

### Post by Ben Crisford on 2009-04-27
> **t0mppa said:**
> Unlike my display drivers, which are giving me a headache now.

My display drivers ***and*** my atheros drivers are driving me nuts :'(.

(no pun intended).

---

### Post by constable0802 on 2009-04-29
I had 8.11 and got the ar5007ag to work there but I upgraded to 9.04 last night and now no witeless.:confused:

here is a link to the thred I used to make it work again
[http://ubuntuforums.org/showthread.php?t=1134165&highlight=atheros+ar5007eg](http://ubuntuforums.org/showthread.php?t=1134165&highlight=atheros+ar5007eg)

---

### Post by reedler on 2009-08-28
Ok, I have an acer aspire 5050. I installed ubuntu 9.04 yesterday and my atheros ar5007eg worked fine. I noticed my acer needed a bios upgrade so i did that. I had to reinstall ubuntu today using the same iso cd. Now my atheros will not work. I have tried many suggestions online and still not working. I can get my network to show up but I use WPA PSK and it will not authenticate. Also my SSID is hidden. Any suggestions much appreciated.

---

### Post by cmcanulty on 2009-09-26
I can't get mine to work and have tried a lot of patches. Where can I get the .inf file I need for the windows wireless I can only find a .exe file and a .sys file?

---

### Post by bkratz on 2009-09-26
> **cmcanulty said:**
> I can't get mine to work and have tried a lot of patches. Where can I get the .inf file I need for the windows wireless I can only find a .exe file and a .sys file?



Please look at this site, read the whole thing since it tells later on to replace statements regarding Intrepid with jaunty.

[http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html](http://www.prash-babu.com/2008/12/how-to-configure-atheros-ar5007eg-or.html)

Good Luck!

---

### Post by cmcanulty on 2009-09-27
I read it twice but don't see any reference to Jaunty,thanks:)

---

### Post by cmcanulty on 2009-09-27
Ow, wow, I got it! I had neglected realizing  to reboot and that did it Thanks mucho!!! Now if [I] could just get my broadcom BCM  4306 on my main laptop to go wireless I would be happier. I have tried everything with that one.

---

### Post by cmcanulty on 2009-09-27
Solved, I tried to mark thread solved on thread tools above but that option isn't there, thanks everyone!:popcorn:

---

