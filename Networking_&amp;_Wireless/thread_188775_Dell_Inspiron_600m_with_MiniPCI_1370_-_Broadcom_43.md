---
title: "Dell Inspiron 600m with MiniPCI 1370 - Broadcom 4318 - ndiswrapper"
date: 2006-06-04
forum: Networking &amp; Wireless
---

### Post by K.Mandla on 2006-06-04
Hello. I wanted to post this in hopes of helping any other Dell Inspiron 600m (or similar machine) owners who need to configure a Dell 1370 MiniPCI wireless card under Dapper 6.06. This card uses the dreaded Broadcom 4318 chipset, which seems to stand out among Broadcom wireless cards as particularly quarrelsome.

That being said, it's possible that you have an identical chipset in a different card or laptop, and this method might work for you. But just for the record, this method is aimed at a 600m armed with the 1370. In other words, your mileage may vary.

I had to solve this one. Running without wireless on this machine was not an option, since it's [mom's computer]("http://www.ubuntuforums.org/showthread.php?t=156175"). :)

I've gone through this procedure twice now, once after hacking away mercilessly at the [bcm43xx method]("http://www.ubuntuforums.org/showthread.php?t=185174"), and once with a clean Xubuntu 6.06 installation. It worked fine both times for me, but be aware that tweaking and retweaking your system could be preventing things from working out. 

**Is this method for me?**

[indent]The first thing you should do, before reading any further, is to see if this post can help you at all. You can check to see if you have similar hardware to mine by entering *lspci* into a terminal.

> Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
If your hardware matches the 4318 chipset and version 2, this procedure might work for you. Of course, it might not, but you could always try, just to see.[/indent]

**Get ndiswrapper ... without the Internet**

[indent]I used ndiswrapper to get things going. *ndiswrapper-utils* is part of the installation CD so you don't need a hard line to download it. 

```
sudo apt-get install ndiswrapper-utils
```
It will ask for your installation CD and install ndiswrapper.[/indent]

**Working drivers**

[indent]Next we need drivers. The drivers downloaded from Dell's support site did not work for me under ndiswrapper. For that reason, I went surfing for another version, and found these.

[ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe](ftp://ftp.hp.com/pub/softpaq/sp30001-30500/SP30379.exe)

These are bundled as a Windows executable and are intended for HP machines. That means it wants to be decompressed in Windows, which may or may not be an option for you. It could also be run under wine, if you have that installed. (Personally, I abandoned Windows quite some time ago, but my witless employer runs XP at work, so I lucked out and decompressed them onto my work station. I should also mention that my witless employer's IT team has given everyone administrator privileges. Go figure.)

However you handle it, extract the files into a directory on your laptop. (Do yourself a favor: Give that directory a short and easy name to type. :) ) Open a terminal window and move to that directory.[/indent]

**Install the drivers**

[indent]Now install the driver with ndiswrapper.

```
sudo ndiswrapper -i bcmwl5.inf
```
Note that I gave ndiswrapper the inf file. I don't know enough about ndiswrapper to tell you if it needs the other files or not, but I kept them all in one directory, just to be sure. Chances are you could throw out the rest of that stuff and never know the difference.

Check to see if ndiswrapper is happy with your hardware and the driver.

```
sudo ndiswrapper -l
```
If you see anything other than "hardware present, driver present", you might end up disappointed.[/indent]

**Tweaking ndiswrapper's results**

[indent]Now put ndiswrapper to work.

```
sudo modprobe ndiswrapper
```
And make sure it's part of your startup routine.

```
sudo ndiswrapper -m
```
You should see a message that says 

> Adding 'alias wlan0 ndiswrapper' to /etc/modprobe.d/ndiswrapper
I think this is where one small problem creeps in. On my system, the wireless is eth1, so as I understand it, adding wlan0 doesn't do much for me. It's easy to fix, though.

```
sudo nano /etc/modprobe.d/ndiswrapper
```
Where you see *wlan0* in that file, change it to *eth1*, or the proper name for your wireless card. (Don't know the name? *sudo iwconfig* should tell you.)[/indent]

**Some smaller adjustments**

[indent]Next step: set the rate to 11M at all times. Time to edit another file ...

```
sudo nano /etc/network/interfaces
```
Change this line

> iface eth1 inet dhcp
to look like this

```
iface eth1 inet dhcp
	pre-up sudo iwconfig eth1 rate 11M
```
Again, remember to use the proper identifier for your wireless card.

You might see your wireless essid and key there; if not, you can add it  below those lines with something like this:

```
wireless-essid _________
wireless-key __________
```
Remember that those blanks are the digits of your essid and encryption key. Don't copy and paste the blanks. ;) Of course, you might prefer to add that info through your friendly neighborhood networking GUI.[/indent]

**Blacklist bcm43xx**

[indent]Next stop: Get rid of bcm43xx. It seems that the bcm43xx module is installed by default, or at least installed when Ubuntu senses a Broadcom card with that sequence. I think it might be hindering some 4318 users, though. Let's blacklist it.

```
sudo nano /etc/modprobe.d/blacklist
```
At the bottom, add

```
blacklist bcm43xx
```
This should prevent bcm43xx from running again when you start up your laptop. 

At this point, I suggest rebooting. It might not be necessary, but I think after inserting and removing modules and setting things to run on startup, you might do well to start fresh. And besides, what happens if you get it working, then reboot and it's broke again?[/indent]

**We walk from here**

Now you should be able to manage your network with the network GUI. I'm a Xubuntu fan, so I access the network setup through Applications > System > Networking. Using KDE or Gnome or what have you will put that menu elsewhere.

I think that's about it. If you don't meet with success, you might try different drivers, or you might try the fwcutter method described elsewhere. Best of luck! :)

[SIZE="1"]**P.S.:** I didn't call this a howto, since I have little experience with this hardware and Linux on the whole, and I don't want to disappoint anyone. :)[/SIZE]

---

### Post by Braino on 2006-06-04
Great post! That is what I did to get it working too. I also found the Dell drivers don't seem to work right. Here is another place you can get the correct driver: [ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip](ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip)
You just need to unzip that one (no Windows needed).

---

### Post by zahidism on 2006-06-04
or try [http://ubuntuforums.org/showthread.php?t=185174&highlight=inspiron+600m]("http://ubuntuforums.org/showthread.php?t=185174&highlight=inspiron+600m") that guide.  it's for broadcom chipsets.  worked like a charm for me.

---

### Post by K.Mandla on 2006-06-04
[QUOTE=zahidism]or try [http://ubuntuforums.org/showthread.php?t=185174&highlight=inspiron+600m]("http://ubuntuforums.org/showthread.php?t=185174&highlight=inspiron+600m") that guide.  it's for broadcom chipsets.  worked like a charm for me.[/QUOTE]
I saw that one; it's the one I mentioned near the top of the post. I spent most of Friday afternoon trying to get that to work, but it seems for a lot of 4318 users, it's not working. :-k

---

### Post by pzipfel on 2006-06-11
I appreciate the effort, but I have found that everytime I try to install the driver with ndiswrapper I get an error at line 139 or something along those lines and nothing installs correctly.  If I -l to see if it installed properly, I get an error message next to the driver list.  If i ndiswrapper -e to uninstall as the program itself says, it won't let me.

I'm currently doing my 3rd install of Xubuntu 6.06 in the last 8 hours trying to figure this out, so any help you can give would be appreciated.  I'm going to try the bcm43xx-cutter method again with this install, but you're the first person I've seen mention Xubuntu.

edit:  nevermind, i'm presently using Xubuntu and posting this after using the bcm43xx-cutter method.  I'm a little leary to restart because I'm afraid it's a one time thing, but I have internet.

---

