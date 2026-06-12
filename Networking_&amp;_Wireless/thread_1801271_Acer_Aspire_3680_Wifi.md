---
title: "Acer Aspire 3680 Wifi"
date: 2011-07-10
forum: Networking &amp; Wireless
---

### Post by janhalik on 2011-07-10
Hi,
I've been trying to revive my old Acer Aspire 3680, which is supposed to have Acer InviLink™ 802.11b/g Wi-Fi CERTIFIED™ solution, supporting Acer SignalUp™ wireless technology, as shown is in [COLOR=Red][FONT=Arial Black][SIZE=4][COLOR=DarkOrange][Specification]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire3680/Aspire3680sp2.shtml")[/COLOR][/SIZE][/FONT]
[COLOR=Black]The system simply doesn't detect Wi-fi and I don't know how to make it work.
Please help[/COLOR]
[/COLOR]

---

### Post by westie457 on 2011-07-10
> **janhalik said:**
> Hi,
I've been trying to revive my old Acer Aspire 3680, which is supposed to have Acer InviLink™ 802.11b/g Wi-Fi CERTIFIED™ solution, supporting Acer SignalUp™ wireless technology, as shown is in [COLOR=Red][FONT=Arial Black][SIZE=4][COLOR=DarkOrange][Specification]("http://support.acer.com/acerpanam/notebook/0000/Acer/Aspire3680/Aspire3680sp2.shtml")[/COLOR][/SIZE][/FONT]
[COLOR=Black]The system simply doesn't detect Wi-fi and I don't know how to make it work.
Please help[/COLOR]
[/COLOR]

Hi in a terminal type```
lspci
```
copy the output come back here click on New Reply then click on the # -symbol and paste between the brackets. The # is for code tags and make things easier to read.

---

### Post by matt_symes on 2011-07-10
Hi

The output of

```
sudo lshw -C network
```

may be useful as well. Enter your password. It will not be echoed to the screen.

Kind regards

---

### Post by chili555 on 2011-07-10
I think Matt and Westie also want:```
rfkill list all
```An Acer, eh?

---

### Post by bkratz on 2011-07-10
> **chili555 said:**
> I think Matt and Westie also want:```
rfkill list all
```An Acer, eh?



might as well get a

lsmod | grep acer

too!

---

### Post by chili555 on 2011-07-10
Wow! janhalik has four surgeons hovering over his lifeless Acer!

---

### Post by bkratz on 2011-07-10
> **chili555 said:**
> Wow! janhalik has four surgeons hovering over his lifeless Acer!


But we seem to have lost the "patient" anyway!

---

### Post by janhalik on 2011-07-10
i'm back :P but my comp is not :(

```
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
02:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
0a:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
0a:09.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
0a:09.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
```any ideas? i see it's Broadcom, but I still have no idea

---

### Post by bkratz on 2011-07-10
Joseph has written a pretty good description of what you need here.

[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)

you probably will want to post this when done (unless everything works)

rfkill list all

---

### Post by janhalik on 2011-07-10
i tried to follow the first half of the instructions but to no avail.
[[IMG]http://img715.imageshack.us/img715/488/selection003z.th.png[/IMG]]("http://img715.imageshack.us/i/selection003z.png/")
looks like its presence is not even detected. my light indicating wifi functions hasn't flicked since having installed the system (but it worked before with Windows XP)
[B]
rfkill list all[/B]     does nothing at all

---

### Post by bkratz on 2011-07-10
> **janhalik said:**
> i tried to follow the first half of the instructions but to no avail.
[[IMG]http://img715.imageshack.us/img715/488/selection003z.th.png[/IMG]]("http://img715.imageshack.us/i/selection003z.png/")
looks like its presence is not even detected. my light indicating wifi functions hasn't flicked since having installed the system (but it worked before with Windows XP)
[B]
rfkill list all[/B]     does nothing at all



please post the output of 

```
lsmod | grep b43
```

and also

lspci -vnn | grep 14e4

---

### Post by janhalik on 2011-07-10
[[IMG]http://img12.imageshack.us/img12/8029/selection006.th.png[/IMG]]("http://img12.imageshack.us/i/selection006.png/")

---

### Post by bkratz on 2011-07-10
From this page

[http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices](http://linuxwireless.org/en/users/Drivers/b43#Known_PCI_devices)

"
Ubuntu/Debian

In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you:


 sudo apt-get install b43-fwcutter

You will be asked to automatically fetch and install the firmware into the right location. Again, you will need an internet connection.  "

---

### Post by janhalik on 2011-07-10
```
*****@*****-Aspire-3680:~$ sudo apt-get install b43-fwcutter
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
b43-fwcutter is already the newest version.
The following packages were automatically installed and are no longer required:
  quilt libnspr4-0d debconf-utils
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by janhalik on 2011-07-10
maybe i just have it turned off somehow....if there's such an option....

---

### Post by bkratz on 2011-07-10
Try 

sudo modprobe b43

and see if your wireless comes to life

---

### Post by janhalik on 2011-07-10
> **bkratz said:**
> Try 

sudo modprobe b43

and see if your wireless comes to lifeI LOVE YOU!!! it worked. (already writing thru wifi) 
just one last question. will I have to type in this every time?

---

### Post by bkratz on 2011-07-10
> **janhalik said:**
> I LOVE YOU!!! it worked. (already writing thru wifi) 
just one last question. will I have to type in this every time?



To quote the famous Dr. Chili
"

Quote:
we'll take steps to load it automagically on boot.
Please do:

sudo su
echo "b43" >> /etc/modules
It should now load correctly on boot. "

Oh, and by the way go to the thread tools and mark the thread as solved in case it helps someone else.

Oh, and the I love you was a bit strong! your thanks is enough, that is why the volunteer help!

and yes it would have probably quit after a reboot without adding it to the modules

---

### Post by RFWB on 2012-01-31
I'm a new forum member and this is my first post - I have the same Acer Aspire 3680, same wifi problem, same success - Thanks ! :)

---

### Post by geosto on 2012-04-27
I am also a new member and did have the same problem.
I thought i was smart and skip the first solutions bud the are all needed.
If you follow this thread step by step it works like a charm.

regards George 

:guitar:

---

### Post by lisati on 2012-04-27
Old thread closed.

---

