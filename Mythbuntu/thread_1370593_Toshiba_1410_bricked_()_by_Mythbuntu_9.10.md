---
title: "Toshiba 1410 bricked (?) by Mythbuntu 9.10"
date: 2010-01-02
forum: Mythbuntu
---

### Post by latrodectus on 2010-01-02
Hello world,

this is my first post in the Ubuntu forums. I have been using Ubuntu on various platforms for quite a long time, but now I am stuck with an issue, therefore I would ask for some help. 

The following happened:
I have installed Mythbuntu 9.10 on my Toshiba Satellite 1410 notebook (Mobile Celeron 1.8GHz / 512M / 160G). Everything went fine, have also installed the driver for my Linksys WUSB600N WiFi stick using ndiswrapper.
I started watching a divx movie on my LCD TV connected to the HD15 port of the notebook and after a while, I closed the lid. The notebook went into standby and since then I have not been able to wake it up. 
When I turn it on, the fan spins up, however the screen remains black, no disk activity can be heard and the power LED starts blinking in amber (1s on - 1s off), like in normal standby state. This blinking rhytm is not an error code, but the sign of being in standby. 

I tried the following:
1. Took battery and AC power out, held power button for 90s - after turning on, still standby mode with spinning fan.
2. Took battery and AC power out for about 72 hours - still standby mode with spinning fan.
3. Took battery, AC power and CMOS battery out for about 90 min - still standby mode with spinning fan.

At this point I am a bit confused...
Why does the notebook go into such strange state that the fan is spinning, but the LED shows standby?
Where could this information be stored that it should go into this state (CMOS battery was removed for 90 minutes)?

Has anyone experienced similar issues?

Thanks in advance,
latrodectus

---

### Post by eljeffe on 2010-01-02
Not an answer, but I had a similar problem with my desktop. I accidently hit the suspend button on my multimedia keyboard and it went into that same state. For me, removing the power cord and holding the power button did work. I did have to do a hard reset (reboot button) when it started the boot, but it did come back.

It seems that mythtv has a very bad suspend state issue.

---

### Post by latrodectus on 2010-01-03
Lucky you! :)
I have read dozens of threads on various boards regarding issues with standby on Ubuntu 9.xx, but noone seems to have such serious problem like me.

---

### Post by busuttils on 2010-01-06
Looks like we hit the same problem on just about the same days.  I had an old Toshiba 1410 and dicided to install a minimal ubuntu setup.  Then I added gnome, openoffice and a couple of other goodies.

Whilse answering a phone call I closed the laptop lid and the laptop triggered the hibernate state.  Sadly I have a bricked laptop with the exact problem as described by [latrodectus]("http://ubuntuforums.org/member.php?u=989588").

I opened up the laptop and disconneded the RTC battery to make sure the BIOS returns to a decent state.  Tried after two hours and the laptop still runs with the fan at full speed, but no activity.  Have disconnected the RTC and left it overnight.  My hopes are not very high.

Anyway.  anyone using Toshiba 1410 on Ubuntu please be warned.  Furthermore I do not think that this is a coincidence as several other posts can be found in other forums stating that this state does not always work properly.

---

### Post by latrodectus on 2010-01-06
> **busuttils said:**
> Looks like we hit the same problem on just about the same days.  I had an old Toshiba 1410 and dicided to install a minimal ubuntu setup.  Then I added gnome, openoffice and a couple of other goodies.

Whilse answering a phone call I closed the laptop lid and the laptop triggered the hibernate state.  Sadly I have a bricked laptop with the exact problem as described by [latrodectus]("http://ubuntuforums.org/member.php?u=989588").

I opened up the laptop and disconneded the RTC battery to make sure the BIOS returns to a decent state.  Tried after two hours and the laptop still runs with the fan at full speed, but no activity.  Have disconnected the RTC and left it overnight.  My hopes are not very high.

Anyway.  anyone using Toshiba 1410 on Ubuntu please be warned.  Furthermore I do not think that this is a coincidence as several other posts can be found in other forums stating that this state does not always work properly.

