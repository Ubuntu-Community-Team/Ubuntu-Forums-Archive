---
title: "No wireless connections show"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by faydub on 2010-03-18
Hey all,
 
installed Ubuntu 9.10 Karmic a few hours ago. This my 1st time using any sort of Linux based system (decided to try it out cause I'm learning about it in college)
 
Anyway, When I first tried to connect to a wireless network everything seemed fine.
I could see all the wireless networks around me, selected my one entered the security key but the icon just kept going around in circles and wouldnt connect.i
 
I researched it and saw thati had to install all the ndisgtk stuff.
 
So i installed ndiswrapper-common, ndiswrapper-utils-1.9 and ndisgtk. Installed the .inf file for my Belkin adapter
 
Then I went to reconnect to the network but found all the networks that were therewere gone.
 
Before the ndisgtk installation the blue light on my belkin adapter was on constantly but now its off.
 
Ive looked around but cant find a solution.
 
Anyones help would be greatly aprecciated.
 
(By the way im using the Belkin N wireless adapter F5803ea or something like that)
 
Thanks

---

### Post by 2hot6ft2 on 2010-03-18
So I take it this is a usb adapter?
Maybe a F5D8053?
Open a terminal
Applications > Accessories > Terminal
and run
```
lsusb
```
That's LSUSB in lower case, and post the results.
So we can see what adapter you have

---

### Post by faydub on 2010-03-19
oh nevermind i turnedthe computer on tismorning and it worked straight away.
 
Sorry for the waste of time and thread space

---

