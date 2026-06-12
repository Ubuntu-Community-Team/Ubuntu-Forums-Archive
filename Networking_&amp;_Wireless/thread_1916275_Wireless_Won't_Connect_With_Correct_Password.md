---
title: "Wireless Won't Connect With Correct Password"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by JosephBeck on 2012-01-27
Title says it. I installed Ubuntu 11.10 last night and deleted the Windows XP I originally had on here. I didn't want to make my netbook a dual boot. Now even with the correct password it keeps asking for it to connect to wifi, I have yet to connect even once. For hours I've been trying different solutions and I can't seem to fix it....I'm ready to just delete Ubuntu all together and reinstall XP if this keeps up, its literally been nearly 5 hours. 

Tell me what I need to put in the terminal to post here and I will. I want this fixed so badly because I love how Ubuntu 11.10 is, just won't connect to the damn wifi. This is the first time I've ever used Ubuntu before. I installed it on my HP Mini 210 Netbook.

---

### Post by jwbrase on 2012-01-27
Have you made sure the security type is set to the same thing the router you're trying to connect to is using? (WEP, WPA, etc.)

---

### Post by JosephBeck on 2012-01-27
> **jwbrase said:**
> Have you made sure the security type is set to the same thing the router you're trying to connect to is using? (WEP, WPA, etc.)

Yes sir, I use WPA2. I've tried everything from removing the kernel method to editing the blacklist x-x.

---

### Post by JosephBeck on 2012-01-27
Could use some assistance, it is very important that I get my netbook connected to WiFi. I am going try to installing Ubuntu 11.10 over again but I am doubting it is going to work from what I've seen from others.

---

### Post by Optico89 on 2012-01-28
I too have been dealing with this issue, but for the past five days!! 

It appears Ive installed my AWUS036NHR Alfa USB wireless card drivers
Correctly.

Help would most definitely be appreciated!
I hang at obtaining ip, and the it drops me...

---

### Post by kalimojo on 2012-01-28
im having the same problems with my wifi

---

### Post by 23senick on 2012-01-28
Always helpful if you can post the type of hardware you have. Open terminal and type 
lspci

usually with these issues there seems to be hardware or driver specific problem.

---

### Post by JosephBeck on 2012-01-28
I have an Atheros AR9285. I found a solution that may help everyone that can't seem to get any other situation to work. Before you do anything at all in technical terms, reset your wifi. That is a pain I know but reset it with the name and password (You can keep it the same). I think for people with WPA2 like I have theres an issue with Ubuntu's network manager connecting to it as Ubuntu has the whole WPA/WPA2 set up not setting them as individual ones. I reset it and set it to WPA2 again and rebooted with the terminal and fixed it. If it doesn't work try downgrading to normal WPA when you reset your wifi. I hope this helps everyone who followed all other solutions and got nowhere.


It should work if you had the problem like me where it kept asking for the password even if you were using the correct one. If you have problems with none of your wireless connections showing up at all it most likely will be a driver issue and resetting your wifi won't help.

---

### Post by bkratz on 2012-01-28
> **JosephBeck said:**
> I have an Atheros AR9285. I found a solution that may help everyone that can't seem to get any other situation to work. Before you do anything at all in technical terms, reset your wifi. That is a pain I know but reset it with the name and password (You can keep it the same). I think for people with WPA2 like I have theres an issue with Ubuntu's network manager connecting to it as Ubuntu has the whole WPA/WPA2 set up not setting them as individual ones. I reset it and set it to WPA2 again and rebooted with the terminal and fixed it. If it doesn't work try downgrading to normal WPA when you reset your wifi. I hope this helps everyone who followed all other solutions and got nowhere.


It should work if you had the problem like me where it kept asking for the password even if you were using the correct one. If you have problems with none of your wireless connections showing up at all it most likely will be a driver issue and resetting your wifi won't help.

I use wpa2 with no problems--just make sure the router is set to either wpa or wpa2--not mixed mode (it does cause problems)

---

### Post by coilwinder on 2012-11-22
> **bkratz said:**
> I use wpa2 with no problems--just make sure the router is set to either wpa or wpa2--not mixed mode (it does cause problems)

THANK YOU!

I know it's kind of an old thread, but some old threads are gold! That fixed my puzzling network un-connectivity for one of my Ubuntu netbooks. Just setting the router to WPA2 only (and not mixed mode) solved it.


EDIT: To elaborate:

I have two similar netbooks, both using Ubuntu 10.04 LTS (but different versions, haven't updated in a while). Information I was able to retrieve about the wireless and system is stated below. I don't know if this is useful for anyone, but there is is. I used the commands "lspci" to get wireless NIC adapter name and "nm-tool" to get the name of the driver it used (I'm no expert really, just FYI and just in case).


The Ubuntu netbook that worked with mixed mode wireless security (or "Auto WPA or WPA2"), was:

[LIST]
[*] Acer Aspire One (slow 8GB SSD version, 1 GB RAM), running Ubuntu 10.04 LTS, Kernel Linux 2.6.32-23-generic, GNOME 2.30.2
[*] Wireless network card: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
[*] Driver: ath5k
[/LIST]
 
The netbook that did not work with mixed mode wireless security:

[LIST]
[*] EEE PC 1000HE, running Ubuntu 10.04 LTS, Kernel Linux 2.6.32-34-generic, GNOME 2.30.2
[*] Wireless network card: Atheros Communications Atheros AR8121/AR8113/AR8114 PCI-E Ethernet Controller (rev b0)
[*] Driver: rt2860
[/LIST]

---

