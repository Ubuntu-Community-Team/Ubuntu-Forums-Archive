---
title: "Help please"
date: 2009-03-20
forum: Networking &amp; Wireless
---

### Post by Sanus Compleo on 2009-03-20
Well guys, I'm pulling my hair out.  Turns out that messing with partitions gives you a currupted hard drive.  Fortunately, that decided my question on weither or not to switch to Ubuntu full time.  Unfortunately, that wiped out the last several months of... well everything.  I'm rather stressing things now.  Anyway, got ubuntu up, no problem, used the whole hard-drive, and opened up firefox.  Guess what didn't happen?  What didn't happen, is I didn't get to log into the internet at all.  Oh, no problem, just have to log onto the wireless network!  typed in the ssid, turned off security on the router, logged in with the SSID and security set to: none.  Nothing happened for some odd reason.  Running Broadcom BMC4309 or something along those linse, I probably need that ndiswrapper or w/e it is, but I can't get it because my laptop has no internet access.  can't log in with a wired connection because while it had windows it shut off that network card, and was unable to turn it back on.  Dell calls this a "feature".  anyway, what's my next step?  I want internet, and I have none.  please tell me how I can get some internet.  It would be well appreciated.

EDIT: Using 8.10, and Dell Inspiron 600m laptop.

---

### Post by lisati on 2009-03-20
Sorry to hear of your unfortunate experience. It's always a good idea to make sure you have backups before tinkering with partitions.

 There are data recovery programs available, but the names elude me at the moment.

---

### Post by Sanus Compleo on 2009-03-20
What's happened has happened, even if it could be recovered it would take me moe money than the data was worth :P  And more money that I had, of course :P.

Edit: At least I still have gimp :D

Edit2: :O  The Gimp windows actually work in Ubuntu!  If you don't know what I'm talking about, try to use gimp in windows ;)

---

### Post by markdjones82 on 2009-03-20
So, the wired ethernet got disabled in windows and you say you can't enable it?  Seems odd to me.  It shouldn't be hardware dependant and you should be able to enable it in the bios or something.

Does network manager recognize your wireless network when it scans?

---

### Post by Sanus Compleo on 2009-03-20
Er...  Scan?  It just gives me options to type in the ssid manually... nothing about scanning in here so far.

Update: Had to reset the computer because I somehow inverted all of the colours on everything when I got frustrated with the AI on connect four.  When it came back on it showed that there were driver updates for the broadcom card, but couldn't download them because there's no internet -_-.  I wonder how it detected them though...  Anyway, I can burn ONE SINGLE CD and get whatever I need from this computer onto the laptop, SO LONG as it's the exact right thing that will at least get the internet up and running, weither it be the broadcom bmc43xx driver or the ndiswrapper thing, can somebody tell me which exactly I need and where exactly I can get them?  It's not that I don't want to find them myself, it's just that I don't trust myself to find the right ones.

---

### Post by ugm6hr on 2009-03-20
In order to ensure we give accurate advice, please see my Wifi help? link below and answer as many questions as you can.

You can use Cut / Paste to a USB stick to save outputs from commands.

---

### Post by Sanus Compleo on 2009-03-20
Unfortunately, I don't have a USB stick at the time, though I'd like to.  But I'm pretty good at manual copying.

The router is a Netgear WGR614, v9 software, with G compatability?  Whatever G means >.>


00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller # 1 (rev 01)
00:1d.1 Same as above, except controller # 2
00:1d.2 Same as above, except controller # 3
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (Ich4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 02)
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet (rev 01)
02:01.0 CardBus bridge: 02 Micro, Inc. OZ711EC1 SmartCardBus Controller (rev 20)
02:01.1 Same as above.
02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

