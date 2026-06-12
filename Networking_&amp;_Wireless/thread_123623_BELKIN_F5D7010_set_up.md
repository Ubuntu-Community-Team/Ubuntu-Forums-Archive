---
title: "BELKIN F5D7010 set up"
date: 2006-01-30
forum: Networking &amp; Wireless
---

### Post by jimmy_29_75 on 2006-01-30
Hi,

I have been trying to set up Belkin F5D7010 version 4 on Breezy Badger w/o any luck. I copied the bcmwl5.inf from the CD-rom that came with the PCMCIA card. From the synaptics package i have appled the ndiswrapper utility.When I follow instrucion this is whta i see

ndiswrapper i/path/bcmwl5.inf i get ndiswrapper OPTION. ndiswrapper -l says there is no driver installed.

My pciid is 14e4:4318, but what is my driverid?????? I'm not sure if I need any other driver. This is the only reason I'm hanging on to windows and really want to get away from it. Please help, Please!!!!!!!!!!

Thanks.
PS: It is a DEll latitude, C610, PIII, 1GHz, 20GB

---

### Post by bscbrit on 2006-01-30
Have you followed these instructions?

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper](https://wiki.ubuntu.com/HowToSetUpNdiswrapper)

I used the driver from my CD (despite all of the advice not to) and it worked perfectly.  Well, it did in unencrypted form.  I have just (15 minutes ago! \\:D/ ) solved the problem of getting it to function encrypted.  Do not waste your time using the GUI - it does not do what you think it should.  But I am getting ahead of you.  Follow the directions in the link using the driver from your CD and then let me know how you get on.

---

### Post by jimmy_29_75 on 2006-01-30
Hi bscbrit,

Thanks for your reply. Here is the outcome. I get an error when I do modprobe. The one in red is the belkin card. I have tried several drivers(CD-rom, other broadcom drivers, still no success) and sorry for posting such a long one. 
Plz see below

jimmy@laptop:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82830 830 Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Co ntroller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev  78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420
0000:07:00.0 Network controller: Broadcom Corporation: Unknown device 4318 (rev 02)
jimmy@laptop:~$ lspci -n
0000:00:00.0 0600: 8086:3575 (rev 04)
0000:00:01.0 0604: 8086:3576 (rev 04)
0000:00:1d.0 0c03: 8086:2482 (rev 02)
0000:00:1e.0 0604: 8086:2448 (rev 42)
0000:00:1f.0 0601: 8086:248c (rev 02)
0000:00:1f.1 0101: 8086:248a (rev 02)
0000:00:1f.5 0401: 8086:2485 (rev 02)
0000:00:1f.6 0703: 8086:2486 (rev 02)
0000:01:00.0 0300: 1002:4c59
0000:02:00.0 0200: 10b7:9200 (rev 78)
0000:02:01.0 0607: 104c:ac51
0000:02:01.1 0607: 104c:ac51
[COLOR="Red"]0000:07:00.0 0280: 14e4:4318 (rev 02)[/COLOR]
jimmy@laptop:~$ sudo ndiswrapper -i/home/desktop/2/bcmwl5.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
jimmy@laptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

jimmy@laptop:~$ sudo ndiswrapper -hotplug
jimmy@laptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

jimmy@laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Operation not permitted
jimmy@laptop:~$

---

### Post by jimmy_29_75 on 2006-01-30
I have tried a lot and since a lot of ppl have got this to work, I'm sure I'm doing something wrong. Can anybody give me a detailed step-by-step instructions.I'm a newbie to linux!!!

---

### Post by Lambert on 2006-01-30
post output of these commands here.

```
cat /proc/version 
```
```
sudo modinfo ndiswrapper 
```

then run this command, there will be no output

```
sudo slocate -u
```

then run this and post output of this command

```
sudo slocate ndiswrapper
```

---

### Post by jimmy_29_75 on 2006-01-30
Hi Lambert, 

Thanks for your reply. Here is the output

jimmy@laptop:~$ cat /proc/version
Linux version 2.6.12-10-386 (buildd@rothera) (gcc version 3.4.5 20050809 (prerel ease) (Ubuntu 3.4.4-6ubuntu8)) #1 Mon Jan 16 17:18:08 UTC 2006

jimmy@laptop:~$ sudo modinfo ndiswrapper
Password:
filename:       /lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
version:        1.1
license:        GPL
vermagic:       2.6.12-10-386 386 gcc-3.4
depends:        usbcore
srcversion:     E21E28A177890611AE46391
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           if_name:Network interface name or template (default: wlan%d) (charp)

jimmy@laptop:~$ sudo slocate -u

sudo slocate ndiswrapper
jimmy@laptop:~$ sudo slocate ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper
/etc/ndiswrapper/modules.ndiswrapper
/var/lib/dpkg/info/ndiswrapper-utils.postinst
/var/lib/dpkg/info/ndiswrapper-utils.list
/var/lib/dpkg/info/ndiswrapper-utils.md5sums
/var/cache/apt/archives/ndiswrapper-utils_1.1-4ubuntu2_i386.deb
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-9-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper
/lib/modules/2.6.12-10-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
/usr/share/doc/ndiswrapper-utils
/usr/share/doc/ndiswrapper-utils/README.Debian
/usr/share/doc/ndiswrapper-utils/README
/usr/share/doc/ndiswrapper-utils/AUTHORS
/usr/share/doc/ndiswrapper-utils/changelog.gz
/usr/share/doc/ndiswrapper-utils/copyright
/usr/share/doc/ndiswrapper-utils/changelog.Debian.gz
/usr/share/man/man8/ndiswrapper.8.gz
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-buginfo
jimmy@laptop:~$

---

### Post by jimmy_29_75 on 2006-01-31
Lambert plz see the outputs and let me know what you think

---

### Post by Lambert on 2006-01-31
I need to get into my breezy partition to check what I have but not near that pc. I do believe you're missing something though, possible a module.h file.

You say you've tried many things, what sort of things have you tried? Anything with trying to compile a newer version of ndiswrapper?

If anybody else has a working ndiswrapper using **v 1.1** if you could run the slocate commands and post here so I can compare would be appreciated.

---

### Post by jimmy_29_75 on 2006-01-31
Hi,

I have tried different drivers only. I have not used any other version of ndiswrapper. As I understand the one I have is ver 1.1. I will look for instructions to update ndiswrapper. If I understand it right Lambert, you want to see slocate from another version of 1.1, am I right? Thanks.

---

### Post by Lambert on 2006-01-31
Yes, from what I've read, the error you get usually comes from someone who compiles ndiswrapper and it basically doesn't install properly or there is already a module that didn't get deleted before the upgrade to a newer ndiswrapper. There might be something else that I'm not aware of as in your case you didn't do anything. It might also be the driver you're using. I believe you can try to remove the driver

sudo ndiswrapper -e (*insert driver name minus the .inf part*)

and then try to modprobe ndiswrapper to see if you get the same error. It won't work as far as getting wireless to work,  it will suggest though if there is a problem with the driver being used if it will modprobe with out the error.

You can try to update to a newer ndiswrapper, there are howtos in the tips and trick section or on the wiki, or you can even look at the ndiswrapper wiki site for instructions. You will just want to make sure you remove ndiswrapper-utils and the module files that came with breezy. 

There's a link on this page about uninstall.

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Main_Page)

