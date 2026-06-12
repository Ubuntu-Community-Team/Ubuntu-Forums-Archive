---
title: "Installing B43 legacy drivers in Xubuntu"
date: 2013-01-30
forum: Networking &amp; Wireless
---

### Post by D0wnp0ur on 2013-01-30
I'm new to Linux and I found out that after my installation of Xubuntu 12.04, my wireless card was not being detected by Xubuntu. I found out that there are some drivers that I need to install in order for my wireless card to be detected. I found out that my type of card requires a b43legacy driver. I am wondering how to install these drivers and also where to get the exact file(s). I have also heard that if I am connected via ethernet cable, I can simply install "additional drivers". Is this true?

---

### Post by fantab on 2013-01-30
Yes, if you have ethernet cable or any other internet for that matter you can install "additional drivers". I would recommend that you search this forum for b43 issues, a lots of related issues have been addressed before. 

Also you might find more info [**here**]("http://linuxwireless.org/en/users/Drivers/b43#Supported_devices").

---

### Post by Bucky Ball on 2013-01-30
[I]Thread moved to [B]Networking & Wireless

[/B][/I]Welcome to the forums. Please provide the output of:

```
sudo lshw -C network

```If there is nothing in  Additional Drivers (which is already there and looks for available drivers, you don't need to install Additional Drivers but the drivers it finds) get online with a cable and try installing b43-fwcutter and firmware-b43legacy-installer which can be found in Synaptics then restart.

If that doesn't work, try uninstalling firmware-b43legacy-installer and installing firmware-b43-installer. We'll know more when you provide the output I've asked for.

---

### Post by D0wnp0ur on 2013-01-30
*-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5702X Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:0d:56:df:df:52
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 66MHz
       capabilities: pcix pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5702-v2.25 ip=192.168.0.17 latency=64 link=yes mingnt=64 multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:11 memory:faff0000-faffffff
  *-network:1
       description: Network controller
       product: BCM4306 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=wl latency=32
       resources: irq:5 memory:fafee000-fafeffff

This is what came up. I have tried installing additional drivers and it gave me STA Proprietary Driver, I clicked activate and it started installing, after a minute or sol the screen went black and information popped up, not sure what it said. Nothing happened for a while and the only way to exit was to power off the computer. Back in Xubuntu I clicked on additional drivers once again and there were no drivers detected this time.

---

### Post by D0wnp0ur on 2013-01-30
Update: I reinstalled Xubuntu altogether and immediately went to Additional Drivers, where I proceeded to activate the STA driver. Once again near the end of the installation the black screen with the words on it came up, it did not look like an error message at all but there was no way I could get out of the screen or finish the installation. I then used this command: sudo apt-get install firmware-b43legacy-installer, which worked, but when I go to Additional Drivers, nothing pops up for me to install. I'm really confused as to what I'm supposed to do.

This is what I ran: 
ashton@Ashton-Latitude-D600:~$ sudo apt-get install firmware-b43legacy-installer[sudo] password for ashton: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43legacy-installer
0 upgraded, 2 newly installed, 0 to remove and 230 not upgraded.
Need to get 21.9 kB of archives.
After this operation, 109 kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/main b43-fwcutter i386 1:015-9 [18.9 kB]
Get:2 [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) precise/multiverse firmware-b43legacy-installer all 1:015-9 [3,000 B]
Fetched 21.9 kB in 0s (54.3 kB/s)                  
Selecting previously unselected package b43-fwcutter.
(Reading database ... 128224 files and directories currently installed.)
Unpacking b43-fwcutter (from .../b43-fwcutter_1%3a015-9_i386.deb) ...
Selecting previously unselected package firmware-b43legacy-installer.
Unpacking firmware-b43legacy-installer (from .../firmware-b43legacy-installer_1%3a015-9_all.deb) ...
Processing triggers for man-db ...
Setting up b43-fwcutter (1:015-9) ...
Setting up firmware-b43legacy-installer (1:015-9) ...
No chroot environment found. Starting normal installation
--2013-01-30 15:13:51--  [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
Resolving downloads.openwrt.org (downloads.openwrt.org)... 78.24.191.177
Connecting to downloads.openwrt.org (downloads.openwrt.org)|78.24.191.177|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 652866 (638K) [application/octet-stream]
Saving to: `wl_apsta-3.130.20.0.o'

100%[======================================>] 652,866      400K/s   in 1.6s    

2013-01-30 15:13:58 (400 KB/s) - `wl_apsta-3.130.20.0.o' saved [652866/652866]

This file is recognised as:
  filename   :  wl_apsta.o
  version    :  295.14
  MD5        :  e08665c5c5b66beb9c3b2dd54aa80cb3
Extracting b43legacy/ucode2.fw
Extracting b43legacy/ucode4.fw
Extracting b43legacy/ucode5.fw
Extracting b43legacy/ucode11.fw
Extracting b43legacy/pcm4.fw
Extracting b43legacy/pcm5.fw
Extracting b43legacy/a0g0bsinitvals2.fw
Extracting b43legacy/b0g0bsinitvals5.fw
Extracting b43legacy/a0g0initvals5.fw
Extracting b43legacy/a0g1bsinitvals5.fw
Extracting b43legacy/a0g0initvals2.fw
Extracting b43legacy/a0g1initvals5.fw
Extracting b43legacy/b0g0bsinitvals2.fw
Extracting b43legacy/b0g0initvals5.fw
Extracting b43legacy/b0g0initvals2.fw
Extracting b43legacy/a0g0bsinitvals5.fw

---

### Post by DuckHook on 2013-01-30
The STA driver will not work with your broadcom chip and, in fact, must be blacklisted so that it doesn't capture the system resources needed by b43legacy. The BCM4306 chip is frankly a royal pain in the neck. I have a couple of old laptops that use this chip and must go through the same-old-same-old for every install. To do the following, you must be connected by ethernet cable. These steps will not work without a wired connection. These steps must be done in order and to completion. Skipping any step will gum up the works and require that you start over from the beginning.

1. bring up "additional drivers" and disable the *sta* driver. Your *b43 legacy* driver cannot be installed that way.

2. do:
```
echo "blacklist sta" | sudo tee -a /etc/modprobe.d/blacklist.conf
```3. Then:
```
echo "blacklist wl" | sudo tee -a /etc/modprobe.d/blacklist.conf
```These two steps will blacklist competing incompatible drivers.

4. Then open synaptic package manager and search for *bcm*. Mark every already checkmarked box and tag for removal. Apply.

5. Reboot

6. Do:
```
lspci -vvnn | grep 14e4
```7. The output will consist of one or two network cards, depending on whether your wired ethernet card is also a broadcom. We are not interested in the wired card. Look instead for the reference that contains BCM4306. The important number in this reference are the four digits immediately following "14ef:" If they are any of:
```
14e4:4301
14e4:4306
14e4:4320
14e4:4324
```then we must install b43legacy. If they are anything else, then we must install b43 (not legacy).

8. Run synaptic again. Search using *bcm*. Check the box "b43-fwcutter" for installation. Then, based on the results from step #7, check either firmware-b43-installer or firmware-b43legacy-installer for installation. Do *not* check both. You must choose one or the other based on the results from step #7.

9. Reboot

10. To check, do:
```
lsmod | grep b43
```This should return a nubmer of lines showing the b43 and variants are now residing as kernel modules.

11. To check that sta and wl are no longer gumming up the works, do:
```
lsmod | grep -w sta | grep -w wl
```This should return nothing. Your wireless should now be working. If not post back to this forum and we will try more troubleshooting.

---

### Post by Bucky Ball on 2013-01-30
You also need to insall b43-fwcutter.

---

### Post by DuckHook on 2013-01-30
Yes you do. I mentioned that as part of step #8.

---

### Post by DuckHook on 2013-01-30
<begin rant>
What I don't understand is why we have to go through this arcane wand-waving procedure for equipment that is still prevalent and in rather common use. There must be dozens if not hundreds of threads in this forum alone wrestling with this stupid chip. You'd think that Ubuntu could autodetect for the chipset and recommend the proper driver installation. The steps are right there in the help site, yet cannot be automated in the driver install? It doesn't make sense.
<end rant>
Had to get it off my chest.

---

### Post by Bucky Ball on 2013-01-30
> **DuckHook said:**
> <begin rant>
What I don't understand is why we have to go through this arcane wand-waving procedure for equipment that is still prevalent and in rather common use. There must be dozens if not hundreds of threads in this forum alone wrestling with this stupid chip. You'd think that Ubuntu could autodetect for the chipset and recommend the proper driver installation. The steps are right there in the help site, yet cannot be automated in the driver install? It doesn't make sense.
<end rant>
Had to get it off my chest.

While I understand your frustration, this belongs in ***Communtity Cafe ***or another non-support forum, not here. Off topic. You might find in future updates this chip will be easier to install and software included with the kernel.

There is nothing stopping you, or anyone else, from patching this all together and forwarding it for inclusion in an attempt to make it happen. Without you voicing your concerns in the correct places it can only be considered a rant, adds nothing to the OPs solution and is in no way constructive. From the Code of Conduct:

> **Thread Drifting/Steering:** Please keep discussions on topic.  Topics that do not belong in the technical or 3rd party project sections  belong in the Cafe, if they fit the posted rules in the Cafe.If you have complaints, direct them to the right place(s) else you achieve nothing. Thanks. This might be a start:

[http://brainstorm.ubuntu.com/ideas_in_preparation/](http://brainstorm.ubuntu.com/ideas_in_preparation/)

There is a button on the right to submit your idea ...

---

### Post by DuckHook on 2013-01-31
> **Bucky Ball said:**
> From the Code of Conduct:

If you have complaints, direct them to the right place(s) else you achieve nothing.

Of course, you are right. Apologies to all for misplaced rant.

---

### Post by JohnnyShotgun on 2013-02-05
DuckHook,

I have the same problem as OP.  I did what you advised I have received this at step #8 (two separate text boxes)

"Please insert the disk labeled:
Xubuntu 12.04.1 LTS _Precise Pangolin_ - Release amd64 (20120817.3)
in drive /cdrom/


Some of the packages could not be retrieved from the server(s).
Do you want to continue, ignoring these packages?"

HELP PLEASE?

---

### Post by DuckHook on 2013-02-05
I suspect that in Software Sources>Other Software, you have CD-ROM checked (meaning that you want the system to check every time the CD-ROM from which you installed) and at the same time, you don't have Ubuntu Software>multiverse checked. Try turning off the CD-Rom and turning on multiverse, then going through step 8 again. Multiverse is strung out to be "Software restricted by copyright or legal issues (multiverse)" on my versions of Ubuntu. The "Software Sources" dialogue box can be found in Update Manager>Settings.

---

### Post by JohnnyShotgun on 2013-02-05
Thank You Thank You!  This solved my problem!  For some unknown reason, there was 4 CDROMs that I had to uncheck (?).  

DuckHook, thank you for the quick response to my PM.

---

### Post by DuckHook on 2013-02-05
Glad to help. I see you are new to the forum so, welcome to the community. Despite my earlier rant, it's a great OS and an even greater worldwide movement. Hope you end up enjoying Linux as much as I do.

---

### Post by Bucky Ball on 2013-02-06
> **DuckHook said:**
> I see you are new to the forum so, welcome to the community. Despite my earlier rant, it's a great OS and an even greater worldwide movement. Hope you end up enjoying Linux as much as I do.

+1. Welcome aboard. Enjoy the OS, the learning curve and the forums. Any quesions, just ask.

---

