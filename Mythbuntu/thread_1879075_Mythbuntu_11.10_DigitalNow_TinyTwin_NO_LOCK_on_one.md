---
title: "Mythbuntu 11.10 DigitalNow TinyTwin NO LOCK on one Tuner"
date: 2011-11-10
forum: Mythbuntu
---

### Post by daveshep on 2011-11-10
Gday everyone, I've been struggling since about June with DVB tuners. (I had a Technisat AirStar 2 which worked nicely until it died). I bought a Leadtek DTV2000DS which was supposed to work out of the box, and didn't work at all. I gave up on it..  

Then I bought a DigitalNow TinyTwin which is supposed to work out of the box, BUT only one tuner works. The tuner on adapter0 just will not lock. the signal strength is fine, and the other tuner works fine (although on one occasion it did refuse to lock but a system reboot fixed the problem).

I tried the TinyTwin in Windows 7 MCE and it works beautifully. Only problem is MCE is just not as good as mythtv... But I am tempted to try Media Portal... I really don't want to, but the Mrs has had enough (how many times have I said "i read that this is gonna work out of the box", then a month later i'm still trying to get it to work), and to be honest so have I ;) Any ideas?

---

### Post by goffa on 2011-11-16
The digitalnow tinytwin seems to be only partially supported [http://linuxtv.org/wiki/index.php/DigitalNow_TinyTwin_DVB-T_Receiver](http://linuxtv.org/wiki/index.php/DigitalNow_TinyTwin_DVB-T_Receiver)

There seems to have been a few patches sent for the af9015 based hardware, both your cards use this. [http://www.mail-archive.com/linux-media@vger.kernel.org/msg39006.html](http://www.mail-archive.com/linux-media@vger.kernel.org/msg39006.html)

I suggest you join the V4L mailing list and ask for their help. 

> Currently, the main development mailing list is hosted at vger.kernel.org. To subscribe, just send an email to [email]majordomo@vger.kernel.org[/email], with the body of the email containing subscribe linux-media.

---

