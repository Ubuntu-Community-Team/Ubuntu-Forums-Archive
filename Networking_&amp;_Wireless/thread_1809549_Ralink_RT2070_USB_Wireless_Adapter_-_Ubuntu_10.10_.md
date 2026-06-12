---
title: "Ralink RT2070 USB Wireless Adapter - Ubuntu 10.10 Desktop"
date: 2011-07-21
forum: Networking &amp; Wireless
---

### Post by Ograws on 2011-07-21
*DISCLAIMER*
This is my first forum thread post and I am pretty techdumb especially in the field of Linux so I apologise in advanced for my lack of knowledge and vague description of my issues so I am very sorry :D

Okay, first things first I have read this guideline in posting on Wireless and Networking Topic Postings 

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

I cannot however post these descriptions as I do not know how to create those boxes with the Command Lines on them but I will try in the future

I have a Ralink RT2070 USB Wireless Adapter 
I have a desktop computer with a dual boot of Windows 7 and Ubuntu 10.10
I do not know my PCI Card
I do not know about other hardware I should mention so please ask me ''what ..... do you have?'' etc.....
I don't know how to give my system specs on either OS but I will soon

Yes I have gone here to the Ubuntu Wi-Fi Docs page with supported USB Wireless Adapters and so on 

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

I have a Wireless Connection Establishment on my Windows partition but not the Ubuntu :-( Would that have anything to do with the fact Ubuntu does not get the Internet?

I have gone to this page on the Ralink site to see if they have drivers for Linux 

[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)

Which one should I choose because I don't see Ralink RT2070 USB or something near like that

If it isnt supported reccomend a USB Wireless Adapter that is suported in Linux and I might buy it online 

Thanks for reading if you did and ask me questions 

:D

---

### Post by chili555 on 2011-07-21
I think we can solve this pretty easily. We are going to use the terminal, that mysterious black window often with Matrix-like green text, so get ready to get your geek on. We will use it because we get concise information very fast. Anything I put in a code box is a terminal command I'd like you to run and post. Enter the text in the terminal and press Enter. Post the result and we'll use that information to decide what the required driver is and the easiest way to install it.

First, let's list your USB devices; we'll pick out your wireless device and go from there. Please run and post:```
lsusb
```Thanks.

---

### Post by chili555 on 2011-07-21
To put something in a Code box, highlight it and press the hashmark at the top. Please see attached.```
lsusb
```

---

### Post by Ograws on 2011-07-21
Thank you for the reply I understand what Terminal is :-)

i have run that command already I get only two USB ports with devices connected to them

Ralink RT2070 Wireless Adapter is one of them

The other is a mouse

---

### Post by chili555 on 2011-07-21
> Ralink RT2070 Wireless Adapter is one of themWould you please be kind enough to tell us exactly what it says about it? The exact details are what we need. 'Ralink RT2070 Wireless Adapter' is not enough.

---

### Post by Ograws on 2011-07-21
I would be glad :D

It is late where I am so I contact this forum tomorrow is that ok?

---

### Post by chili555 on 2011-07-21
> **Ograws said:**
> I would be glad :D

It is late where I am so I contact this forum tomorrow is that ok?I will be happy to hear from you then.

---

### Post by Ograws on 2011-07-22
If you were me what Terminal Commands would you use to show my hardware info?

I will tell you my diagnosis....

I have the USB Wireless Adapter connected to my desktop computer via USB port (duh!)

I boot up and log into Ubuntu

The Network Applet in the Top Right Hand Corner (in the Gnome 2.6 desktop environment) shows the Network Icon showing no Network Access Points from the Dropdown Menu when I Right-Click. I was expecting to see my Router which is closeby to appear here but i guess.

What would you do if you wanted to configure the Network Settings?

---

