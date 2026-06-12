---
title: "Ettercap dns_spoof cannot work anymore"
date: 2011-07-05
forum: Networking &amp; Wireless
---

### Post by Mels on 2011-07-05
Hi everyone! I 've been reading the forum for a long time, but I registered just today because I could not find solution to my problem. I have been working for my university's last year project for graduating. My project is a Wireless phishing attack. I failed to make a fake AP with aircrack-ng suite both in BT4 and Ubuntu so I tried to make a mitm attack with ettercap. I use an Ubuntu 10.04 live distribution with a USB stick.

The happy part :P :
After some effort, I could redirect (with the use of dns_spoof plug-in) the original Facebook website to my Ubuntu laptop's localhost fake login page (using XAMPP server). The attack was successful against my iPhone, my Nokia phone and against 2 PCs running Wndows XP and Vista. Ettercap's output when faking facebook in a remote host (like my iPhone) was:
```
dns_spoof: [facebook.com] spoofed to [192.168.1.66]
```The router used was Thomson TG585v7.

The sad part :( :
Yesterday the professor and his assistant contacted me to demonstrate the attack today. So last night I decided to do the attack one more time just to be sure. I used my girlfriends laptop and had to install some new drivers for her wifi card, as it was not Ubuntu ready like mine (I don't think that I need for ettercap some special card with monitoring, etc like for aircrack). I tried the attack again to the previously used wifi router (TG585v7) but I realised that for some reason I did not have connectivity to Internet (with neither of my PCs nor my smartphones). Note that the wifi router is not mine, it is some neighbor's unlocked router. I used the attacks (they are IP driven) strictly to my devices only (my PCs and my phones). So I decided to unlock my wifi router (TG585**v8**) and place the attack there. Ettercap could not spoof so I formated my usb stick and reinstalled all the useful tools. I returned to the original attacker laptop, but I was unlucky again. So I tried to attack my phone through the previous wifi router. After a lot of time, I finally got it working but, as stated above there was no Internet access, so the only working site was the fake Facebook. Even that was extremely slow and sometimes could not fully load.
Note that before finally getting to work Ettercap (the first time, when it was perfectly working) I was experimenting with aircrack and editing files and installing programs just to get aircrack work. Anyway, I don't think that it has anything to do with it, but I am stating that just in case.

So now I don't know if it is the router's fault or something else. The absence of Internet access to the router that I made the attack successful is pulling me down from having a clear view of the case. Do you have any solutions or suggestions?
I used chk_poison with my router too, and all i got was outputs like this:
```
chk_poison: No poisoning between 192.168.1.65 -> 192.168.1.254
```The gateway is 192.168.1.254. The demonstration will take place in my University with the labs' WAN (I don't know what's the labs' wifi router).

Sorry for my english, looking forward to a solution!
Thanks in advance!!!

---