lsusb comes out with this:
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Ouch... This one's a long one.

 *-network:0
         description: Ethernet interface
         product: NetXtreme BCM5705M Gigabit Ethernet
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:02:00.0
         logical name: eth0
         version: 01
         serioal: 00:11:43:3d:20:10
         width: 64 bits
         clock: 66MHz
         capabilities: bus_master cap_list ethernet physical
         configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5705-v3.16 latency=32 mingnt=64 module=tg3 multicast=yes
   *-network:1
          description: Network controller
          product: BCM4309 802.11a/b/g
          vendor: Broadcom Corporation
          physical id: 3
          bus info: pci@0000:02:03.0
          version: 03
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master
          configuration: driver=b43-pci-bridge latency=32 module=ssb
   *-network:0 DISABLED (Typist's note: Whaaaaa???)
          description: Wireless interface
          physical id: 1
          logical name: wlan0
          serial: 00:11:f5:09:f3:5d
          capabilities: ethernet physical wireless
          configuration: broadcast=yes multiclass=yes wireless=IEEE 802.11bg
   *-network:1 DISABLED
          description: Ethernet interface
          physical id: 2
          logical name: pan0
          serial: ee:fe:5c:f6:14:35
          capabilities: ethernet physical
          configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

Again, I'm typing this, so there might be very very slight typos here and there, but I've gotten pretty good at typing... so... Here's to hoping :D

Next part...
Oh, er... Running Ubuntu 8.10

Can't get online with my laptop using any method
Using secondary windows pc, which is hooked through a wired line to the Netgear router, which connects to a wowway modem.  It's in the family room.

eth0      Link encap:Ethernet  HWaddr 00:11:43:3d:20:10
             UP BROADCAST MULTICAST  MTU:1500  Metric:1
             RX packets:0 errors:0 dropped:0 overruns:0 frame:0
             TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:1000
             RX bytes:0 (0.0 B)   TX bytes:0 (0.0 B)

lo          Link encap:Local Loopback
             inet addr:127.0.0.1 Mask:255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric: 1
             RX packets:240 errors:0 dropped:0 overruns:0 frame:0
             TX packets:240 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueuelen:0
             RX bytes:15040 (15.0 KB)   TX bytes: 15040 (15.0 KB)

iwconfig now...

lo            no wireless extensions.

eth0         no wireless extensions

wmaster0 no wireless extensions

wlan0       IEEE 802.11bg  ESSID:""
                Mode:Managed  Frequency:2.412 GHz   Access Point: Not-Associated
                Tx-Power=0 dBm
                Retry min limit:7   RTS thr:off   Fragment thr=2352 B
                Power Management:off
                Link Quality:0   Signal level:0  Noise level:0
                Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
                Tx excessive retries:0  Invalid misc:0   Missed beacon:0
	
pan0         no wireless extensions.

Hrm... Your lack of wireless extensions disturbs me...

route -n comes out with this
Kernel IP routing table
Destination    Gateway          Genmask         Flags Metric Ref     Use Iface

pinging gets network unreachable, and unknown host.

Not dual booting with windows, it got broke half way.  Note to users who wish to dual boot: NEVER SKIP A CHCKDISK!!!

---

### Post by ugm6hr on 2009-03-20
This shows how to install the b43 driver without internet.

[http://ubuntuforums.org/showthread.php?p=6028741#post6028741](http://ubuntuforums.org/showthread.php?p=6028741#post6028741)

There are 3 files to download (remember to get the correct 32- vs 64-bit (or just download everything and sort it out after).

Ref: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) (BCM4309 compatibility)

---

### Post by Sanus Compleo on 2009-03-20
I'm a bit confused here.  Normally I'd gun through it and try whatever as I go, but I only have one shot to go through.  I'm at the "Downloading Firmware" part, and my best estimate is that I need to download something (Not exactly sure what) burn it to the CD, put the CD in the laptop, and do something else with it.  So yeah, I'm confused and don't trust myself to try to do it on my own at the moment, I'd rather not mess my stuff up worse x.x

---

### Post by ugm6hr on 2009-03-20
Download the files first:

[http://packages.ubuntu.com/intrepid/amd64/b43-fwcutter/download](http://packages.ubuntu.com/intrepid/amd64/b43-fwcutter/download)
[http://packages.ubuntu.com/intrepid/i386/b43-fwcutter/download](http://packages.ubuntu.com/intrepid/i386/b43-fwcutter/download)
[http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
[http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2](http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2)

Copy files to CD

Boot into Ubuntu.

Copy files to "Home Folder" (/home/username)

Open Terminal
Either 64-bit:
```
sudo dpkg -i b43-fwcutter_011-4ubuntu1_amd64.deb
```

Or 32-bit:
```
sudo dpkg -i b43-fwcutter_011-4ubuntu1_i386.deb
```

Then:
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o
tar xfvj broadcom-wl-4.150.10.5.tar.bz2
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o
sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy
sudo ifconfig wlan0 up
sudo /etc/init.d/networking restart
```

Hopefully that should work.

Good luck.

---

### Post by Sanus Compleo on 2009-03-20
\\:D/\\:D/\\:D/\\:D/\\:D/

Guess where I'm typing this from?  Go ahead guess.  Did you guess?  Well if you guessed "From his laptop with Ubuntu 8.10" you would have guessed right!  :D.  I am so happy to have a working computer again.  Not only that, but a working computer with Ubuntu!  :D.  Such joy, such excitement.  So many new things to figure out.  So much stuff to mess with.  Thank you to everybody who posted in the thread, you guys here at Ubuntuforums.org really are beautiful and shiny :D.

---

### Post by ugm6hr on 2009-03-21
Welcome to the (online) community :)

Glad it turned out to be pretty easy!

---

### Post by freonchill on 2009-04-26
dont mean to steal the thread,

but i just installed jaunty on by dell d800 laptop
and i have a dell 1400 wifi card (BCM4309 802.11a/b/g [14e4:4324])

it shows up, but isnt working in network manager for wireless (e.g. it shows that wireless is there, but there arent any ap's to connect to)

so i tired the list of commands above, and i have a wlan0 now (where before i didnt)

is there something i need to do to get network manager to use wlan0 for wifi over wmaster-00?

or should i give up on network manager and use wicd for this card in jaunty?

thanks,

---

