---
title: "Ubuntu can't find my wireless network"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by Beinlaus on 2011-05-20
Hey, I just downloaded Ubuntu 11.04 and dualbooting it with Windows XP. When I go on Ubuntu for some reason it can't find the wireless network in my house (It worked before with an older version of Ubuntu). The wireless network button on my laptop is in the right position, please help me out.

---

### Post by josephmills on 2011-05-20
Hi there could we please get some more info about your computer. Please open up your terminal (ctrl+alt+t)and type in ```
lspci -nn
```  and ```
rfkill list all 
``` please paste here thanks

---

### Post by Beinlaus on 2011-05-20
> **josephmills said:**
> Hi there could we please get some more info about your computer. Please open up your terminal (ctrl+alt+t)and type in ```
lspci -nn
```  and ```
rfkill list all 
``` please paste here thanks
Ehm, I'm not good with computers....

---

### Post by josephmills on 2011-05-20
Ok lets try that again 
1) press ** ctrl + alt + t ** a window should pop up if not try again
2) Once that window or terminal pops up please type in ```
lspci -nn
``` then press enter you should get a list of things do you see it highlight that with your mouse and then right click your mouse and **copy ** it then bring it over here (ubuntuforums) and paste it here (right click on the mouse and select paste)
3) Now Please open your terminal again and now type in ```
rfkill list all 
``` then copy and paste that here also if you run into some troubles just post we are here to help you out :)

---

### Post by Beinlaus on 2011-05-20
> **josephmills said:**
> Ok lets try that again 
1) press ** ctrl + alt + t ** a window should pop up if not try again
2) Once that window or terminal pops up please type in ```
lspci -nn
``` then press enter you should get a list of things do you see it highlight that with your mouse and then right click your mouse and **copy ** it then bring it over here (ubuntuforums) and paste it here (right click on the mouse and select paste)
3) Now Please open your terminal again and now type in ```
rfkill list all 
``` then copy and paste that here also if you run into some troubles just post we are here to help you out :)

rfkill sounds scary! does it destroy something?

---

### Post by josephmills on 2011-05-20
No But I am glad that you asked please never put anything into your terminal that you do not know what it is ask the person if they do not give you an answer then do not do it.,  rf stands for radio frequency and list all means list all radio frequency 

this is what it should look like 
```
$ rfkill list all 
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```


see it tells us if there is something blocking it from working here is some more about rfkill [http://wireless.kernel.org/en/users/Documentation/rfkill](http://wireless.kernel.org/en/users/Documentation/rfkill)

---

### Post by Beinlaus on 2011-05-21
I didn't get the first command to work, but I did the other one and it said:
0:dell-wifi: Wireless LAN
Soft blocked: no
Hard blocker: no
1:Phy0: Wireless Lan
Soft blocked: no
Hard blocked: no

What do I do?

---

### Post by josephmills on 2011-05-21
open your terminal and type in ```
lspci -nn
``` what is lspci well **ls** stands for list and **pci **stands for pci cards in the computer **-nn** means model # or serial or something like that 
ls-->+<--pci -nn = list all pci card in the computer with there model number or serial number 
so you see once we all get to see your pci cards we will know what kind of wireless card you have and also the model # kinda like a car lot lol (make and model )

---

### Post by Beinlaus on 2011-05-21
Am I supposed to copy all of the information that was on the first one? (What kind of information is it?)
It was an awful lot of text...

---

