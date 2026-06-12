---
title: "no connection to the internet ever"
date: 2010-03-24
forum: Networking &amp; Wireless
---

### Post by revaew on 2010-03-24
i am a complete ubuntu noob. i got the 9.1 CD thing in the mail and i tried it out. everything is going great except i cannot connect ot the internet. wired or wireless i cant connect. when i plug in the Ethernet cable, the lights in the jack don't even blink.... i downloaded the latest drivers to a flash drive but i need the ndisgtk thing to use it or what ever, but i cant get it because i don't have the internet. i am currently trying this on an acer aspire 5739. i have the intel wireless card thing. and ive tried to hook up directly to the modem, wired through my router and  wirelessly. but nothing seems to work. any help would be appreciated =)

---

### Post by Iowan on 2010-03-24
Check **sudo lshw -C network** (from a terminal) to get more information on your interfaces.

---

### Post by gordintoronto on 2010-03-25
It also might help if you described your computer a little.

I have never seen an Ethernet port which did not work right away, but people I trust tell me it is possible to have one. But they are very rare, and only part of unusual hardware.

---

### Post by amit@nitttrchd.ac.in on 2010-03-25
> **gordintoronto said:**
> It also might help if you described your computer a little.

I have never seen an Ethernet port which did not work right away, but people I trust tell me it is possible to have one. But they are very rare, and only part of unusual hardware.



_____________

Check dns settings given by ISP or proxy server at /etc/resolv.conf
nameserver ip  e.g.
nameserver 4.2.2.1


use ifconfig to chk ip and mii-tool cmd to see ethernet working 

and if its thru dhcp run dhclient cmd

---

### Post by revaew on 2010-03-25
what should i look for when i use those commands and stuff? because i cant copy and paste from the terminal or anything because im currently typing on a windows pc because the one with ubuntu isnt working with internet. so what lines should i be looking for?

---

### Post by davoudi on 2010-03-25
First use wired connection. There are two options available here: 
1) Install linux-backports-modules-karmic using
sudo apt-get install linux-backports-modules-karmic 
and check if anything has changed. You might need to download and install the driver from your network card company.
2) Use ndiswrapper, read here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by revaew on 2010-03-25
> **davoudi said:**
> First use wired connection. There are two options available here: 
1) Install linux-backports-modules-karmic using
sudo apt-get install linux-backports-modules-karmic 
and check if anything has changed. You might need to download and install the driver from your network card company.
[r]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")


how can i do this when my internet doesnt connect?

---

### Post by bkratz on 2010-03-25
> **revaew said:**
> how can i do this when my internet doesnt connect?

I think it is probably more important to determine what your ethernet and wireless cards are before worrying about updating drivers.

In post two above someone asked for you to send the following:

```
sudo lshw -C network
```


If you change this to:

```
sudo lshw -C network > hardware.txt
```

Then you will find a text document in your /home/user directory, in this case hardware.txt , which you can drag-n-drop onto a flash drive and see it in Windows with, IIRC, wordpad

you might also want to post the contents of 

```
lspci
``` 


in a similar manner as the previous.

---

### Post by revaew on 2010-03-25
ok the hardwar.txt is :
 
  *-network
       description: Network controller
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: driver=iwlagn latency=0
       resources: irq:17 memory:be000000-be001fff
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:09:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd cap_list
       configuration: latency=0
       resources: memory:be100000-be13ffff ioport:3000(size=128)


and the lspci content is :
 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Device 0a34 (rev a2)
01:00.1 Audio device: nVidia Corporation Device 0be2 (rev a1)
05:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
09:00.0 Ethernet controller: Attansic Technology Corp. Device 1063 (rev c0)

---

### Post by revaew on 2010-03-26
anybody have any thoughts or ideas as to what to do?

---

### Post by Iowan on 2010-03-26
Neither interface has an alias (logical name), so I wonder about drivers (unfortunately, still a weak area for me...).

---

### Post by revaew on 2010-03-26
oh.... is that what might be the problem? missing drivers?

---

### Post by seenthelite on 2010-03-26
I have the same problem when I try to install 9.10 from a CD I downloaded 2 days after 9.10 released. ( the CD is fine ) In January I tried again same thing so I had a USB ethernet adapter and I used that and when the CD started I saw it was working OK. So during the install I stay connected to the internet and with the 32 bit CD the new kernel is installed and when the CD finishes and prompts for the reboot I remove the USB adapter and then wired and wireless work. If you are using 64 bit you need to leave the USB adapter connected after the reboot and install all the updates and then remove the adapter. (I have 10.04 on the same computer now and it installs fine.)

---

### Post by revaew on 2010-03-26
is there anyway to do it without the usb connector? cuz i dont have one so....

---

