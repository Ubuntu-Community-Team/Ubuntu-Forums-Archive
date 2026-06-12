---
title: "can't connect to wireless"
date: 2009-04-17
forum: Networking &amp; Wireless
---

### Post by rhythmiccycle on 2009-04-17
I just got ubuntu, I've never used Linux before.

so I installed ubuntu onto my laptop. and it's not connected to the wireless.

i did some reading and it seems i need to get "widc"

i went to a couple of sites that explained how to install it directly from the net, but I CAN NOT GET ONLINE.

i found this site:
[http://linux.softpedia.com/progDownload/Wicd-Download-40130.html](http://linux.softpedia.com/progDownload/Wicd-Download-40130.html)

and got a file called this:
wicd_1.5.8_all.deb

so i put the deb file on to a usb drive, and clicked on it, and i get the message

"error: Conflicts with the installed package 'network manager' "

I then went to the "add/remove" thing, and unchecked "network manager", but i still got the same message.

i just want to connect to my wireless network, 
please help.

---

### Post by Daisuke_Aramaki on 2009-04-17
> **rhythmiccycle said:**
> I just got ubuntu, I've never used Linux before.

so I installed ubuntu onto my laptop. and it's not connected to the wireless.

i did some reading and it seems i need to get "widc"

i went to a couple of sites that explained how to install it directly from the net, but I CAN NOT GET ONLINE.

i found this site:
[http://linux.softpedia.com/progDownload/Wicd-Download-40130.html](http://linux.softpedia.com/progDownload/Wicd-Download-40130.html)

and got a file called this:
wicd_1.5.8_all.deb

so i put the deb file on to a usb drive, and clicked on it, and i get the message

"error: Conflicts with the installed package 'network manager' "

I then went to the "add/remove" thing, and unchecked "network manager", but i still got the same message.

i just want to connect to my wireless network, 
please help.

you cannot install wicd right alongside network-manager. in any case, are you able to see your wireless access points. i mean if you have network manager, you can check it out. It will already tell you what networks are available and then you can choose your network, supply the credentials and it should be up and running. Do you have everything else set up?. like the driver for your wireless card and such?

---

### Post by rhythmiccycle on 2009-04-17
i am not able to see your wireless access points.

when i click on the network manager icon, on the top right. 
a drop down menu pops up, and wireless and wireed networks are in grey, nothing happens when i click on it.

i can't find the list of available networks. (i can when i'm on XP)

i tryed adding a network and typing the info, from my network, like the name and password, but that didn't work.

 maybe it is the driver, when i run xp, the drivers are just there, i'm using a dell inspiration 1300.

i'll try looking up,

"dell inspiration 1300 Linux wireless driver"

if it works, i'll post a reply. otherwise, i need more help

thank you

---

### Post by Daisuke_Aramaki on 2009-04-17
> **rhythmiccycle said:**
> i am not able to see your wireless access points.

when i click on the network manager icon, on the top right. 
a drop down menu pops up, and wireless and wireed networks are in grey, nothing happens when i click on it.

i can't find the list of available networks. (i can when i'm on XP)

i tryed adding a network and typing the info, from my network, like the name and password, but that didn't work.

 maybe it is the driver, when i run xp, the drivers are just there, i'm using a dell inspiration 1300.

i'll try looking up,

"dell inspiration 1300 Linux wireless driver"

if it works, i'll post a reply. otherwise, i need more help

thank you

Execute this command in a terminal and post the output here

```
lspci
```

---

### Post by rhythmiccycle on 2009-04-17
i found this at [http://pryds.eu/ubuntu/7.04.php:](http://pryds.eu/ubuntu/7.04.php:)

"The driver for the wireless network card in the Inspiron 1300 doesn't come with a Linux driver, and there is no such to find. Fortunately, the ndiswrapper project makes it possible to use a Windows driver on Linux. They have a great guide on how to make it work on Ubuntu."

i'm reading that here

---

### Post by Daisuke_Aramaki on 2009-04-17
> **rhythmiccycle said:**
> i found this at [http://pryds.eu/ubuntu/7.04.php:](http://pryds.eu/ubuntu/7.04.php:)

"The driver for the wireless network card in the Inspiron 1300 doesn't come with a Linux driver, and there is no such to find. Fortunately, the ndiswrapper project makes it possible to use a Windows driver on Linux. They have a great guide on how to make it work on Ubuntu."

i'm reading that here

Good. so i guess you might be having a broadcom chip

---

### Post by rhythmiccycle on 2009-04-17
> **Daisuke_Aramaki said:**
> Execute this command in a terminal and post the output here

```
lspci
```

i never used Linux before, how do I open a terminal?

---

### Post by Daisuke_Aramaki on 2009-04-17
> **rhythmiccycle said:**
> i never used Linux before, how do I open a terminal?

assuming you are using gnome, press alt+f2 to launch the run dialog. then type gnome-terminal. you will get a terminal

---

### Post by rhythmiccycle on 2009-04-18
ok, 

i typed lspci, and got
> 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)

00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)

