---
title: "RTL8187 Driver Solution on Jaunty"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by MeanEYE on 2009-05-05
For all troubled souls out there heaving problems with RTL8187 driver in jaunty... be at rest... there's a solution and a simple one too.

I tried everything from compiling drivers from realteks site to installing whole bunch of things. The thing is drivers for this wireless card worked in 8.10 but now I have problems...

Well I installed linux-backports-modules-jaunty and everything worked again. Somehow before installing I've removed rtl8187 driver from system :D so... maybe someone else can tell you more about that part...

Am just happy everything is working again :D

---

### Post by afeasfaerw23231233 on 2009-05-07
Hi. Does it work with WPA1/2 encryption on your rtl8187 wireless connection?

---

### Post by hav0x on 2009-05-18
I can confirm it works with WPA1/2.

---

### Post by Lex Luthor on 2009-05-29
Hello !

 Thank you for the tip ! I ran it here and everything seems to be good.
 But I noticed something strange. If my notebook is closer to my AP, it works perfectly, but as soon as I get a little far, I cannot navigate anymore. I have signal, but cant browse any page.

 I found this solution, but I did not test, since it has do compile, but I'll test soon. Sorry, but it is in portuguese:

[http://naoeval.blogspot.com/2009/05/como-utilizar-o-wi-fi-do-laptop-cce-w55.html](http://naoeval.blogspot.com/2009/05/como-utilizar-o-wi-fi-do-laptop-cce-w55.html)

-----
Update:

   I tried and didn't work. My notebook frooze as soon as ubuntu tries to load the new module...
   I am still having to use Window$ on my laptop...

---

### Post by MeanEYE on 2009-06-19
> **afeasfaerw23231233 said:**
> Hi. Does it work with WPA1/2 encryption on your rtl8187 wireless connection?

Yes everything works like it should...

---

### Post by MeanEYE on 2009-06-19
> **Lex Luthor said:**
> Hello !

 Thank you for the tip ! I ran it here and everything seems to be good.
 But I noticed something strange. If my notebook is closer to my AP, it works perfectly, but as soon as I get a little far, I cannot navigate anymore. I have signal, but cant browse any page.

 I found this solution, but I did not test, since it has do compile, but I'll test soon. Sorry, but it is in portuguese:

[http://naoeval.blogspot.com/2009/05/como-utilizar-o-wi-fi-do-laptop-cce-w55.html](http://naoeval.blogspot.com/2009/05/como-utilizar-o-wi-fi-do-laptop-cce-w55.html)

-----
Update:

   I tried and didn't work. My notebook frooze as soon as ubuntu tries to load the new module...
   I am still having to use Window$ on my laptop...

I found it that with backport modules my connection was more stable and signal much better all the time. Althow I usualy used it mainly within my apartment.

---

### Post by Lex Luthor on 2009-06-19
My notebook works setting rate to 5,5M, but only in the same room as my AP. If I go to another, I cannot connect.

I also noticed that the connection is stable, but it is "a little" dedicated to a program. Ex.: If I am downloading something and start another one, the first download rate drops to 0kbps until the second is finished.

---

### Post by MeanEYE on 2009-07-29
> **Lex Luthor said:**
> My notebook works setting rate to 5,5M, but only in the same room as my AP. If I go to another, I cannot connect.

I also noticed that the connection is stable, but it is "a little" dedicated to a program. Ex.: If I am downloading something and start another one, the first download rate drops to 0kbps until the second is finished.

Sorry for late reply. I had no experiences like that. For me back-port driver worked more stable than new one. With new driver my wifi connection broke every time I turned on torrents or anything more demanding.

Tho new driver has support for external On/Off switch, I hope only that ubuntu team fixes this soon...

---

### Post by slowtrain on 2009-11-15
Before you get too triumphalist about having solved the RTL8187 problem, you might want to hear about my experience.  I installed the backports as well and, well, nothing--I still can't get out to the Internet.  One difference in my situation is that my device has a RTL8187L chipset, not the RTL8187b, which may be what you have.  Perhaps backports don't work with the "L" chipset.

Problem is that it's often hard to tell exactly what chipset you are getting till after you buy the wifi card or usb stick.  I bought 3 over the course of a week, all of which on the surface at least, should have worked w/ Ubuntu.  But then I find out such things as that the Belkin F5D7050 wifi usb stick presumably works fine if you have v3000 and not at all if you have v4000.  

Someone knowledgeable about stuff like this should put together a wifi device buyer's guide in the community documentation that gives very specific information about what works and what does not and how buyers can know what they are getting.  The current documentation is next to useless and is likely driving people away from Ubuntu.  

As for me, I still don't know where to look to find something that will work for my system.

---

### Post by slowtrain on 2009-11-24
I discovered something that works on my system with the RTL8187L wifi pci card.  First, I installed wicd (need to uninstall network manager).  I can connect to my system using the wicd window (hidden network, so I feed it the ESSID).

Whenever I want to suspect or hibernate, I have to do this song and dance to insure my wifi is still available on wake-up (and that my system doesn't hang, at least some of the time):  a) I disconnect using wicd, b) I shut down the wlan0 interface using this from the command line:  sudo ifdown wlan0, c) I remove the pci card driver module from the operating system with:  sudo modprobe -r rt61pci .  Now, the system is safe to sleep or hibernate.  After wakeup, I issue this to reinstall the driver:  sudo modprobe rt61pci .  Wicd does the rest and 'automatically' connects to the network (I do have the auto connect box checked for my network).

This is still a pain, but I don't have to deal w/ my system hanging or being unable to reconnect to the wifi router.

Hope this helps someone.

---

