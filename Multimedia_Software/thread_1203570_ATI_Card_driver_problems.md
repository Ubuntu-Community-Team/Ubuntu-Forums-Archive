---
title: "ATI Card driver problems"
date: 2009-07-03
forum: Multimedia Software
---

### Post by Sandie555 on 2009-07-03
[FONT=Lucida Console][SIZE=2][COLOR=Navy]I've newly installed Ubuntu alongside XP. [/COLOR][/SIZE][/FONT][FONT=Lucida Console][SIZE=2][COLOR=Navy]After installing Stellaium on the Ubuntu I got the message that [/COLOR][/SIZE][/FONT][FONT=Lucida Console][SIZE=2][COLOR=Navy]openGL was not supported. So I installed a fglrx driver which seemd appropriate. Lost the Ubuntu, just getting a weirdly scrambled desktop. In the rescue portion of booting up I tried running aticonfig --initial which states that there is no supported adapter. Also tried reconfigure xserver-xorg which will do the keyboard but then won't go any further, just keeps going back to the main screen.
Synaptic won't display. I've even tried to reinstall the os but get error message that there is no root file--- so something along those lines. 

Any ideas would be helpful.:KS

Thanks SAndie [/COLOR][/SIZE][/FONT]

---

### Post by cinohpa on 2009-07-03
I actually had the exact same problem. Basically, you don't want to use the fglrx driver. 

Go to the ati website and use their driver there: 
[http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/](http://www.ngohaibac.com/how-to-install-ati-graphic-driver-for-ubuntu-904/)

^instructions on finding and installing driver. 

Someone more familiar with ubunutu will be able to tell you how to umount the fglrx driver from the rescue mode command line, but a little googling might do the trick. 

I just ended up reformating and trying again when I got to where you are. . .

---

### Post by loose111 on 2010-07-22
Well there are basically two options.  

1.	Search far and wide for the drivers on the merchant websites.  

2.	 Download software that will find the right drivers and install them all automatically.  

I used to do it on my own until I discovered how easy it was to download drivers with driver update software.
===============
[Link Building Service](http://www.linkbuilderspro.com)
[Internet Web Marketing](http://www.grantcom.us/news/2007/alexa-ranking-importance.htm)

---

### Post by Mark Phelps on 2010-07-24
> **loose111 said:**
> Well there are basically two options.  

1.	Search far and wide for the drivers on the merchant websites.  

2.	 Download software that will find the right drivers and install them all automatically.  

I used to do it on my own until I discovered how easy it was to download drivers with driver update software.
===============
You're talking about MS Windows, right? Because that kind of advice in Ubuntu is just plain crazy!!  

Video drivers are installed automatically by the kernel when the installation is done.  Forcing the installation of other drivers virtually guarantees disaster.

---

