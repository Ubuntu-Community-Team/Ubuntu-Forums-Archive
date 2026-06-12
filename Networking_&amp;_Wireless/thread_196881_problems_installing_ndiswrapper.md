---
title: "problems installing ndiswrapper"
date: 2006-06-14
forum: Networking &amp; Wireless
---

### Post by maniacmusician on 2006-06-14
hey; as you can see i'm running xubuntu and trying to install ndiswrapper. i'm pretty new to linux, but i have been able to install this program in the past...anyways...

the ndiswrapper wiki would have me use this command:

```
make distclean
```

but xubuntu says command not found. do i not have something installed? 

thanks, i'd appreciate any input

---

### Post by noname101 on 2006-06-14
You shouldn't have to compile ndiswrapper. But I'm not sure since I'm not using xubuntu. Just install ndiswrapper-utils.
```
sudo apt-get install ndiswrapper-utils
```

---

### Post by maniacmusician on 2006-06-14
ah thanks, i should've realized that it would be in apt-get. but just for future reference (i'm sure i'll have to use it sometime), why did 'make' not work?

---

### Post by noname101 on 2006-06-14
Because you need to install build-essential.
```
sudo apt-get install build-essential
```

---

### Post by maniacmusician on 2006-06-14
ah thanks...but my problems are not over yet

i followed the instructions on the [ndiswrapper wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation") to the letter but still not working right. i get down to the step where you have to enter depmod -a. the first time i did that, it gave me an error and said permission denied, so i used it again with sudo; went through fine. the next step was to enter 'modprobe ndiswrapper.' did that too, without any errors. I think thats the point the lights on the card are supposed to light up and it should start working, but nothing happens. soo i keep going, enter 'iwconfig', and for some reason it is reading the card as eth1 instead of wlan0...could this be a problem? 

anyways, this is my situation now, and i don't know what to do next. what really irks me is that i've successfully done this before...that's life, i guess. i'd appreciate any help.

thanks.


edit: 'iwlist eth1 scan' yields "no scan results"

---

### Post by noname101 on 2006-06-14
What does ndiswrapper -l say?
Also what chipset is your card?

---

### Post by maniacmusician on 2006-06-14
it says 

```
Installed ndis drivers:
bcmwl5                  driver present, hardware present. 
```

as for the chipset, lspci tells me its BCM4306, but the entry i found on the ndis list of cards using the model number on the card that i have says its Broadcom 94306.

---

### Post by noname101 on 2006-06-14
It might be using a different driver. Try this:
```
sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
```
If that works then you know its using bcm43xx. So black list it.
```
sudo gedit /etc/modprobe.d/blacklist
```
Add at the bottom:
blacklist bcm43xx

---

### Post by maniacmusician on 2006-06-14
coincidentally, i tried that right before you posted. i saw it in another topic and figured i should try it. since i dont have gedit, i used mousepad instead, added blacklist bcm43xx at the bottom, saved it. and *then* tried ```
sudo modprobe -r bcm43xx
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper 
```

but it still worked; even though i had blacklisted it

meanwhile, the other driver i assigned using ndiswrapper is still not working

---

### Post by noname101 on 2006-06-15
What does iwconfig say?
Does sudo iwlist wirelessdevice scan show any results?
Also it doesn't matter if it shows up as eth1.

---

### Post by maniacmusician on 2006-06-15
yeah i checked all those again, and it seems to be all fixed. it once again shows up as wlan0, which is a good sign, and the scan comes up positive with the correct essid. i went into network settings and activated wlan0 and set everything up, and can get onto the network/use the internet and everything.

one more question; will this automatically load when i reboot? i remember i had a lot of trouble with that last time. I couldn't get the ndiswrapper module to launch at boot, so i had to enter it manually each time. if i could get this last step done, you'll have made my night. really. i'll give you hugs and kisses and everything. even chocolates, if you want.

---

### Post by noname101 on 2006-06-15
To load it at reboot do this:
```
sudo ndiswrapper -m
```
Add at the bottom of /etc/modules ndiswrapper.
```
sudo mousepad /etc/modules
```
I only want kisses and hugs if your a pretty women. Otherwise i'll pass. But i'll take the chocolates.

---

### Post by maniacmusician on 2006-06-15
ah i'll hold off on the hugs and kisses; i'm just a pretty man. (well maybe not *that* pretty. geekily handsome. haha.) chocolates huh? what kind?



but thank you! it's a totally cleansing feeling to know you can get on the internet again. you rock.

---

### Post by noname101 on 2006-06-15
Any chocolates will do. As long as its not dog poop.

---

