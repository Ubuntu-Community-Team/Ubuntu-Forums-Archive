---
title: "Connecting via Wireless Notebook WCP54G V5"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by ruthcarroll on 2011-01-03
**Connecting via Wireless Notebook WCP54G V5** 			
 			 			 		   		 		 		Hi everyone.  im new here, this is my first post. always have been a windows user and  my brother decided to install Ubuntu 10.10 on my laptop, before he  completed the full installation so i could use my wireless card, he fell  out with me so now i am a little stuck!
i have been reading various posts for the last two days and i am none  the wiser.  I have a linksys wireless G notebook WPC54G Ver.5.
i really need a step by step (idiots guide) on what to do and how to do it. PLEASE!!!
I have the software (drivers) for the card saved on my machine and have also installed NDISWRAPPER? i think,
i am normally quite good with computers but io am dumb founded with this  system. Please help me before i i give up and reinstall windows! 
thanks:confused:
PLEASE REMEMBER I AM AN ABSOLUTE BEGINNER SO ANY HELP WOULD NEED TO BE IN IDIOT TYPE STEPS! Thank you ):P

---

### Post by chili555 on 2011-01-03
Ndiswrapper, the system to utilize the Windows driver in Linux, has a graphical front-end. Do you have System > Administration > Windows Wireless Drivers? If so, please open it and point it to the location of the .inf file you have saved. I believe the correct file is called lsmvnds.inf. The Windows Wireless Drivers utility should do all the work for you. You can check its progress by opening Applications > Accessories > Terminal and doing:```
ndiswrapper -l
```That's lower case L for 'list.' If everything is correctly installed, you should see something like:> Installed ndis drivers:
  lsmvdns: driver present, hardware presentPost back and let us hear your progress.

---

### Post by ruthcarroll on 2011-01-03
i dont seem to have windows wireless drivers option?

---

### Post by chili555 on 2011-01-03
Let's do it the old-fashioned geek way. First you need to know the location where you have the Windows .inf file. Is it on your desktop? Open Applications > Accessories > Terminal and do:```
cd Desktop/windowsfolder
```Obviously, substitute the actual location containing the .inf file.```
sudo ndiswrapper -i lsmvnds.inf
sudo depmod -a
sudo modprobe ndiswrapper
ndiswrapper -l
```Is the driver installed? When you click the Network Manager icon, do you see your network? Can you connect?

---

