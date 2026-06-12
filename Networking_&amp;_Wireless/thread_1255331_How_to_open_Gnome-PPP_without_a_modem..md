---
title: "How to open Gnome-PPP without a modem."
date: 2009-09-01
forum: Networking &amp; Wireless
---

### Post by etienne@Rofti on 2009-09-01
Hi there!

I would like to open Gnome-PPP, but I do not have a modem attached and thus it seems to not want to open.

If I run the command "gnome-ppp" then I get the following result:
```
WVCONF: /home/etienne/.wvdial.conf
Segmentation fault
```
If I run the command "wvdial" then I get the following result:
```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
```
I am not attempting to connect to the internet via dial-up. I am attempting to set up my computer to connect to the internet through my mobile phone over bluetooth in emergencies. I have a how-to already, but step 1 is to open up Gnome-PPP.

Any help would be greatly appreciated
Thanks!

---

### Post by GeorgeVita on 2009-09-01
Hi **etienne@Rofti**. I  am not sure if I can help but I think some more data would help readers of your thread to give you ideas:

1. point us to the HowTo you are trying. Maybe we can bypass or use alternative of Gnome-PPP as this is an error:> ... If I run the command "gnome-ppp" then I get the following result:```
WVCONF: /home/etienne/.wvdial.conf
Segmentation fault
```
2. The output of wvdial is not an error as you did not manage to configure it yet: > If I run the command "wvdial" then I get the following result:```
--> WvDial: Internet dialer version 1.60
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
--> Cannot open /dev/modem: No such file or directory
```
3. Test if system can find the com-port of your modem and post here the output: ```
sudo wvdialconf 
```
4. If you are going to use a specific model of GSM phone, supply more info.
5. How did you install wvdial, Gnome-PPP, etc? 
 
Regards,
George

---