### Post by chili555 on 2011-07-22
> If you were me what Terminal Commands would you use to show my hardware info?I thought I pretty well explained that in post #2.> What would you do if you wanted to configure the Network Settings? I'd suspect that you have no working wireless driver and that no available networks are ever going to appear until you do. I'd open the terminal and run and post:```
lsusb
```Then I'd sit back and let Dr. Chili work his magic.

---

### Post by Ograws on 2011-07-22
One of the USB devices connected to my computer is the Ralink RT2070 USB Wireless Adapter
 
Do you know if that is supported or not?

---

### Post by chili555 on 2011-07-22
Ograws-

I have asked you for information about your device three times. Please open a terminal and type in this command:```
lsusb
```Press Enter. Post the result here on this forum. Without more detail, I'm afraid I don't have the answer to your question.

---

### Post by Ograws on 2012-01-09
[B]GOOD NEWS!!!!!

[/B]My USB Wireless Adapter out of the box for me :D:D:D:D:D

All I did was Download an ISO of _[FONT=Book Antiqua][COLOR=Black]ubuntu-desktop-11.10-i386.iso [/COLOR][/FONT]_

[FONT=Arial]As soon as the Live Environment loaded for me a notification popped up and said 

[B]Wireless Networks Detected


[/B]Punched in my WPA2 Encryption Key/Password [/FONT]and BOOM 

[B]Connect Established - You are now online

:popcorn:

[/B]Thank you everyone for your help and have a nice day :)

---

### Post by libertyfelix on 2012-03-05
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 148f:2070 Ralink Technology, Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Now where were we?
 
Ubuntu 10.4, trying to revive a duel cpu 1.4G clunker.
I have the tiny CD which includes linux support folder. But I'm so noob that it isn't clear to me, what and how many files I need to copy and adjust and where do they end up for boot configuration.... ~?

Liberty Felix

---

### Post by libertyfelix on 2012-03-05
libertyfelix@libertyfelix-CQ:~$ sudo iwlist wlan0 scan
[sudo] password for libertyfelix: 
wlan0     No scan results


libertyfelix@libertyfelix-CQ:~$ sudo lshw -c network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5704 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 9
[snip]
resources: irq:25 memory:fc9b0000-fc9bffff memory:fc9a0000-fc9affff memory:fc990000-fc99ffff(prefetchable)
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:e0:4c:90:0f:ed
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bgn

libertyfelix@libertyfelix-CQ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=12 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


apparently the stick is seen  but not 'driven'.

---

### Post by chili555 on 2012-03-05
You probably don't have to do all that. Let's see if conflicting drivers are loaded. Please open a terminal and run:```
lsmod | grep rt2
```The pipe symbol | is on the right side of my US keyboard on the same key with \.

Are both rt2870sta and rt2800usb loaded? Ah! Just as we suspected. Please do:```
sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
```Reboot and let us hear your report.

---

### Post by libertyfelix on 2012-03-05
Hey Chili~! :-)
Thanks for picking this back up. As I guessed, the rt2870 was not installed. I have failed to make heads/tails out of the Ralink disk Linux folder. And so, haven't installed anything yet. I assume you thought Ubuntu would have it already. 

So new the blacklist is in force, deleting both the auto-detect and the hidden wifi manual install sections of the net-manager drop down. 

One confusion has been that the Ralink disk has three folders on the root directory for multiple chipsets. and apparently the RT2770 or RT2870 is called for the hardware which is listed in the PC as RT2070. I can look for the RT2870 online and move it by memory stick. where would it go?

---

### Post by libertyfelix on 2012-03-05
Before:

libertyfelix@libertyfelix-CQ:~$ lsmod | grep rt2
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27573  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb

sudo su
echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
exit
(I'm not sure I did it right...., multiple lines, with a new/intermediate prompt....

libertyfelix@libertyfelix-CQ:~$ sudo su
[sudo] password for libertyfelix: 
root@libertyfelix-CQ:/home/libertyfelix# echo "blacklist rt2800usb" >> /etc/modprobe.d/blacklist.conf
root@libertyfelix-CQ:/home/libertyfelix# exit
exit


After: 

libertyfelix@libertyfelix-CQ:~$ lsmod | grep rt2
rt2800usb              31531  0 
rt2x00usb               9703  1 rt2800usb
rt2x00lib              27573  2 rt2800usb,rt2x00usb
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00usb,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211
crc_ccitt               1339  1 rt2800usb

---

### Post by chili555 on 2012-03-05
> As I guessed, the rt2870 was not installed.Why, I wonder. rt2870sta is included by default in Ubuntu 10.10. Did you do something to remove it? May we see:```
cat /etc/modprobe.d/blacklist.conf
sudo updatedb
locate rt2870sta.ko
```updatedb will take a few moments, please be patient.

After you blacklist the module, it will remain in place until you remove it or reboot. Let's find the elusive rt2870sta before we do anything else.> I can look for the RT2870 online and move it by memory stick. where would it go? It's not that simple. It must be compiled for your kernel and gcc versions specifically.

---

### Post by libertyfelix on 2012-03-05
> **chili555 said:**
> Why, I wonder. rt2870sta is included by default in Ubuntu 10.10. Did you do something to remove it? May we see:```
cat /etc/modprobe.d/blacklist.conf
sudo updatedb
locate rt2870sta.ko
```updatedb will take a few moments, please be patient.

I'm going to reasist, since I only have 10.4. I need the wifi to upgrade to anything higher. Although I am browsing on a Asus Eee PC which had 10.4, but also an internal wifi, and should have upgraded by now. I think it did last night. So, can I transport from the little laptop?


> **chili555 said:**
> 
After you blacklist the module, it will remain in place until you remove it or reboot. Let's find the elusive rt2870sta before we do anything else.It's not that simple. It must be compiled for your kernel and gcc versions specifically.

And there is the rub. I need to learn compiling, architecture and sysop, all at the same time. 
I haven't programmed in 23 years. But I had a minor in Programming/math in the late 80s. Pascal/basic/assemblly.

---

### Post by libertyfelix on 2012-03-05
I just looked and no, i'm still on 10.4. fixing that now.

Ralink starts with this instruction. 

1> $tar -xvzf RT2870_Linux_STA_x.x.x.x.tgz
    go to "./RT2870_Linux_STA_x.x.x.x" directory.

Is that two command line directives or a wrap around? 
Is a file being created? I don't find the original otherwise.

---

### Post by libertyfelix on 2012-03-06
...don't know why. Update manager won't take me up to 10.10. tablet stillat 10.4.

---

### Post by chili555 on 2012-03-06
I don't understand why you resist finding the rt2870sta that's **already on your system** and fixing it up. Why do you think that a compiled vanilla version is going to work better than your built-in? > Is that two command line directives or a wrap around? Two.> Is a file being created? I don't find the original otherwise. Exactly. A folder is being created by un-tar-gzipping the .tgz package.

I repeat: Why do you think that a compiled vanilla version is going to work better than your built-in? I think it's fine to learn to compile. I try to compile from source every day. It's just plain clean fun! However, if you get to the end of the process and it doesn't work for the same un-diagnosed reason that the built-in isn't working, what have you gained? Frustration?

---

### Post by libertyfelix on 2012-03-06
Pardon, Chili, the leap of logic. I only have Ubuntu 10.4, and your statement was that you were sure that 10.10 had the RT2870. 
I'm more than preferring the quickest, least frustrating remedy here. If I have to go read manuals front to end, so be it. Thanks dearly for any patient work around. 

I will execute your search. Incidentally, another thread suggested also blacklisting  rt2x00usb, rt2x00lib. Any thoughts~? 

So, I'm less familiar with file searches on Linux. Should I get an app on my tablet to port over to the PC. ...and then search my Ubuntu disk for the RT2870~? 
What's the next move. 

Here's the location:
locate rt2870sta.ko
/lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/rt2870sta.ko

---

### Post by libertyfelix on 2012-03-06
Did you really want to see my full blacklist~?

ibertyfelix@libertyfelix-CQ:~$ cat /etc/modprobe.d/blacklist.conf
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist rt2800usb

---

### Post by chili555 on 2012-03-06
> locate rt2870sta.ko
/lib/modules/2.6.32-33-generic/kernel/drivers/staging/rt2870/[COLOR="Red"]rt2870sta[/COLOR].ko Excellent! Now let's see if rt2870sta claims and drives your device. If not, we can 'help' it! Please run and post:```
modinfo rt2870sta | grep 2070
```Remember your device is 148f:[COLOR="Red"]2070[/COLOR] Ralink Technology, Corp. If it is claimed, then please do:```
sudo modprobe -rv rt2800usb
sudo modprobe rt2870sta
iwconfig
```Do we have a working wireless interface?

If your device is *not* claimed in 10.04, we'll write two quick files and make it so.

---

### Post by libertyfelix on 2012-03-06
> **chili555 said:**
> Excellent! Now let's see if rt2870sta claims and drives your device. If not, we can 'help' it! Please run and post:```
libertyfelix@libertyfelix-CQ:~$ modinfo rt2870sta | grep 2070
libertyfelix@libertyfelix-CQ:~$ sudo modprobe -rv rt2800usb
[sudo] password for libertyfelix: 
libertyfelix@libertyfelix-CQ:~$ sudo modprobe rt2870sta
libertyfelix@libertyfelix-CQ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.


