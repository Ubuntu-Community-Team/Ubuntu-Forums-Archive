---
title: "LCD monitor problem !!"
date: 2009-10-15
forum: Multimedia Software
---

### Post by samisomy on 2009-10-15
[SIZE=3][COLOR=Green]Hi,
am a new user on ubuntu have little situation here.

i installed ubuntu 9.0.4 and it installed the driver software for all cards automaticly,
 but I got a problem which is the desktop resolution  is very low and the graphics looks badly.
even i makes comperhensive update to the system the problem still same.

i went to see the hardware i found it istalled correctly which is 

Nvidia geforce fx 5500 
version 173


[COLOR=Blue]but am using WEGASONIC LCD monitor 21 Inch

[/COLOR]i entered the display option from the menu preferences it tells that the monitor is unknown !!!!  :confused:


how to install this monitor to solve the problem please ?????? 

 :sad:[/COLOR][/SIZE]

---

### Post by HappyFeet on 2009-10-15
Do:
```
gksudo nvidia-settings
```
and see if you can change the settings from there.

---

### Post by samisomy on 2009-10-15
thanks for your interest but i cant change the setting or resolution from here also !!!!

---

### Post by samisomy on 2009-10-16
up up up !!!!!

---

### Post by samisomy on 2009-10-18
my friends told me that I'll got the answer for my problem here
but seems to be that I'll go back to windows better

please heeeeeeeeeeeeeeeeelp !!
](*,)

---

### Post by Capt. Blackwood on 2009-10-18
Assuming your drivers are installed and activated. Try to find the "X Server settings control panel"

System -> Administration -> NVIDIA X Server Settings.

Click on X Server Display Configuration. 

I've never had to install a monitor before, to be honest i never knew monitors were installed, just detected. 

try irc.ubuntu.com <<< using your irc client and ask around. 

I'd reccomend #SeaPhor as a channel, we might be able to help.


Perhaps the monitor wasn't detected on install or a manual configuration is required to make the monitor work.

---

### Post by samisomy on 2009-10-19
> **Capt. Blackwood said:**
> Assuming your drivers are installed and activated. Try to find the "X Server settings control panel"

System -> Administration -> NVIDIA X Server Settings.

Click on X Server Display Configuration. 

I've never had to install a monitor before, to be honest i never knew monitors were installed, just detected. 

try irc.ubuntu.com <<< using your irc client and ask around. 

I'd reccomend #SeaPhor as a channel, we might be able to help.


Perhaps the monitor wasn't detected on install or a manual configuration is required to make the monitor work.


[SIZE=3][COLOR=Green]many thanks for you

but I didn't find the #SeaPhor !!!

how to connect on it ?? [/COLOR][/SIZE]

---