---

### Post by jimmy_29_75 on 2006-01-31
Hi Lambert,

This is what I did. Looks like I have never been able to instal any of the drivers I tried. Do you think it might have to do with permissions ! ndiswrapper -l all along came with no drivers installed. I'm looking at how to update /install ndiswrapper. I'm not sure if I really need to do that though !!!

jimmy@laptop:~$ sudo ndiswrapper -e bcmwl5
Password:
Driver bcmwl5 is not installed. Use -l to list installed drivers
jimmy@laptop:~$ modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Operation not permitted
jimmy@laptop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-10-386/kernel/drivers/ne t/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by jimmy_29_75 on 2006-01-31
Hello,

Can anybody guess why I have the error that I keep getting !!!!

---

### Post by bscbrit on 2006-01-31
Shouldn't you be using 'sudo' before each of these commands?

---

### Post by jimmy_29_75 on 2006-01-31
I do use sudo !!! Is a there a particular command that you expect to have that I have not done correctly ?

---

### Post by Lambert on 2006-01-31
I think there's something wrong with your ndiswrapper install.

Open up synaptic from system>administration> and search for ndiswrapper-utils Click on the icon and choose remove completely then apply. After it's done then hit reload to update everything again and then reinstall ndiswrapper-utils

---

### Post by bscbrit on 2006-01-31
Sorry - one of your attempts didn't use sudo but you are correct, you have used it elsewhere.  Are you sure that you haven't already got a driver installed using ndiswrapper.  I had a similar problem when I tried to install the correct driver over a previous incorrect one - similar but perhaps not the same, so I am not sure.  What was the result of running the ndiswrapper -l option to list the installed driver?

---

### Post by robotgeek on 2006-01-31
Sometimes, you might have to install with newer version of ndiswrapper. 

Try with this Howto for the latest version of ndiswrapper:
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

---

### Post by jimmy_29_75 on 2006-01-31
Hi,

After "complete removal, reload and apply" of ndiswrapper utlis, i tried to install the CRrom driver(i copied the fiels to desktop) and here is the output. What else should I try before updating the ndiswrapper. What is the easiest way to do that ???

