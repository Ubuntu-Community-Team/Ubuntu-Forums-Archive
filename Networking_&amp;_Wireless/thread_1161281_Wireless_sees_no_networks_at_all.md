---
title: "Wireless sees no networks at all"
date: 2009-05-16
forum: Networking &amp; Wireless
---

### Post by EricDallal on 2009-05-16
I am currently trying to configure Ubuntu to get internet  on an dell mini. I have been using Ubuntu for years myself and have always managed to get the internet to work on other computers, but this ultra user friendly version of Ubuntu is a pain in the behind. The wireless doesn't even see any networks. I have tried switching the wireless on and off (I actually can't tell when it is on and when it is off since there is no light on this stupid computer, but I know that I can toggle on/off with fn 2) and then trying sudo /etc/init.d/networking restart. Nothing seems to work. It not only doesn't connect to my wireless network (which has four other computers connected to it without any problems), but doesn't even see any other network (all the other computers can see the neighbour's network).

Any ideas?

---

### Post by Aaardwark on 2009-05-16
What wireless card do you have? Which drive is it using?

---

### Post by EricDallal on 2009-05-16
I put it in sleep after putting starting this thread and when I took it out of sleep it connected. Except that now it won't stay connected for more than 2min at a time. I'm not sure what the wireless card is, but the driver is wext.

---

### Post by Aaardwark on 2009-05-16
With dell you can always check what hardware you have, by checking their website. Either by using the name (dell dimension 5990, or whatever) or using a number on a tag that they will guide you too from their site. I've had use of this once when the card was one thing, but the chip something else. Here is a link to the searchpage:
[http://support.dell.com/support/index.aspx?c=us&cs=19&l=en&s=dhs](http://support.dell.com/support/index.aspx?c=us&cs=19&l=en&s=dhs)

Of course using linux you can also use the terminal:
lspci | grep wifi
or
dmesg | grep wifi

---

### Post by EricDallal on 2009-05-16
Broadcom Corporation BCM4312 802.11b/g (rev 01)

---

### Post by Aaardwark on 2009-05-16
The problem your having is a driver problem. It believes you have the right driver. The driver isn't working, even if it signals it does, thus no networks!

Plug in the computer via cable, check if there is an STA driver in System -> Administration -> Hardware Drivers. If there is, install it. Tell me how it goes. If it doesn't work, I believe it works with ndiswrapper. My girlfriend has a laptop with bcm4312 rev 02 I think. I'll look up the ndiswrapper guide for you, if it doesn't work.

---

### Post by EricDallal on 2009-05-16
The STA wireless driver was installed but disactivated before. However, activating it (and restarting) changed nothing. It still doesn't connect at first when I start up. It also continues to connect and disconnect every 30secs once I put the computer to sleep and wake it up again.

---

### Post by Aaardwark on 2009-05-16
Ok, means we have to do it the hard way with ndiswrapper. [There is a guide for this]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff#head-bc33832c0547766a33c3a84f13f971ca757b2851")

But I'll paste the steps you will have to do. Copy and paste them one line at the time. Type your password when it asks for it. Here we go:
echo -e 'blacklist bcm43xx\nblacklist wl' | sudo tee -a /etc/modprobe.d/blacklist
sudo apt-get install ndiswrapper-utils-1.9
mkdir ~/bcm43xx; cd ~/bcm43xx
sudo apt-get install cabextract
wget [ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe](ftp://ftp.compaq.com/pub/softpaq/sp33001-33500/sp33008.exe)
cabextract sp33008.exe
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo cp /etc/network/interfaces /etc/network/interfaces.orig
echo -e 'auto lo\niface lo inet loopback\n' | sudo tee /etc/network/interfaces
sudo ndiswrapper -m
echo 'ndiswrapper' | sudo tee -a /etc/modules
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant

Now copy this line:
lshw -C network
Ignore the initial warning it gives. It will list details of you network devices. If, in the "configuration" line, the wireless interface says "module=ssb" instead of "module=ndiswrapper", then use the following lines:
sudo rmmod b43
sudo rmmod b44
sudo rmmod b43legacy
sudo rmmod wl
sudo rmmod ssb
sudo rmmod ndiswrapper
sudo modprobe ndiswrapper
sudo modprobe ssb
sudo modprobe b44

Hopefully, lshw -C network will now show your wireless interface to have "module=ndiswrapper" instead of "module=ssb." If you can connect to other networks now, then edit modprobe:
sudo gedit /etc/modprobe.d/ndiswrapper
paste in the following:
echo -e '#Hardy ssb/ndiswrapper workaround, added' `date` '\ninstall ndiswrapper modprobe -r b43 b44 b43legacy ssb; modprobe --ignore-install ndiswrapper $CMDLINE_OPTS; modprobe ssb; modprobe b44;' | sudo tee -a /etc/modprobe.d/ndiswrapper

Save, exit, and enjoy you solved problems! :D

---

### Post by EricDallal on 2009-05-16
Thank you for the help. However, before I do all this, I would like to mention that the wireless internet worked for a while after I obtained this computer. I think it actually stopped working after some updates were done. Is it possible the computer uses ndiswrapper naturally, but that I disabled while trying to fix the wireless?

---

### Post by Aaardwark on 2009-05-16
It wouldn't use ndiswrapper by default. Ndiswrapper is a way to use windows wireless drivers in linux. However it is possible that STA or wl och something worked before an update. Generally things in Ubuntu don't break when updating, it's rare but happens. The positive thing with this is: If it works your are pretty much guaranteed Ubuntu wont mess with these drivers.

---

### Post by MartinGS on 2009-05-16
I had a Broadcom card in a Dell Inspiron 1000 and after 50 hours of messing with it, I gave up.  The Broadcom would work but when I changed users or rebooted it was gone and then I couldn't get it back.

You might want to enable SSID broadcast and set up and access list.

I bought a Edimax EW-7108PCG Wireless PCMCIA Adapter for $25 including shipping and it works perfect, no driver, WPA-PSK security, it just works. The box even says "Supports the most popular operating system: Windows 98SE/Me/2000/XP/Vista and Linux".

I think your mini has the NIC built in, but good luck with the Broadcom.

---

### Post by EricDallal on 2009-05-16
This computer doesn't have windows installed on it (at all). The dell mini comes in either Ubuntu or Windows, however, so it might be possible that they installed windows drivers on it by default. That being said, I am somewhat skeptical. Is there any other reason to use Ndiswrapper besides if windows is also installed on the computer (on another partition like on my other Ubuntu computers)?

---

### Post by Aaardwark on 2009-05-16
No windows driver is installed by default in Ubuntu. Some wireless cards need parts of the windows drivers to work. You wont be using windows. You will be using part of a driver made for windows. There would be no point in using ndiswrapper with windows, since windows already can use drivers for windows.

Have you tried the steps yet? Did it work?

---

### Post by EricDallal on 2009-05-17
What if the module says wl?

---

### Post by EricDallal on 2009-05-17
> Now copy this line:
lshw -C network
Ignore the initial warning it gives. It will list details of you network devices. If, in the "configuration" line, the wireless interface says "module=ssb" instead of "module=ndiswrapper", then use the following lines:

What if it says module=wl?

---

### Post by EricDallal on 2009-05-17
Also, I got:

bcmwl5 : driver installed

as the output to:

ndiswrapper -l

I found the following on the foums:

> If the output of 'ndiswrapper -l' says that a driver is installed but doesn't mention either device XXXX:XXXX present or invalid driver, then something's wrong: most likely you installed the wrong Windows driver.

The most reliable way to locate the appropriate Windows drivers for your wireless device is to search the ndiswrapper site for your wireless card's device ID and chipset model.

---

### Post by EricDallal on 2009-05-17
Unfortunately, I can't seem to find this list (I found a link but the link was empty).

---

