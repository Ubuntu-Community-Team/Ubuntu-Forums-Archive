---
title: "TV Tuner remote control"
date: 2005-12-14
forum: Multimedia &amp; Video
---

### Post by vlatkop on 2005-12-14
Hello to everyone.
I have TV card with these specifications:
Vendor: Philips Semiconductors
Device: SAA7130 Video Broadcast Decoder
I didn't have to do anything about configuring module for this card (it was all automatic :)) Right now I use module driver saa7134. I have tryed TV and Radio and it was all OK. But when I tryed is the remote controler works... It works but only the buttons: from 0 to 9, shutdown, mute, ent, volume up and volume down. The other buttons are not working. So I have some question about my problem. At first i was thinkinig to install and configure lirc but then I decided to find where is configuration file for the TV Tuner and the Remote Controler and just put the other buttons there. But I don't know where to look. Can I make my idea works? Or I will have to install lirc. Also I have read that the XFree86 can be configured to recognise the remote keys  by using kbd driver and xkb options. But I don't know if this is possible in xorg and simply I don't know how to do that. At first I thougt that there are allready defined some devices in /etc/X11/xorg.conf for controlling  remote controler but there isn't. Who controls now the remote controler? The module saa7134?
Thanks in advance

---

### Post by medya on 2005-12-15
[QUOTE=vlatkop]Hello to everyone.
I have TV card with these specifications:
Vendor: Philips Semiconductors
Device: SAA7130 Video Broadcast Decoder
[/QUOTE]


Hey I dont know if it is the right place to ask my question , I have the same TV TUNER card,  I am a VERY VERY NEW to linux, I just runned ubuntu linux once..

please tell me how I can watch tv, 

-how did you install your card in ubuntu? 
-do I need to download any program to surf tv ? if yes, what , where , is it free?

---

### Post by vlatkop on 2005-12-15
[QUOTE=medya]please tell me how I can watch tv,[/QUOTE] 

OK. I will try on short to answer some of your questions. If you wanna watch TV you must first install some tv program, like tvtime, kdetv, zapping and others. You can go on google and search there for extra programs or you can do that by searching in Synaptic Package Manager the keywords "TV" or using apt-get.

[QUOTE=medya]-how did you install your card in ubuntu? 
-do I need to download any program to surf tv ? if yes, what , where , is it free?[/QUOTE]

I didn't had to do anything in the field of installing my card, because the Ubuntu have done that automaticly. If you are using 2.6.x kernel I think that the module is allready in the kernel and allready loaded, so you don't have to do anything on the field of installing module for this card. You can check if the module is loaded by using: lsmod | grep saa7134. And if you have any result after this command you have, for sure, loaded module. If not, find it in /lib/modules/2.6.XXX/kernel/drivers/media/video/saa7134 or by using locate saa7134 and then go in the working directory and load the module by: insmod saa7134. After you have successfuly loaded the module, install TV program and check what you have done.
Regards.

---

