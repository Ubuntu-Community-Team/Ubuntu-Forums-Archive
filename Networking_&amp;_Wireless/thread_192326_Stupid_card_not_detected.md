---
title: "Stupid card not detected"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Minyaliel on 2006-06-08
This was also an issue with Breezy - I never really got my wireless card to work. Ubuntu won't detect it, even though it's supposedly one of those cards that should be detected automatically, according to a wifi "guide" on the wiki (?). I'm using a Topcom Skyracer Pro PC Card 3054 on a HP Pavilion ze2000. It actually did work for a while out of the box when I first installed hoary. Not anymore... I've done all the things I should do to get it working. I've got the drivers, I've followed all the guides available, I've installed madwifi. Nothing. And I really need my wifi card to work. So I'd be _very_ grateful if someone could help me make this thing work permanently, not just for one session (yes, that's actually happened while I was still using breezy. One session, I fixed it, it worked, next time I tried connecting it wouldn't detect the drat card again).

---

### Post by ComplexNumber on 2006-06-08
i'm not really sure what you've done already, so here are some questions to give people an idea of where to start to help:
-are you on a router?
-do you have network manager installed? (i assume you're using gnome). wifi-radar seems to be some help too.
-are your drivers installed? you can check by typing 'ndiswrapper -l'. also, don't forget to run the statement 'modprobe ndiswrapper' each and every time you login otherwise your card won't be detected. you an put this statement in /etc/rc.d/rc.local file.
-check that the following services are running and start at boot: netwrok manager, network manager dispatcher(i'm not too sure if this is a fedora thing or not), named. i think wpa_supplicant has to be switched off too. it certainly does for me.
-after you've typed modprobe ndiswrapper, type in iwlist wlan0 scan (if it isn't wlan0, it will be ra0(i think)). what is the output?


oh, and install gnome keyring manager too. everytime i login, it pops a keyring dialogue up asking for the password to access the internet. so i guess its needed too.

---

### Post by Minyaliel on 2006-06-09
I'm not on a router. The output for the ndiswrapper -l rather confused me, though...

niah@Azazel:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver!

---

### Post by rcatman on 2006-06-12
[QUOTE=Minyaliel]I'm not on a router. The output for the ndiswrapper -l rather confused me, though...

niah@Azazel:~$ ndiswrapper -l
Installed ndis drivers:
bcmwl5  invalid driver![/QUOTE]

I had the same problem with my D-Link wifi card. 

I followed the steps in
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)


Basically, I found the latest drivers for the card by going to the vendors site and downloaded the zip file. I unzipped it and found the folder that contained the .inf file. Copy all the .inf file along with any .sys or .bin files that are in the folder into  seperate folder. 

When you issue the command 
sudo ndiswrapper -i YOURWIFI.INF
you must be in the folder as the .inf and .sys files. It will install the driver. Hopefully now the driver was setup properly! 

ndiswrapper -l    should show you that it found the hardware and installed the driver. i hope that helps.

i'm pretty new to ubuntu (linux user for 3 weeks now) but after scowering the online forums thats the advice that helped. Good luck.

---

### Post by Minyaliel on 2006-06-13
Hey, thanks, I'm going to give that a go. :)

---

### Post by dyssident on 2006-06-13
i too had to deal with an atheros chipset. 

first issue is drivers. ndiswrapper didnt work for me but madwifi did. also i believe bcmwl5 is for a broadcom chipset, but yours should be atheros. so try:

```

# remove driver
sudo ndiswapper -x bcmwl5
# remove ndiswrapper
sudo modprobe -r ndiswrapper
# reinstall latest madwifi
sudo apt-get -y install --reinstall linux-restricted-modules

```

make sure that it is working by doing

```
sudo iwlist ath0 scan
```

as for stopping working, im not sure what you mean by "session". if you rebooted and it stopped working then you probably are not starting something up correctly, but if it just sort of randomly drops the connection that is potentially a bigger problem.

are you using NetworkManager?

---