jimmy@laptop:~$ sudo ndiswrapper -i /Home/Desktop/belkin cd/FILES/DRIVERS/WINXP2 K/BCMWL5.inf
Usage: ndiswrapper OPTION

Manage ndis drivers for ndiswrapper.
-i inffile        Install driver described by 'inffile'
-d devid driver   Use installed 'driver' for 'devid'
-e driver         Remove 'driver'
-l                List installed drivers
-m                Write configuration for modprobe
-hotplug          (Re)Generate hotplug information


where 'devid' is either PCIID or USBID of the form XXXX:XXXX
jimmy@laptop:~$ sudo ndiswrapper -m modprobe config already contains alias directive

jimmy@laptop:~$ sudo ndiswrapper -hotplug jimmy@laptop:~$ sudo ndiswrapper -m
modprobe config already contains alias directive

jimmy@laptop:~$ sudo modprobe ndiswrapper jimmy@laptop:~$ sudo ndiswrapper -l
No drivers installed
jimmy@laptop:~$

---

### Post by Lambert on 2006-01-31
Copy the files from the cd to your hard disk. Make sure you have all of these if they are available.

.inf
.bin
.sys

but make sure you copy only one of each as your cd might have drivers for different windows versions.

so if you have a bcwmlf.inf and bcmwlfa.inf only copy one and include the matching .sys or .bin files.

---

### Post by jimmy_29_75 on 2006-01-31
There is one set of .cat, .inf, .sys files for each OS in separate folders. I choose one of the folders. Other files like .bin, .hdr,.boot,.exe,.ini files not in either of the folders.

---

### Post by jimmy_29_75 on 2006-02-01
Hi,

Does anybody have any idea as to why there is an alias associated. How do I get rid of it. I'm still not sure if it is the driver  or the ndiswrapper problem !! Please see previous threadds for the problem !!!

---

### Post by jimmy_29_75 on 2006-02-01
How do I get rid of the alias. Pleases see the output of previous threads. I think that why I'm not able to install any drivers . Plz help !!

---

### Post by jimmy_29_75 on 2006-02-01
Hi, 

Finally I could see the driver installed. I have no reason how but ndiswrapper -l shows the installed driver and device present. Now I have to connect to 

ESSID (Network Name): UTDALLAS
EAP Type: PEAP (Protected EAP)
Inner EAP Type: EAP-MSCHAPv2 (most clients will not ask for this)

and the server certificate is signed by the RSA Secure Server Certification Authority and is registered to 8021x.utdallas.edu. Do I use ndiswrapper or from Administration>Network. Any clues/suggestions ???

---

### Post by jimmy_29_75 on 2006-02-02
Hi,

I have the above mentioned up and running w/o any encryption. From the forums I have read, I undertand that admin>network>interface file needs to be modified. When I open the interface file I'm not able make any changes to it to enable me to use WEP. Is this the way to do it. I'm new to linux. Please commetn/suggestions !!!!

---

### Post by bscbrit on 2006-02-02
You can only edit the file if you have 'root' permissions, so you will have to use 'sudo' before you invoke any editing commands.

[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

should help explain why

[https://wiki.ubuntu.com/WifiDocs](https://wiki.ubuntu.com/WifiDocs)

should explain how.

---

### Post by jimmy_29_75 on 2006-02-03
BSCBRIT,

thanks for the reply. I will try it out this weekend and let u know. Have been busy lately. cheers, jimmy

---

### Post by bscbrit on 2006-02-03
Jimmy, the bits of the 'interfaces' file that are relevant and work with my Belkin G are as follows:

> 
iface wlan1 inet static      // you might want inet dhcp and then miss the next line...
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1
wireless-essid networkname
wireless-nick computername
wireless-channel 1
wireless-mode managed
wireless-key1 00112233445566778899aabbcc
wireless-defaultkey 1
wireless-keymode open
auto wlan1


You will have to change some values to suit your own network but it should be a good starting point.

---

### Post by PatientZero on 2006-02-03
bscbrit,

You said you had managed to work out the problem with the WEP?

---

### Post by bscbrit on 2006-02-03
Yes I now have working 128 (104) bit  (and 64 (40) bit) WEP and I am currently setting up WAP, which is more secure. My post #27 shows what works for me and this thread:

[http://ubuntuforums.org/showthread.php?t=122382](http://ubuntuforums.org/showthread.php?t=122382)

might also show a few lessons learned along the way.

But I am no expert - what are you seeing as your particular problem?  Have you tried following this thread :

[http://ubuntuforums.org/showthread.php?t=87643](http://ubuntuforums.org/showthread.php?t=87643) ?

---