Uh-oh, not good. There's something definitely screwed up, as suspend was working flawlessly on lid closing for me in earlier releases (e.g. 7.10, 8.04).
Anyways, I've taken it to service, hopefully they can wake it up. 
I'll come back when I have more information.

---

### Post by busuttils on 2010-01-06
> **latrodectus said:**
> Uh-oh, not good. There's something definitely screwed up, as suspend was working flawlessly on lid closing for me in earlier releases (e.g. 7.10, 8.04).
Anyways, I've taken it to service, hopefully they can wake it up. 
I'll come back when I have more information.

Would appreciate it if you could share the tech news.  This laptop was an experiment and I am not took keen to put any money into it.  

BTW, I checked again and the laptop is definitely hang in some state of limbo ....guru meditation...

---

### Post by latrodectus on 2010-01-08
Update, the service just called me. 
They had spent many hours on measuring the motherboard with multimeter. Power has disappeared from about half of the mobo. 
As they are not able to wake the laptop up, they have to replace some power-related parts. 
3 manhours + some parts = ~100 EUR...

Toshiba Satellite 1410 owners with Ubuntu 9.10 pay attention! 
First step after install should be disabling standby and hibernate!

---

### Post by busuttils on 2010-01-08
> **latrodectus said:**
> Update, the service just called me. 
They had spent many hours on measuring the motherboard with multimeter. Power has disappeared from about half of the mobo. 
As they are not able to wake the laptop up, they have to replace some power-related parts. 
3 manhours + some parts = ~100 EUR...

Toshiba Satellite 1410 owners with Ubuntu 9.10 pay attention! 
First step after install should be disabling standby and hibernate!

Have tried another route to see if that is the problem also.  I tried to check the magnetic switch which invokes standby when the lid is closed.  Still no luck.  My last resort was going to be the replacement of power related parts....but I will probably brick the baby as it's not worth it.  Thanks all lot for your help.

---

### Post by petekat03 on 2010-04-04
I have a Toshiba Portege R100 laptop that looks like its stuck in standby mode. In Ubuntu 9.10 I found that hibernate wasn't working so I setup ubuntu to go into standby when I press power button. After pressing the power button it went to a blank screen and sat there for the next 5 minutes. So I forced the laptop OFF.
 
Now when I try to boot the laptop, the Power On (DC ON) LED just constantly flashes amber at about 1sec On, then 1sec Off - with a blank screen and the hard drive spinning up.
 
I was hoping to find a BIOS factory reset jumper, but I haven't had any luck yet. At the moment I've unplugged the RTC battery in the hope that maybe after a day or so it may reset BIOS.
 
I also noticed someone with a Toshiba M200 had the same issue with standby.

---

### Post by iponeverything on 2010-04-04
This is strange. Mythbuntu 9.10 install on a box with a GeForce 6100SM-M MB, caused the box to hang right after post. I was still able to get into the bios, but it would not move beyond it. I disconnected everything from the MB and removed the battery and let it sit for the night, in the morning everything seemed to be back to normal. But, for the sake of marital bliss, I didn't put mythbuntu 9.10  drive back into the machine. Perhaps the Mythbuntu 9.10 install is doing some kind of probe that is killing boxes....

---

### Post by chaanakya_chiraag on 2010-04-21
I use regular Ubuntu, but I have the same problem.  I'm using a Portege m200 (but I'm not the poster mentioned above). Fan runs at full speed, nothing else turns on, beeps whenever I press a key on the keyboard.

---

### Post by volkswagner on 2010-04-21
I don't think Ubunutu is the root of the cause.  The Toshiba 1410 has some bugs in the power management and/or BIOS.

I had a similar issue on Satellite 1415-S105.

I can't say what fixed it, but I nearly gave up on it.

Verify the voltage of the CMOS battery is putting out 3V.

Verify the power supply is putting out proper voltage.

Let it sit for a couple months and try again...Ha Ha Ha.

Really, I am not sure what fixed it, but it just started working.

By the way, it was running Windows XP.

Does the machine react to the play button, while laptop is off?  When mine had the issue, pressing the play button would act similar to pressing the power button.  I think that machine is supposed to play DVD without the OS, but not sure.

---

