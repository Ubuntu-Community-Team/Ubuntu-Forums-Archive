---
title: "New to ubuntu - want to install on Samsung N250 Netbook"
date: 2011-06-28
forum: Networking &amp; Wireless
---

### Post by TrafficPilot on 2011-06-28
Hello everyone

Firstly I am a TOTAL ubuntu and Linux newbie so please be gentle...am currently using Windows 7 across my networked PCs at home.

I've just received my new Samsung N250 Plus Netbook which comes with Windows 7 Starter (yuk). I read a post on Ebuyer from someone who has installed ubuntu on his N250 so thought I'd give it a go tonight.

My main concern is whether my wi-fi card (Broadcom 802.11n according to windows) will work when I remove windows and install ubuntu. I intend to use the netbook for internet use only while working abroad.

Is it possible to test it works by running ubuntu from my USB stick first (without removing windows 7)?

Your thoughts (and any relevent links) would be appreciated. I did run a search on the forum earlier but there is so much info I am lost..

Thanks

Adam

---

### Post by georgelab on 2011-06-28
I suggest you to make a bootable USB stick with Ubuntu 11.04. It's quite simple to do, you can use a live CD on your main computer to run Ubuntu and then make the bootable USB stick from it.

Your wireless card is supported and will work fine after installing the OS.

Best regards!

---

### Post by e79 on 2011-06-28
+1 for testing it with a bootable USB stick.

From your Windows machines, visit Pendrive Linux and follow the instruction (pretty easy).

[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Hope this helps

---

### Post by dFlyer on 2011-06-28
Download the Ubuntu live desktop iso and burn it to cd/dvd or usb. When you download the iso before you burn the image please make sure you have checked the MD5SUM against the checksum file provided from the web site you downloaded the image. If your using windows you will have to search the internet for a program called md5sum.exe and download that first. To check the md5sum for a command line enter the following command where you downloaded both the image (iso) and md5sum.exe to:

md5sum.exe "Name of image file.iso" with out the quotes.

Once you are sure that the checksums match you can proceed with creating a cd/dvd or usb live cd.

Once the burn is complete, my advice is to test drive the cd/dvd or usb to be sure everything works before you choose to install. If everything is working great that the next step is to clone or backup any important data you have on your computer. A clone is better as it will be easier to restore should something go wrong.

Your next step is to decide how you want to install, for a new linux user I recommend a dual boot system where windows is on one partition and linux is on another, but than again that choice is your.

I usually warn everyone to go slow, have fun and ask questions when and if problem pop us. When you as a question include as much information as possible about your hardware, software and error messages and someone will jump in and work you through the problem. Just remember that Linux is not Windows and don't expect it to act or run like windows. I find Linux very stable and have been using it since the mid 90's. Ubuntu is a great distro of Linux and to is very stable.

---

### Post by TrafficPilot on 2011-06-28
Thanks for all your replies! I'll investigate and try these tonight.

---

### Post by TrafficPilot on 2011-06-29
I've installed ubuntu with Windows 7 (dual boot) on my laptop reasonably successfully:)

Couple of issues I have if anyone can suggest a fix..

1: The screen is way too dark and I can't seem to adjust the brightness (this isn't an issue in Windows 7)

2: ubuntu cannot see any wireless networks - they are greyed out. It worked last night at home fine so not sure why it doesn't work today - I haven't changed anything. Windows works fine using wi-fi here at my office.

Any ideas?

Thanks again,

Adam

---

### Post by e79 on 2011-06-29
> I've installed ubuntu with Windows 7 (dual boot) on my laptop reasonably successfully:smile:Congratulations and welcome to freedom ! :popcorn: 

> 1: The screen is way too dark and I can't seem to adjust the brightness (this isn't an issue in Windows 7)On your netbook, see if you can press the Function key (FN) and F5 to decrease / F6 to increase the brightness; or go to System --> Preferences --> Power Management  and adjust the brightness from there.

> 2: ubuntu cannot see any wireless networks - they are greyed out. **It  worked last night at home fine** so not sure why it doesn't work today - I  haven't changed anything. Windows works fine using wi-fi here at my  office.
Are you sure your wireless card isn't turned off for some reason; or that the 'Enable Wireless' isn't ticked when left-clicking your network connexion ?

---

