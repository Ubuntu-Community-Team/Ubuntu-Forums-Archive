---
title: "ATI TV Wonder not loading for MythTV"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by jrshelby on 2007-11-07
Hi guys -

I'm trying to install a new TV tuner card - an ATI TV Wonder HD 600 - one of ATI's HDTV tuners - ultimately for use with MythTV. However, I have not managed to get this thing to be recognized by Ubuntu. I have followed these instructions through the Ubuntu How-to here:

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-ad99fc4a0037a37c20a95c85bf8580305a2af85b](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#head-ad99fc4a0037a37c20a95c85bf8580305a2af85b)

      Download this script: get_dvb_firmware
            $ chmod +x get_dvb_firmware
            $ ./get_dvb_firmware nxt2004
            $ sudo cp dvb-fe-nxt2004.fw /lib/firmware
            $ sudo modprobe cx88-dvb
            $ sudo sh -c "echo "cx88-dvb" >> /etc/modules"

But when I run "sudo cp dvb-fe-nxt2004.fw /lib/firmware" I get:
jrshelby@Lucifer:/dev$ sudo modprobe cx88-dvb 
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.22-14-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

After this process, dmesg gives me:
[83403.477383] cx2388x dvb driver version 0.0.6 loaded
[83403.477391] cx8802_register_driver() ->registering driver type=dvb access=shared

But no specific mention of the ATI card. lspci can see the card, but does not know what it is:
02:01.0 Multimedia controller: ATI Technologies Inc Unknown device ac00

And here I thought that this card was one of the ones that was supported right out of the box.... Anyone have an idea for some way I could begin to tackle this?

Thanks in advance!
--John

---

### Post by jrshelby on 2007-11-08
After some pretty serious messing around with this thing, I'm beginning to think I'm going to attempt to return it for Fry's and get one of the Hauppauge ones. I believe that the firmware is not loading here...  but I have no idea why. Perhaps I am misunderstanding the instructions and this card is not the "HDTV Wonder" but instead something unsupported?

---

### Post by luisito on 2007-11-13
I have the (slightly modified) ATI HDTV Wonder card that comes with the hp z555. It seems to work just out of the box in feisty. I've never used it, but if I run mplayer /dev/video0 I can see the video coming from the card (which is all static noise at the moment since there is nothing connected).

---

### Post by Devastator9 on 2007-11-21
I just downloaded the scrip now what do I do. I click on it and nothing.

---

### Post by jordanubun on 2008-02-02
i am having a simular problem with my kworld 115 card it works in m player with audio but does not give audio in myth also i want it work with astc i have gotten that side to work in mce on my vista boot but it cant get any signal in myth even when i run the scan it says i have a signal but gives me no ginal for all chanels

---

### Post by superfan99 on 2008-04-09
I have same exact problem.  Anyone have any thoughts?

---

### Post by Dashman403 on 2008-05-11
Has anyone tried the bttv drivers?  This is supposed to support the ATI Wonder cards.
[URL="http://linux.bytesex.org/v4l2/bttv.html"]
http://linux.bytesex.org/v4l2/bttv.html[/URL]

---

