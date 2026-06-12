---
title: "Pavillion Dv2 Wifi Problem using flash drive"
date: 2011-04-12
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-04-12
i've installed a fresh ubuntu os on flash drive and trying to get the wifi on it too work. the wifi has worked on this laptop before when the hard drive was in it but it went out and has been removed from the laptop its just using a sandisk flash drive with ubuntu installed on it. its not a live os. it is installed. wired connection works fine. i have installed both sta and the b43 drivers and it didnt work. their is a hardware switch on this laptop and i have tried it over and over but no networks ever show up. when the switch is off or on of course no networks pull up with either drivers installed. anyone have an idea?

---

### Post by josephmills on 2011-04-12
please post ```
lspci
``` thanks

---

### Post by slixz85 on 2011-04-12
> **josephmills said:**
> please post ```
lspci
``` thanks

01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
02:00.0 Network controller: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

---

### Post by josephmills on 2011-04-12
please post ```
 iwconfig 
``` ```
rfkill list
```

---

### Post by slixz85 on 2011-04-13
i just tried linux mint and still same issue unfortunately the commands arent recognized. im pretty new to linux and just know my way around terminal a bit and such.

the internet speed is really slow also just thinking maybe thats because im downloading all this data to a flash drive instead of hard drive obviously. it only get 200-300kb download speed normally and should be 3MB or so

thanks to any help

---

### Post by slixz85 on 2011-04-14
anybody got an idea. already tried couple other os's on the flash drive also no luck

---

### Post by josephmills on 2011-04-14
I am new to this also but could you please post ```
lspci -vnn | grep 14e4 
``` ps go back to ubuntu (save headaches )

---

### Post by josephmills on 2011-04-14
I would also like to say that the flash drive has nothing to do your drivers it is because they are proprietary and that is why you are having troubles please read this [http://www.ubuntu.com/project/about-ubuntu/our-philosophy](http://www.ubuntu.com/project/about-ubuntu/our-philosophy) Thanks again but please so step #7 and we will get you up and going once again thanks

---

### Post by slixz85 on 2011-04-14
thanks i will try this again as soon as i can. i have already tried the b43 and sta drivers for my card it says to use.


broadcom bcm4322 802.11a/b/g/n wireless lan controller     (14e4:432b) <not sure what that is but was in text also


this is funny now too unfortunately just trying a couple os's being new to linux i thought was the solution maybe. i have puppy linux now on my usb drive and its the only os i have right now. definitely going to go back to ubuntu because your right, less headaches. the problem now is, i need to figure out how to get unetbootin or something similar with puppy linux. i just dont know what type of files to try and get or a way to get them. someone just suggested puppy linux and said it had good wifi driver support, but now stuck with it for this time being.

even running into mount problems because at first i was going to install this one to another usb drive just to have for another backup since i got this problem now

need to get back to ubuntu permanantely. too many linuxs out there had to try em. but yeah tired of this crap. lol

---

### Post by josephmills on 2011-04-14
hi there again, please take a look at this [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)  you will see that you card is partially in 2.6.39+ so there are work arounds

---

### Post by slixz85 on 2011-04-14
good news then thanks. i was affraid would have to buy a new wifi card but this one has worked with windows vista. i tried to use that ndiswrapper program or whatever for windows drivers but it wants a .inf file and only drivers i can find are .exe


now if i can just find some software for this damn puppy thing to burn iso of ubuntu back to the usb to RETURN and STAY. i just thought it was cool seein all the different desktops and linuxs but i see now that i should go with something more widespread for support. have been using and know about ubuntu for year or so so i aint very good with knowing all the commands to make the work easier

---