### Post by seenthelite on 2010-03-27
> **revaew said:**
> is there anyway to do it without the usb connector? cuz i dont have one so....
  Not that I am aware of, I have the same wireless card that you have and it works out of the box on 9.04 and 10.04 but not 9.10. Maybe you could consider using 9.04 or even 10.04. 10.04 is in Beta 1 for testing but it is better on this computer than 9.10 I have both installed at the moment.

---

### Post by davoudi on 2010-03-27
Do you have access to another computer? You could use sudo apt-get -d packagename to just download the packaged and the repositories. You can then copy everything to a memory stick and install the package on your computer.

---

### Post by revaew on 2010-03-28
Eh I guess I will just try a different version. Thanks for all the help.   = D

---

### Post by chili555 on 2010-03-28
Let's get your Intel wireless going! Please open Applications > Accessories > Terminal and run these commands:```
rfkill list > rfkill.txt
dmesg | grep iwl > iwl.txt
```Transfer the two text documents on a USB key and post them here. Thanks.

---

### Post by revaew on 2010-03-29
ok the iwl is :
 [   87.697135] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[   87.697138] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[   87.697242] iwlagn 0000:05:00.0: enabling device (0000 -> 0002)
[   87.697270] iwlagn 0000:05:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   87.697308] iwlagn 0000:05:00.0: setting latency timer to 64
[   87.697353] iwlagn 0000:05:00.0: Detected Intel Wireless WiFi Link 5100AGN REV=0xEFB7D7FF
[   87.848796] iwlagn 0000:05:00.0: Failed, HW not ready
[   87.848831] iwlagn 0000:05:00.0: PCI INT A disabled



and the rfkill is :

0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by chili555 on 2010-03-29
Wow! You are the holder of an official Ubuntu bug!

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/418933?comments=all)

If you look down to post #82, you will see that a rather famous guy is working on it for you; Linus Torvalds, the original author of the Linux kernel. When you need help, you get help!

Reading through the bug reports there and here: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407824](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/407824)  seem to suggest that by the most current kernel version, 2.6.31-20, this should be fixed. Others suggest a patched kernel here: [http://people.canonical.com/~apw/lp418933-karmic/](http://people.canonical.com/~apw/lp418933-karmic/)

Others suggest the 2.6.32 Lucid kernel and even others suggest a GRUB parameter.

My first suggestion is to determine which kernel version you have and if it's not 2.6.31-20, download the most current version on a USB key and install it. Reboot and see if your problem is fixed. What is your current kernel version?```
uname -r
```

---

### Post by chili555 on 2010-03-29
Be sure to get 32- or 64-bit version as needed. 

[http://packages.ubuntu.com/karmic-updates/any/linux-image-2.6.31-20-generic](http://packages.ubuntu.com/karmic-updates/any/linux-image-2.6.31-20-generic)

---

### Post by revaew on 2010-03-29
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed


^^^^ it says that.... what does this mean?

---

### Post by chili555 on 2010-03-29
> it says that.... what does this mean?The meta package makes sure that you get upgrades correctly. I am quite sure you already have it! Find out with:```
dpkg -l | grep linux-generic
```Does it say 'ii' meaning installed?

However, you can't get upgrades with the kernel you have. Our first attempt at a fix is the newest kernel. If we get on line with either ethernet or wireless, updates will take care of themselves.

If you decide to install it, do:```
cd Desktop  [COLOR="Red"]<--or wherever you dropped the file[/COLOR]
sudo dpkg -i linux-image*
```

---

### Post by revaew on 2010-03-29
it does say "ii". so thats a start. uhm, i do want to install so my internet will work;). but the ```
cd Desktop  [COLOR=Red]<--or wherever you dropped the file[/COLOR]
sudo dpkg -i linux-image*
```what would i put if i am just going to plop the package on the desktop?

---

### Post by chili555 on 2010-03-29
> what would i put if i am just going to plop the package on the desktop?Perfect!!```
cd Desktop
sudo dpkg -i linux-image*
```

---

### Post by revaew on 2010-03-29
```
cd desktop
```
ia that something i am supposed to type into the terminal?
be cause  i get "bash: cd: desktop: No such file or directory"

---

### Post by chili555 on 2010-03-29
[COLOR="Red"]D[/COLOR]esktop...not desktop.

---

### Post by bake130 on 2010-03-29
im also having a problem with my internet connection. i have a hp pavilion dv5z-1000 laptop and it has an anthols(sp) wireless card and i just down loaded xutunbu 9.1 on to my computer. now my computer wont recognize my wireless card. well not fully it sees the wireless networks but it wont let me turn my wireless to connect to them. any ideas?

---

### Post by chili555 on 2010-03-29
> **bake130 said:**
> im also having a problem with my internet connection. i have a hp pavilion dv5z-1000 laptop and it has an anthols(sp) wireless card and i just down loaded xutunbu 9.1 on to my computer. now my computer wont recognize my wireless card. well not fully it sees the wireless networks but it wont let me turn my wireless to connect to them. any ideas?
Please start a new thread and post:```
lsmod | grep ath
```Thanks.

---

