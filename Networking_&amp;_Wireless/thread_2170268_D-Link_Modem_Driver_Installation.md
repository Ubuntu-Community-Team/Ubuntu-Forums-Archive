---
title: "D-Link Modem Driver Installation"
date: 2013-08-25
forum: Networking &amp; Wireless
---

### Post by jithinjohnygeorge on 2013-08-25
Hi,

I am using ubuntu 12.04 [ 32 bit ] . When i connected my d-link datacard[model number DVM-156], it doesn't seem to detected. I understands that the modem driver is not installed. How can i install that driver.
 
Please help me. Thanks in advance :)

---

### Post by wildmanne39 on 2013-08-25
Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security,  then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

---

### Post by Cheesemill on 2013-08-25
*Thread moved to **Networking & Wireless**.*

---

### Post by jithinjohnygeorge on 2013-08-26
> **Wild Man said:**
> Hi, copy and paste this command in the terminal (ctrl+alt+t) please:
```
 wget -N -t 5 -T 10 http://dl.dropbox.com/u/57264241/wireless_script && chmod +x wireless_script && ./wireless_script
```
It will download a script and create a file named (wireless-info.txt, or wireless-info.txt.tar.gz) in your home folder with wireless information so we can see the condition of your wireless at this time and the Mac address, WPA key and WEP key are removed for your security, then reply back, click on the paper clip and attach the wireless-info.tar.gz file as a zip file. 

If you do not have ethernet either then follow the directions at this link for running the script without internet.
[http://ubuntuforums.org/showpost.php?p=12350385](http://ubuntuforums.org/showpost.php?p=12350385)
Thanks

done, the wireless-info.txt is attached with this comment 

[ATTACH]245719[/ATTACH]

---

### Post by wildmanne39 on 2013-08-26
It says it is hardblocked that usually means the physical switch is off, you need to turn it on either by sliding or pressing the switch or there is a key combination that turns it on like fn + f5 you may have to refer to your documentation to see how to turn it on.

---

### Post by jithinjohnygeorge on 2013-08-26
It's actually a usb modem, works fine with windows, i can not find any hardware lock for my device :(

---

### Post by wildmanne39 on 2013-08-26
You also have > 02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: brcmsmacit is blocked so that means your usb adaptor is blocked.

The usb adaptor needs usb-modeswitch, did you install it?
Is there any reason not to use the internal card?
Thanks

---

### Post by jithinjohnygeorge on 2013-08-27
> **Wild Man said:**
> You also have it is blocked so that means your usb adaptor is blocked.

The usb adaptor needs usb-modeswitch, did you install it?
Is there any reason not to use the internal card?
Thanks


am not talking about that one. 

The issue is with my usb modem

**Bus 001 Device 004: ID 2001:7d00 D-Link Corp. **

---

### Post by jithinjohnygeorge on 2013-08-29
somebody please help me :KS

---

### Post by wildmanne39 on 2013-08-29
In post 7 I asked > The usb adaptor needs usb-modeswitch, did you install it?
Is there any reason not to use the internal card?
it is blocked so that means your usb adaptor is blocked.I have been waiting for you to answer those  questions.
Thanks

---