00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 03)

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)

00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03)

02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)

02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)




I also found this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

i'm using ubuntu 8.10

and i'm up to step "2.2. Installing Packages (With Internet access on another computer)"

but i'm not sure what "Architecture" to download

amd64 OR i386

i think i should get i386, because i'm not running at 64bit, but i'm not sure

Do you think that website will get my wireless working?

and IF so, what "Architecture" should I download?

---

### Post by Daisuke_Aramaki on 2009-04-18
> **rhythmiccycle said:**
> ok, 

i typed lspci, and got


I also found this page:

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

i'm using ubuntu 8.10

and i'm up to step "2.2. Installing Packages (With Internet access on another computer)"

but i'm not sure what "Architecture" to download

amd64 OR i386

i think i should get i386, because i'm not running at 64bit, but i'm not sure

Do you think that website will get my wireless working?

and IF so, what "Architecture" should I download?

i386 is the one.

---

### Post by rhythmiccycle on 2009-04-18
i've been doing the steps from the website, i gave in my last post.

 i downloaded 

> 
For 8.10 Intrepid Ibex
   1.[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-common)
   2.[http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9](http://packages.ubuntu.com/intrepid/misc/ndiswrapper-utils-1.9)
   3.[http://packages.ubuntu.com/intrepid/net/ndisgtk](http://packages.ubuntu.com/intrepid/net/ndisgtk)


put them on to a usb drive, and then installed onto ubuntu from the usb.

now i'm on step "3.1. Disable Free Drivers"

it says

> 
Firstly, all releases since Ubuntu 6.06 have the open source bcm43xx driver, which was replaced in 8.04 by b43 and b43legacy, see WifiDocs/Driver/bcm43xx. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx lines for each driver to the modprobe blacklist.

```

echo -e "blacklist bcm43xx\nblacklist b43\nblacklist b43legacy\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist

```

(Or just edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx, blacklist b43, blacklist b43legacy and blacklist ssb to the end of the file.) Note: This only effects what is loaded at startup, so you will have to reboot to have the bcm43xx drivers disabled. If you have an atheros based card, remember to blacklist not only ath_pci, but also ath_hal, since ndiswrapper won't work if ath_hal is still loaded. 



first of all how do I "see WifiDocs/Driver/bcm43xx"

and i'm gussing that after I "see it" then i won't work. IF so, i think that means that i just type that code in (exactly the same as above) into my terminal, and hit enter. Am i correct? OR do I need to change the code somewhat?


i just want to double check before i start disabling things

(btw, thank you so much Daisuke_Aramaki, i'd be so lost with out you.)

---

### Post by rhythmiccycle on 2009-04-19
I tried to "just edit the /etc/modprobe.d/blacklist" i found the file and opened it, and typed what it said to type, but when i try to save it says

> 
Could not save the file /etc/modprobe.d/blacklist.
you do not have the permissions necessary to save the file.
please check that you typed the location correctly and try again.


i looked at the properties of the folder, it says "you are not the owner, so you cannot change these permissions"
I am the owner, i only made one account when i first installed ubuntu, how do I "be an owner"?

---

### Post by Daisuke_Aramaki on 2009-04-19
> **rhythmiccycle said:**
> I tried to "just edit the /etc/modprobe.d/blacklist" i found the file and opened it, and typed what it said to type, but when i try to save it says



i looked at the properties of the folder, it says "you are not the owner, so you cannot change these permissions"
I am the owner, i only made one account when i first installed ubuntu, how do I "be an owner"?

I am guessing you tried to open the file with a text editor right? Since it can be edited only by root, you can use sudo to open the file using gedit for example. Issue this command in a terminal

```
sudo gedit /etc/modprobe.d/blacklist
```

Now you can edit and save the file.

---

### Post by rhythmiccycle on 2009-04-20
i'm up to step "3.6. Configuring Wireless Network Settings"



"3.6.1. Configuring Wireless Network Settings using nm-applet (GNOME front end for Network Manager)"

it says

> 
If this applet is installed, it makes wireless network connection to multiple networks (roaming) easier - this is useful if you use your laptop to connect to wireless networks at more than one location.

Open the Networking Admin tool (System | Administration | Networking), select the Wireless connection and click Properties, ensure the Enable roaming mode checkbox is ticked. 

I clicked on "System" up top then down to "Administration"  but then the was no "Networking" ,only "network tools".

i clicked on network tools, but there was nothing about wireless.

(btw: before, i unchecked the network manger before, and i checked it back on; using wired Ethernet connection to the internet.)


do i need to install an applet?
if so where do i get it?

---

