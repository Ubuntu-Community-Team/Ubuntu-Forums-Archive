---
title: "Wireless Troubles..."
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by Slayer. on 2010-01-31
So my friend has an Acer Aspire. I'm not sure the exact model, but I can find out tomorrow. She installed Ubuntu for the first time a week ago, because she was tired of Windows. She's well aware of how difficult Linux can be for beginners, and the fact that she won't be able to use some of her favorite Windows programs. Her only problem is the wireless. I had a problem setting up my wireless when I first installed Ubuntu, so I figured "Hey, I know how to fix this, I'll take care of it, no problems." Well, I took a look at her computer, and it turns out she doesn't have the required wireless driver. I believe it's some form of B43 driver. The problem is, she can't install it, because of course, she has no internet, so she can't download it. I found a website that has several B43 Packages. I was wondering if I could just put the right one on a flashdrive, and transfer it to her computer. If so, how do I install it?

---

### Post by warfacegod on 2010-01-31
You're scheme might work depending on what dependencies the driver will need. Installing it depends on what type of compressed file it's in.


Would that be Slayer as in metal?

---

### Post by pdc on 2010-01-31
some would suggest this is the definitive Broadcom howto

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by Slayer. on 2010-02-02
> **warfacegod said:**
> You're scheme might work depending on what dependencies the driver will need. Installing it depends on what type of compressed file it's in.


Would that be Slayer as in metal?

Well, I found several packages. Some are .deb files, others are .tar.gz

And yes. Slayer as in metal.

> **pdc said:**
> some would suggest this is the definitive Broadcom howto

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

Thanks, I'll check it out. :)

---

### Post by warfacegod on 2010-02-02
Go with .deb packages. Try to get all of the dependencies for it. If the driver is in Synaptic, check it's properties.


I first heard South Of Heaven when I was nine. Twenty one years later, I'm still not the same!

---

### Post by warfacegod on 2010-02-02
This may be of some use in your nefarious plot:

[http://ubuntuforums.org/showthread.php?t=1090731&highlight=make+trusted+local+repository]("http://ubuntuforums.org/showthread.php?t=1090731&highlight=make+trusted+local+repository")

---

### Post by Slayer. on 2010-02-02
Thanks for all your help, guys. Got it working! :)

---

### Post by tattyt on 2010-02-03
my troublesare similar i have an HP laptop just installed ubuntu 9.10 never run linux before so i am very much a newb still aslo but i have a wireless linksys router the WRT54G model with a boadcom 802.11b/g WLAN card and i cant connect either it says its the wirelss is DISABLED and i have tried about 6 different SUDO  tricks with no success i have never done a full device configuration before i want to go to network admin school possibly  this smmer thats why i downloaded and installed the ubuntu to try and gain knowledge on  UNIX platform but its useless without the net rightnow to get tutorials i THANK all of ubuntu geeks for creating and supporting this Operating System it seems Very cool  ANY ADVICE  THAT CAN GET ME UP AND GOING thanks again you can PM me also

---

### Post by warfacegod on 2010-02-03
> **tattyt said:**
> my troublesare similar i have an HP laptop just installed ubuntu 9.10 never run linux before so i am very much a newb still aslo but i have a wireless linksys router the WRT54G model with a boadcom 802.11b/g WLAN card and i cant connect either it says its the wirelss is DISABLED and i have tried about 6 different SUDO  tricks with no success i have never done a full device configuration before i want to go to network admin school possibly  this smmer thats why i downloaded and installed the ubuntu to try and gain knowledge on  UNIX platform but its useless without the net rightnow to get tutorials i THANK all of ubuntu geeks for creating and supporting this Operating System it seems Very cool  ANY ADVICE  THAT CAN GET ME UP AND GOING thanks again you can PM me also

I would start with the link pdc posted.

If the wireless is disabled, right click the network icon on the top panel and make sure there is an x next to "Enable Wireless".

---