```Do we have a working wireless interface?

If your device is *not* claimed in 10.04, we'll write two quick files and make it so.

Apparently not yet. I'm looking for wlan0 replacement~?~!~? What's next~?

---

### Post by chili555 on 2012-03-06
> What's next~?Please remove the device and write these files to reflect your usb.id:
```
sudo gedit /etc/udev/rules.d/network_drivers.rules
```

Add one long line:
```
ACTION=="add", SUBSYSTEM=="usb", ATTR{idVendor}=="148f", ATTR{idProduct}=="2070", RUN+="/sbin/modprobe -qba rt2870sta"
```

Proofread twice, save and close gedit.
```
sudo gedit /etc/modprobe.d/network_drivers.conf
```Add one long line:
```
install rt2870sta /sbin/modprobe --ignore-install rt2870sta $CMDLINE_OPTS; /bin/echo "148f 2070" > /sys/bus/usb/drivers/rt2870/new_id
```Proofread twice, save and close gedit. Re-insert the device and run:```
iwconfig
```
Do you now have a wireless interface? Can you click the Network Manager icon and connect?

---

### Post by libertyfelix on 2012-03-06
No change, before or after reboot. 
Note:
both edits appeared to  be on brand new files. So it was not exactly adding text. ...more like establishing originally, text files.
Could we have the location wrong?

---

### Post by libertyfelix on 2012-03-06
My bad~!
...forgot to insert (foot in mouth), I mean, stick in usb. 
It took a minute, but has found and is asking for password.

All hail the Chili Pepper~!

Any idea why my tablet won't upgrade automatically through manager from 10.04 LTS to 10.10~?

---

### Post by chili555 on 2012-03-06
> It took a minute, but has found and is asking for password.
Awesome! Glad it's working!> Any idea why my tablet won't upgrade automatically through manager from 10.04 LTS to 10.10~? No idea. You might ask over on General Help. [http://ubuntuforums.org/forumdisplay.php?f=331](http://ubuntuforums.org/forumdisplay.php?f=331)

I suspect, using my limited knowledge of anything outside networking, that 10.10 is not a LTS release and is obsolete and therefore won't upgrade automagically.

---

### Post by libertyfelix on 2012-03-06
Apparently I have additional issues.
PC's network manager did find 2 wifi feeds, but won't authenticate with the password. It cycles for additional pw attempts. Notes from companion disk suggest WPA or WPA2 incompatibility. Also,  nickname jumps to 3070, another of many references on the multiuse companion disk.

ibertyfelix@libertyfelix-CQ:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     RTxx70 Wireless  ESSID:""  Nickname:"RT3070STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=10/100  Signal level:0 dBm  Noise level:-97 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2012-03-06
Let's check a few more things:```
sudo iwlist wlan0 scan
sudo iwlist wlan0 auth
```'scan' will tell us the encryption on your nearby networks and 'auth' will tell us the card and driver combinations authentication capabilities.

---

### Post by libertyfelix on 2012-03-06
Neither will it connect to a neighboring linksys with no password requirement.

---

### Post by chili555 on 2012-03-06
FYI:```
 modinfo rt2870sta
