---
title: "Belkin n150 won't work"
date: 2011-07-27
forum: Networking &amp; Wireless
---

### Post by gsm54321 on 2011-07-27
I have a belkin n150 usb wireless adapter that doesn't seem to work. I have searched for a solution on this and other forums, but the advice is either too confusing/long for my noob brain, or applies to older versions and no longer works.

I am running ubuntu 11.04, the usb device shows up on lsusb so I know it's there, but I can't get it to work. I have installed ndiswrapper and put in the driver from the cd, didn't work. I downloaded the RT2870 linux drivers, tried sudo make and sudo make install and that didn't work (I probably didn't install correctly).

Can anyone help me out? or at the least point me to a usb adapter that works for under $50 and can be bought at Best Buy?

---

### Post by wildmanne39 on 2011-07-28
Hi, run these commands in a terminal please
```
lsusb
```
```
sudo lshw -C network
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
and post the outcome here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by bkratz on 2011-07-28
> **gsm54321 said:**
> I have a belkin n150 usb wireless adapter that doesn't seem to work. I have searched for a solution on this and other forums, but the advice is either too confusing/long for my noob brain, or applies to older versions and no longer works.

I am running ubuntu 11.04, the usb device shows up on lsusb so I know it's there, but I can't get it to work. I have installed ndiswrapper and put in the driver from the cd, didn't work. I downloaded the RT2870 linux drivers, tried sudo make and sudo make install and that didn't work (I probably didn't install correctly).

Can anyone help me out? or at the least point me to a usb adapter that works for under $50 and can be bought at Best Buy?



here is a pretty good thread about your device, especially look at post 15 for complete directions.

[http://ubuntuforums.org/showthread.php?t=1482382&page=2](http://ubuntuforums.org/showthread.php?t=1482382&page=2)

---

### Post by gsm54321 on 2011-07-28
@bkratz, I tried that, no luck. Thanks for the advice

@wildmanne39, I no longer have the belkin. On my way home from work I stopped by best buy and got a netgear n-150, model number wna1100. At first it didn't work, but a full reinstall got it going.

Thanks for your help.

---

### Post by wildmanne39 on 2011-07-28
Hi, I am glad you got one that works for you, we could have got the belkin working I believe. 
Enjoy

---

