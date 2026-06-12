---
title: "Terratec Cinergy HT Pci (DVB)"
date: 2008-06-16
forum: Multimedia Software
---

### Post by hendricius on 2008-06-16
Hello,

I love Ubuntu with all its unique and amazing features. I got along with it quite well for some time now. However I came across a problem which I am not able to solve just by researching and following guides. I hope you don't mind asking for support.

I have the **Terratec Cinergy HT Pci** card for watching television via DVB. I had no problems with my prior tv card using kaffeine. However kaffeine gives me the message that no dvb drive was found. My old card worked out of the box.

The guide I used for installing my new card:
[http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers](http://linuxtv.org/wiki/index.php/How_to_install_DVB_device_drivers)

my lsmod output:
[http://pastebin.com/m3be94816](http://pastebin.com/m3be94816)

my lspci output:
[http://pastebin.com/m60280bb1](http://pastebin.com/m60280bb1)

ls -l /dev/dvb/ gives me no directory.

Thank you very much for your help! I hope I am not alone with this problem.

---

### Post by steefjeqv on 2008-06-17
Hi,

Try the following command (in terminal) :

sudo modprobe cx88-dvb

Don't restart your computer, just start Kaffeine and hopefully your Digital TV icon will be there.

Greetings,
Steven

---

### Post by hendricius on 2008-06-17
Thanks. I get this error now:

> FATAL: Error inserting cx88_dvb (/lib/modules/2.6.24-19-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): No such device

---

### Post by steefjeqv on 2008-06-17
Hi,

Can you post the output of dmesg ?

Something else you can try :

At startup, when grub appears, select the previous kernel version.

Greetings,
Steven

---

### Post by hendricius on 2008-06-17
> **steefjeqv said:**
> Hi,

Can you post the output of dmesg ?

Something else you can try :

At startup, when grub appears, select the previous kernel version.

Greetings,
Steven

dmesg output:
[http://pastebin.com/m4c965b0e](http://pastebin.com/m4c965b0e)

not sure if that's the complete output as my terminal does not display more.

---

### Post by steefjeqv on 2008-06-17
Hi,

Your card doesn't appear to be recognized by the v4l DVB drivers.

See the lines 310 to 478 of your dmesg output.

This card should work out of the box, but this clearly isn't the case.

The driver module mentioned in your dmesg is the cx88 module, but this should be the saa7134 module according to this info :

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.saa7134")

Try loading this module :

sudo modprobe saa7134

or

sudo modprobe saa7134 card=109

Greetings,
Steven

---

### Post by hendricius on 2008-06-17
Thank you. I loaded both modules without any errors.

However, I am still unable to get the device recognized in Kaffeine. I still get the message: "No DVB-Devices found. The DVB related functions will be hidden." Do I have to restart after loading the modules?

---

### Post by steefjeqv on 2008-06-17
Hi,

Modprobe only works for your current session.
When you reboot, you'll have to reload the driver again.

In order to load the saa7134 driver at boot you need to edit the following file :

sudo gedit /etc/modules
 
At the bottom of this file add :

saa7134-dvb

Save and close. Reboot and check if Kaffeine can detect your card.

If there still is a problem, please post your dmesg output. It may be possible that your tuner isn't detected or that the correct firmware isn't loaded.

Greetings,
Steven

---

### Post by hendricius on 2008-06-17
Yup. Still does not work unfortunately.

Here my dmesg output:
[http://pastebin.com/m92d1c54](http://pastebin.com/m92d1c54)

thank you very much for all the help.

Hendrik

---

### Post by steefjeqv on 2008-06-17
Hi,

Sorry for the confusion, but their appear to be two versions of this card :

One with the saa7134 module, which works. And one with the conexant chipset, which doesn't quite work yet.

Judging by your posts on pastebin, yours is a conexant chipset. 
Just ignore my previous posts concerning saa7134. And remove the module added in your /etc/modules file.

According to this thread : [http://mcentral.de/wiki/index.php5/Terratec_Cinergy_HT_PCI]("http://mcentral.de/wiki/index.php5/Terratec_Cinergy_HT_PCI")
You can try the following command in terminal :

sudo modprobe cx88xx card=58

or

sudo modprobe cx88xx card=61

Greetings,
Steven

---

### Post by hendricius on 2008-06-18
Thank you.

Still does not work :(. Both modules loaded fine. However kaffeine does not recognize the card. I delete the config files every time I try it again to ensure a fresh kaffeine.

my new dmesg output:
[http://pastebin.com/m4275da18](http://pastebin.com/m4275da18)

thank you -

hendrik

---

### Post by steefjeqv on 2008-06-18
Hi,

Well, it seems that the new version of this Terratec card isn't supported yet by the v4l-dvb drivers, not even in their newest version.
I find it a bit confusing that manufacturers just change a product specs, without even mentioning this to the buyer.
You think you buy a TV card fully supported by your Linux system and end up with a totally different (not supported) product.

Anyway, you can try to edit the following file :

sudo gedit /etc/modprobe.d/options

add the following to this file :

options cx88xx card=58

Save and close. Restart your computer.
If this doesn't work then replace card=58 by card=61


Greetings,
Steven

---

### Post by hendricius on 2008-06-18
Thank you very much - unfortunately none gives me better results. It still seems the card is not recognized.

Thanks.

---

### Post by hendricius on 2008-06-21
Nobody knows?

---

### Post by steefjeqv on 2008-06-21
Hi,

I'm afraid there are no drivers available for the moment.

This is the current list of supported cx88xx cards :

[http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.cx88]("http://www.mjmwired.net/kernel/Documentation/video4linux/CARDLIST.cx88")

Some more info on the v4l wiki :

[http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TerraTec]("http://www.linuxtv.org/wiki/index.php/DVB-T_PCI_Cards#TerraTec")

All you can do is wait for the drivers to be included in one of the following driver versions of v4l-dvb (which can take a while). This is their current cardlist :

[http://linuxtv.org/hg/v4l-dvb/file/4012ea1a6a06/linux/Documentation/dvb/cards.txt]("http://linuxtv.org/hg/v4l-dvb/file/4012ea1a6a06/linux/Documentation/dvb/cards.txt")

Greetings,
Steven

---

### Post by hendricius on 2008-06-22
Thank you.

---

### Post by MartinuxP on 2008-08-04
Hi, i've got the same card and... it doesn't work :(

How can i try to install a dev version of v4l2? using svn/git or something similar?

---