filename:       /lib/modules/2.6.35-28-generic/kernel/drivers/staging/rt2870/rt2870sta.ko
version:        2.1.0.0
license:        GPL
description:    RT2870/[COLOR="Red"]RT3070[/COLOR] Wireless Lan Linux Driver
author:         Paul Lin <paul_lin@ralinktech.com>
firmware:       rt3071.bin
firmware:       [COLOR="Red"]rt3070[/COLOR].bin
firmware:       rt2870.bin

```Let's also see:```
dmesg | grep -i rt2
```

---

### Post by libertyfelix on 2012-03-06
> **chili555 said:**
> Let's check a few more things:'scan' will tell us the encryption on your nearby networks and 'auth' will tell us the card and driver combinations authentication capabilities.


```

libertyfelix@libertyfelix-CQ:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 7C:03:4C:44:71:9E
                    Protocol:802.11b/g
                    ESSID:"WIN_719F"
                    Mode:Managed
                    Channel:6
                    Quality:100/100  Signal level:-43 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

libertyfelix@libertyfelix-CQ:~$ sudo iwlist wlan0 auth
wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Drop unencrypted : no
          Current Authentication algorithm :
        open

```

---

### Post by chili555 on 2012-03-06
> ESSID:"WIN_719F"Is this your own network? I think it will have a much better chance connecting to a WPA2 only network, not mixed WPA and WPA2 as WIN_719F is set up now. Can you change it?

It looks like the card and driver combo will do WPA2-PSK with no problems.

---

### Post by libertyfelix on 2012-03-06
```
libertyfelix@libertyfelix-CQ:~$ dmesg | grep -i rt2
[  614.091699] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[  614.103181] usbcore: registered new interface driver rt2870
```

The modem-transmitter is from Windstream, and belongs to my hostess where I'm homelessly couch-surfing. Changes may be negotiable. It has a push toggle button saying 'WPS'  next to the 'reset' insert hole. Other than that, no one at SYS Admin level would have a clue about extracting the WPA option. Windstream software is not currently installed. We could eventually get support from them.

---

### Post by chili555 on 2012-03-06
I suggest you leave the WPS button alone; I don't believe we need it. The dmesg listings are remarkably normal. That's good, there are no errors or warnings.

Let's see what Network Manager is doing all this time.```
sudo cat /var/log/syslog | grep etwork | tail -n20
```

---

### Post by libertyfelix on 2012-03-06
libertyfelix@libertyfelix-CQ:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
Mar  8 13:45:18 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar  8 13:45:23 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar  8 13:45:24 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar  8 13:45:32 libertyfelix-CQ NetworkManager: <info>  wlan0: link timed out.
Mar  8 13:45:34 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar  8 13:45:34 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar  8 13:45:34 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar  8 13:45:39 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar  8 13:45:40 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar  8 13:45:47 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Mar  8 13:45:47 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar  8 13:45:47 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Mar  8 13:45:47 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar  8 13:46:02 libertyfelix-CQ NetworkManager: <info>  wlan0: link timed out.
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) failed for access point (WIN_719F)
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  Marking connection 'Auto WIN_719F' invalid.
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) failed.
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar  8 13:47:12 libertyfelix-CQ NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

---

### Post by chili555 on 2012-03-06
While I continue my research, please check to be sure that only rt2870sta and *not* rt2800 or rt2x00 are loaded:```
lsmod | grep rt2
```Let's see what firmware version is being loaded:```
dmesg | grep firmware
md5sum /lib/firmware/rt2870.bin
```

---

### Post by libertyfelix on 2012-03-07
Oh well, Chili. I just cannot keep things simple. For the sake of comparison, I have loaded another hardware piece which is a wifi PCI card. It had the same type of documentation as the usb Ralink, and is itself Ralink ready for Windows installation. (RT2561/RT61) The PCI card wifi was never as strong/sensitive as the usb stick in Windows environment. 

This is with the usb taken out:

libertyfelix@libertyfelix-CQ:~$ dmesg | grep -i rt2
[   12.061875] rt61pci 0000:01:06.0: firmware: requesting rt2561s.bin

And with both in:

libertyfelix@libertyfelix-CQ:~$ dmesg | grep -i rt2
[   12.061875] rt61pci 0000:01:06.0: firmware: requesting rt2561s.bin
[15014.720856] rt2870sta: module is from the staging directory, the quality is unknown, you have been warned.
[15014.732900] usbcore: registered new interface driver rt2870


libertyfelix@libertyfelix-CQ:~$ lspci
[snip]
01:06.0 Network controller: RaLink RT2561/RT61 802.11g PCI
[snip]


Even though I've confused things with a second chip.... Here is with the PCI card RT2561:
(Note that it gets a step further than the usb, with a 4-way handshake, before disconnect.)

libertyfelix@libertyfelix-CQ:~$ sudo cat /var/log/syslog | grep etwork | tail -n20
[sudo] password for libertyfelix: 
Mar  9 15:00:55 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> disconnected
Mar  9 15:00:55 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Mar  9 15:00:56 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Mar  9 15:00:56 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> associated
Mar  9 15:00:56 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Mar  9 15:01:05 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> disconnected
Mar  9 15:01:05 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  disconnected -> scanning
Mar  9 15:01:06 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  scanning -> associating
Mar  9 15:01:06 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  associating -> associated
Mar  9 15:01:06 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  associated -> 4-way handshake
Mar  9 15:01:09 libertyfelix-CQ NetworkManager: <info>  Activation (wlan1/wireless): association took too long.
Mar  9 15:01:09 libertyfelix-CQ NetworkManager: <info>  (wlan1): device state change: 5 -> 6 (reason 0)
Mar  9 15:01:09 libertyfelix-CQ NetworkManager: <info>  Activation (wlan1/wireless): asking for new secrets
Mar  9 15:01:09 libertyfelix-CQ NetworkManager: <info>  (wlan1): supplicant connection state:  4-way handshake -> disconnected
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  (wlan1): device state change: 6 -> 9 (reason 7)
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  Activation (wlan1) failed for access point (WIN_719F)
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  Marking connection 'Auto WIN_719F' invalid.
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  Activation (wlan1) failed.
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  (wlan1): device state change: 9 -> 3 (reason 0)
Mar  9 15:01:14 libertyfelix-CQ NetworkManager: <info>  (wlan1): deactivating device (reason: 0).

libertyfelix@libertyfelix-CQ:~$ lsmod | grep rt2
rt2x00pci               5995  1 rt61pci
rt2x00lib              27573  2 rt61pci,rt2x00pci
led_class               2864  1 rt2x00lib
mac80211              205402  2 rt2x00pci,rt2x00lib
cfg80211              126144  2 rt2x00lib,mac80211


libertyfelix@libertyfelix-CQ:~$ dmesg | grep firmware
[   16.568552] tg3 0000:02:09.0: firmware: requesting tigon/tg3_tso.bin
[   16.648838] tg3 0000:02:09.1: firmware: requesting tigon/tg3_tso.bin
[   16.724673] rt61pci 0000:01:06.0: firmware: requesting rt2561s.bin


libertyfelix@libertyfelix-CQ:~$ md5sum /lib/firmware/rt2870.bin
e4b60f5bb4980a26cbac32be690451d6  /lib/firmware/rt2870.bin
libertyfelix@libertyfelix-CQ:~$ md5sum /lib/firmware/rt2561.bin
99bce75086ea635a2f8288d9b835f787  /lib/firmware/rt2561.bin



Here's another thread which I would consider your spin in regards to pre-compile modification of WPA stuff.
[http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html](http://www.cyberciti.biz/tips/linux-install-rt2870-chipset-based-usb-wireless-adapter.html) 

With both in, the Network Manager shows duplicate incidents of the WIN_719F source I'm trying to connect to. Neither finishes with a good connect.

---

### Post by chili555 on 2012-03-07
> With both in, the Network Manager shows duplicate incidents of the WIN_719F source I'm trying to connect to. Neither finishes with a good connect.This is like trying to do two heart operations at once or drive two cars at once. It's insane to try. How can you tell whick one is performing poorly or well? How can you tell if one is interfering with the other? I'd suggest you pick one or the other. I await your decision.

Whatever one you de-select needs to be locked up till we are solved.

Should it be the 2070, here is a tool we may need.

---

### Post by libertyfelix on 2012-03-08
Thanks Chili,
Of course the RT2561 has  been banished,.. only after trying multiple comparisons.

And while I might not be finding relevant anecdotes, it s interesting that I have similar trouble on Recovery patched OEM WinXPPro units, which more quickly isolate their problems as "unable to contact your DHCP server" issues....Even though the Ralink configuration software clearly shows connection to the  Network signal. ...sounds very similar to my Ubuntu build behavior. 

[https://forums.virtualbox.org/viewtopic.php?f=6&t=37402](https://forums.virtualbox.org/viewtopic.php?f=6&t=37402)

---

### Post by chili555 on 2012-03-08
Let's try newer firmware. Download the file attached to your desktop. Right-click it and select *Extract Here*. Now open a terminal and back up the old firmware:```
sudo mv /lib/firmware/rt2870.bin /lib/firmware/rt2870.bak
```Now copy over the newer firmware:```
sudo cp Desktop/rt2870.bin /lib/firmware
```Now check the md5sum (aka 128-bit checksum):```
md5sum /lib/firmware/rt2870.bin
```If all went well, it will be:> 2bb89af3a7d446deb4695c9a3daa7f9d  /lib/firmware/rt2870.binNow unload and reload the driver to grab the newer firmware:```
sudo modprobe -r rt2870sta
sudo modprobe rt2870sta
```Will it connect now?

---

### Post by libertyfelix on 2012-03-11
Hi Chili,
Sorry for the delay. Workbench had to be shared with a Windows XP project.

Firmware was updated and gave a good error check.

Still no connection. The Network Manager icon sees the router, seeks authentication, and then cycles back to give another window called 'Authentication required  by wireless network'. The wireless security field  box is still limited with one choice, WPA & WPA2 Personal. 
However, in the management setup routine it offers other choices, still excluding WPA alone and WPA2 alone.

The only other optional field seems to be Ad Hoc versus Infrastructure. I think the secondary PCI drivers are not in conflict since it was removed. What other reports should I run now?

---

### Post by chili555 on 2012-03-11
> However, in the management setup routine it offers other choices, still excluding WPA alone and WPA2 alone.Do you mean in the router or in Network Manager? I meant in the router.

I'd like to see:```
sudo iwlist wlan0 scan
lsmod | grep rt2
sudo cat /var/log/syslog | grep -e etwork -e rt2
```Thanks.

---

### Post by libertyfelix on 2012-03-12
Here you go Chili,
Looks interesting.


libertyfelix@libertyfelix-CQ:~$ 
libertyfelix@libertyfelix-CQ:~$ sudo iwlist wlan0 scan
[sudo] password for libertyfelix: 
wlan0     Scan completed :
          Cell 01 - Address: 7C:03:4C:44:71:9E
                    Protocol:802.11b/g
                    ESSID:"WIN_719F"
                    Mode:Managed
                    Channel:11
                    Quality:100/100  Signal level:-47 dBm  Noise level:-97 dBm
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

libertyfelix@libertyfelix-CQ:~$ lsmod | grep rt2
rt2870sta             461843  1 
libertyfelix@libertyfelix-CQ:~$ sudo cat /var/log/syslog | grep -e etwork -e rt2Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 6 -> 4 (reason 0)
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 4 -> 5 (reason 0)
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0/wireless): connection 'Auto WIN_719F' has security, and secrets exist.  No new secrets needed.
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Config: added 'ssid' value 'WIN_719F'
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Config: added 'scan_ssid' value '1'
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Config: added 'key_mgmt' value 'WPA-PSK'
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Config: added 'psk' value '<omitted>'
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: nm_setting_802_1x_get_pkcs11_engine_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: nm_setting_802_1x_get_pkcs11_module_path: assertion `NM_IS_SETTING_802_1X (setting)' failed
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  Config: set interface ap_scan to 1
Mar 14 13:32:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 13:32:41 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
Mar 14 13:32:41 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 13:32:51 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar 14 13:32:51 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 13:32:51 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 14 13:32:56 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar 14 13:32:56 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 13:33:06 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar 14 13:33:06 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 13:33:06 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 14 13:33:11 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar 14 13:33:11 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 13:33:21 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar 14 13:33:21 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 13:33:21 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 14 13:33:22 libertyfelix-CQ NetworkManager: <info>  wlan0: link timed out.
Mar 14 13:33:26 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar 14 13:33:26 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 13:33:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> disconnected
Mar 14 13:33:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
Mar 14 13:33:36 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
Mar 14 13:33:37 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Mar 14 13:33:37 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 5 -> 6 (reason 0)
Mar 14 13:33:37 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0/wireless): asking for new secrets
Mar 14 13:33:41 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Mar 14 13:33:41 libertyfelix-CQ NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 6 -> 9 (reason 7)
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) failed for access point (WIN_719F)
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  Marking connection 'Auto WIN_719F' invalid.
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  Activation (wlan0) failed.
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Mar 14 13:33:47 libertyfelix-CQ NetworkManager: <info>  (wlan0): deactivating device (reason: 0).

