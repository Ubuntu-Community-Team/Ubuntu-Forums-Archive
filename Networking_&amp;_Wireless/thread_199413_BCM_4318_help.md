---
title: "BCM 4318 help"
date: 2006-06-18
forum: Networking &amp; Wireless
---

### Post by mshen10 on 2006-06-18
Hey guys, Im new to Linux. I figure I should try ubuntu, I heard it was easy to setup and use. I like it so far, but I can't seem to get my wireless card to work. Ubuntu does see my card, but it's not sending or receiving packets. I got a Broadcom Corporation BCM 4318 [AirForce One 54g] 802.11g Wireless Lan Controller. I've tried fooling around with it. Now when i start up my Laptop my lan card is activate, but it's not sending or receiving packets. I have to restart it using the command line. 

Could someone please help me

Oh ya, before i started to fool around with the setting. My laptop was reading my, said it was present.

---

### Post by evilghost on 2006-06-18
I've got a BCM4306 WLAN card as well in my laptop.  What I did was to add bcm43xx to /etc/modprobe.d/blacklist and then install and use ndiswrapper.  AFAIK, Others were able to use the native bcm43xx kernel driver however I believe that the fwcutter firmware is required before it will function, I opted for ndiswrapper.

---

### Post by naught101 on 2006-06-18
this might help. I got my dell d410 working with BCM43xx drivers. that's probably preferable, if you can, since they are native. the best thing to do is run 
> lspci
then find your card, and check the number before it, then run
> lspci -n
and get the number like: XXXX:XXXX. that's your vendor ID, and Product ID. compare that to the BCM43xx list at [http://bcm43xx.berlios.de/?go=Devices](http://bcm43xx.berlios.de/?go=Devices) . or, if you're sure of the card type, just check the name on that list. mine seems to work, even though the vendor ID isn't the same (and it's actually a 4320... oh well, it works).

download your driver, install bcm43xx-fwcutter, then follow the instructions here: [https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-1bf745937b6de8a643a08da9e8001632ba459ac6](https://wiki.ubuntu.com/WifiDocs/Driver/bcm43xx?action=show&redirect=WifiDocs%2FDriver%2FBroadcom43xx#head-1bf745937b6de8a643a08da9e8001632ba459ac6) (from 1.2.2. Obtaining the Firmware down)

if that doesn't work, try checking your card against the list at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) and follow the install instructions for ndiswrapper at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
you may need to blacklist your bcm43xx driver,
> echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
and reboot, to avoid conflicts.

---

### Post by trubblemaker on 2006-06-18
yeah figure out which driver you want to run, if you do decide to use ndiswrapper try using the script from my signature, it's supposedly idiotically easy. 
Remeber that one day the native driver will be faster than ndiswrapper.

---

### Post by mshen10 on 2006-06-19
ok. I already have the ndiswrapper installed. Should I uninstall and reinstall? I also have network manager installed too.  Should I just get rid of that? By the way, my laptop is a inspiron b130. Can someone also tell me why my lan doesn't work on start up

---

### Post by trubblemaker on 2006-06-19
depends, if you can see networks with 
```
iwlist scan
```
or get connected to the internet I wouldn't re-instal, if it's simply a matter of getting connected at boot then I would use
```
ndiswrapper -m
```
which should gett it working on boot.

if you aren't getting connected to the net or you aren't getting your interface light to light up, then try uninstalling and following one of the howto's or the script, the howto below tells you howto uninstall properly so that you don't have to worry about past installation of ndiswrapper messing you up.

---

### Post by mshen10 on 2006-06-21
oh ok. i'll see how it goes. I may just end up uninstalling ubuntu and reinstalling for the default settings.

---

