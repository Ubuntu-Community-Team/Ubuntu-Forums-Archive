---
title: "Trendnet TEW-645UB usb wireless card not supported?"
date: 2010-01-28
forum: Networking &amp; Wireless
---

### Post by jscott1 on 2010-01-28
New to Ubuntu and trying to get my wireless capabilities up and running. I didnt find my TEW-645UB usb wireless adapter on the list of supported ones, so I guess there is no way for me to get online with my desktop.
 
Also have a Sony Vaio laptop with an Intel Pro/Wireless 3945ABG card that i believe is supported. What are the basic steps to getting online with Ubuntu. I will search the forums but i would also appreciate any help as I am new to linux.

---

### Post by chili555 on 2010-01-28
> New to Ubuntu and trying to get my wireless capabilities up and running. I didnt find my TEW-645UB usb wireless adapter on the list of supported ones, so I guess there is no way for me to get online with my desktop.Au contraire, mon frere!

I believe it has the rt2870 chipset. Please open a terminal and do:```
lsusb
```Compare the device ID to the ones listed here: [http://ubuntuforums.org/showthread.php?t=1342593](http://ubuntuforums.org/showthread.php?t=1342593) 

If it matches, please do:```
sudo modprobe rt2870sta
```Does your wireless come to life?> Also have a Sony Vaio laptop with an Intel Pro/Wireless 3945ABG card that i believe is supported. What are the basic steps to getting online with Ubuntu.Make sure the wireless switch is on and click the Network Manager icon, see your network, supply any WEP, WPA, etc. passwords and connect.

Post back if it's not quite that easy!!

---

### Post by jscott1 on 2010-01-28
When I lsusb on my desktop I get 157e:3013 The only one close to that on the supported list says 157e:300e I think. Is this close enough?
 
On my laptop I am using Backtrack 4, and the network manager icon is Wicd Network Manager, but when I click this nothing happens...

---

### Post by chili555 on 2010-01-28
Let's take one at a time; unless you disagree, let's try the desktop first. The ID needs to match exactly. I have looked around at the various modules in the rt2xxx and rt3xxx family and none match. We are sure this is a Ralink 2870, because the Windows XP driver I downloaded from Trendnet's site says, in part:> Provider        = %[COLOR="Red"]Ralink[/COLOR]%

Compatible      = 1

DriverVer       = 01/09/2009, 1.04.00.0000

CatalogFile     = [COLOR="Red"]rt2870[/COLOR].cat            ;for WHQL certified



[ControlFlags]

;***********Ralink 802.11 n board  ***********

;ExcludeFromSelect = USB\VID_[COLOR="Red"]157E[/COLOR]&PID_[COLOR="Red"]3013[/COLOR]Let's install it with ndiswrapper. Drop the Ubuntu install CD in the tray and do:```
sudp apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-common ndiswrapper-utils-1.9
```Open your Home folder, create a folder called Trend and drag and drop the files on the Trendnet CD into Trend.You are looking for TEW-645UB (020609)/Drivers/XP_2000/Win2KXP. In that folder will be rt2870.inf.

Next, do:```
ndiswrapper -i ~/Trend/TEW-645UB (020609)/Drivers/XP_2000/Win2KXP/rt2870.inf
```If the driver is installed correctly, you should see the following output: > Installed ndis drivers:
  {name of driver} driver present, hardware presentThen do:```
sudo depmod -a
sudo modprobe ndiswrapper
```You should then have a wireless interface. Post back with any errors or problems.

---

### Post by jscott1 on 2010-01-28
First of all, thank you for your assistance, it is much appreciated. I am determined to make this work and learn linux so I can eventually leave windows behind. 
 
To recap, I have a desktop running windows xp with a Trendnet TEW-645UB usb wireless adapter, and also I have a Sony Vaio laptop with an Intel Pro/Wireless 3945abg adapter. I burned backtrack 4 and am running it live, to my understanding this is a Debian/Ubuntu op system, correct? Just want to make sure i am in the right forum... 
 
Do I need to use sudo?
 
Okay, I agree we can work on desktop first, but my problem is when I do the sudo apt-cdrom add it says
 
Using CD-ROM mount point /cdrom/
Unmounting  CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-Rom...
Identifying.. [4805dcdc4af3e51957db2e06ecf30cea-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: unable to locate any package files, perhaps this is not a Debian Disc
 
Another question is can i update the driver without being online?

---

### Post by chili555 on 2010-01-28
> I burned backtrack 4 and am running it live, to my understanding this is a Debian/Ubuntu op system, correct?Correct. > Just want to make sure i am in the right forum...Some of us, but not me, know a lot about Backtrack 4. If things are not working as expected, I don't really have any suggestions, except to try Backtrack's forums. [http://www.backtrack-linux.org/forums/](http://www.backtrack-linux.org/forums/)

Would you like to skip forward to the Vaio?

---

### Post by jscott1 on 2010-01-28
yes. I am going to download a copy of Ubuntu so i can start learning with that so I am not getting ahead of myself at all

---

### Post by chili555 on 2010-01-28
We'll be ready! When you post, send me a PM. I have a laptop with an Intel 3945, which works perfectly, and I'll be delighted to help.

---

### Post by 73ckn797 on 2010-01-28
I have successfully used "ndisgtk" from Synaptic Package manager to install the Windows XP driver into Ubuntu for a trendnet wireless card, though not the same one you are using.

---

### Post by jscott1 on 2010-01-29
Solution for my laptop was easy just did "start-network" and then wicd worked fine.

---

### Post by Jim March on 2010-10-22
If anybody else comes across this problem, the solution (tested in Lucid and Maverick so far) is to take the instructions at:

[http://ubuntuforums.org/showpost.php?p=8591348&postcount=6](http://ubuntuforums.org/showpost.php?p=8591348&postcount=6)

...and tweak 'em for the ID for the TEW-645UB, which is "157e:3013" per lsusb at the command line.

So where that page says:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "1737 0078" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```

...you do:

```
echo 'install rt2870sta modprobe --ignore-install rt2870sta ; /bin/echo "157e 3013" > /sys/bus/usb/drivers/rt2870/new_id' | sudo tee /etc/modprobe.d/rt2870sta.conf
sudo modprobe -rf rt2870sta
sudo modprobe rt2870sta
dmesg | egrep 'rt28|usb|Phy'
iwconfig
```

There's a second solution on that page under "alternativ automatic driver load" that didn't work for me.  If you try it, tweak the ID numbers along the same lines.

---