---

### Post by chili555 on 2012-03-12
As I said previously:> Is this your own network? I think it will have a much better chance connecting to a WPA2 only network, not mixed WPA and WPA2 as WIN_719F is set up now. Can you change it?Your scan says:> wlan0 Scan completed :
Cell 01 - Address: 7C:03:4C:44:71:9E
Protocol:802.11b/g
ESSID:"WIN_719F"
Mode:Managed
Channel:11
Quality:100/100 Signal level:-47 dBm Noise level:-97 dBm
Encryption keyn
Bit Rates:54 Mb/s
[COLOR="Red"]IE: WPA Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
[COLOR="Red"]IE: IEEE 802.11i/WPA2 Version 1[/COLOR]
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSKCan you change it?

I know, I know: it ought to work either way, but it simply won't. It is a simple fact that some things in Ubuntu and Linux work better than Windows and some worse. We can fight it and complain and not connect or we can adapt and hope the next releases of both Windows *and* Ubuntu are a little better. In my eleven years with Linux, they always are.

---

### Post by libertyfelix on 2012-03-12
I have no idea if I can change it or not. I shared the cost of the router with m;y hostess. It is both sold by and DSL distributed by Windstream who haven't been much help. No management software is used or required. How would I approach such a change?

---

### Post by chili555 on 2012-03-12
First, you should ask and get clear permission from your hostess. Second, on the computer you are answering these posts from, check the network details and look for the gateway. It will likely be something like 192.168.1.1 or 192.168.0.1; I have also seen 192.168.1.254. Plug that into a browser address bar and see if you can get into the administration pages of the router.

You may need to know a password. You can almost always find it by Googling the brand and model of the router.

Then look under Wireless Security and change to WPA2 only.

Please see attached. Note that my router is set to WPA2 Personal and not WPA2 Personal Mixed.

Be sure to Apply and Save before you quit the administration pages of the router.

---

### Post by libertyfelix on 2012-03-12
As I said, You are the pepper, Mr. Chili~!

Windstream has reset us at WPA2-PSK only. My dialog boxes do not show that change. But I am now connected~! 

Thanks again. You've given me a template for several lessons of further study~!

---

### Post by chili555 on 2012-03-12
> But I am now connected~!Awesome! I am glad it's working. Have fun!

---

