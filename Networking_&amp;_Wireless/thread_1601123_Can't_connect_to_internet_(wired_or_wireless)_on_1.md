---
title: "Can't connect to internet (wired or wireless) on 10.10 Maverick"
date: 2010-10-19
forum: Networking &amp; Wireless
---

### Post by nullflux on 2010-10-19
Hello!

I've had Ubuntu installed on my laptop for around 7 months, starting with 9.10, then upgrading to 10.04 and 10.10 when they were released. I've never had issues connecting to the internet before but now I seem to have lost it. 

I'm dual-booting Windows Vista and Ubuntu 10.10 on an ASUS G71Gx. I was able to connect to my wifi (no security) and access the internet just two days ago but I lost it yesterday. At first I thought it was just my ISP, but now my desktop running Windows XP (ethernet) and my desktop running Ubuntu 10.04 (using a USB wifi adapter) have full internet connections. My laptop can connect to the router and I can access the config page (192.168.1.1), but I can't reach any other web sites or even other machines connected to my router. This happens with **both wireless and wired.**

If anyone can help I would gladly appreciate it! I'm willing to run any commands and post the output or give any additional information. I really would like this fixed soon.

Thanks in advance!

---

### Post by guiwegian on 2010-11-13
HI,
I have got a similar issue here.
I have noticed that I can connect to the access point, but when I start Chrome or Firefox, Pidgin, they couldnt connect to the Internet. However, the updates are working perfectly.
So I decided to start Firefox as sudo and here we are, the problem is sorted.
The only thing is, how do I change the rights of my account, knowing that it has never been restricted? What should I do?
It is not really handy to have to launch all the application as sudo

Regards

Guillaume

---

### Post by uncaspi on 2010-11-13
Try the OpenDNS nameservers. Click network icon and then edit the connections select DNS and give the ip's to OpenDNS

---

### Post by guiwegian on 2010-11-13
> **uncaspi said:**
> Try the OpenDNS nameservers. Click network icon and then edit the connections select DNS and give the ip's to OpenDNS

I don't see how it will fix his problem, he has no issue running Internet via Windows, it is obvious that the problem comes from Ubuntu

---

### Post by baldurmen on 2010-12-30
Well, I've got the same problem ( looks like it ).. If someone could complete the thread... would be extremely appreciated!

---

### Post by PatchesTheCaveman on 2010-12-31
Hi baldurmen!  Sorry you're having trouble accessing the Internet wirelessly.

To try and figure out what's going on, I'm going to have you collect some information.  To do so, you'll need to go to Applications > Accessories > Terminal.  In the black box that appears, type the following and press Enter:
```
lspci -v
```
Then, copy and paste that in a post here.  That lists your hardware and the drivers installed and activated for them.

Then, type this and press Enter:
```
ifconfig -a
```
and copy/paste that too.  That's your network configuration.

Next, type this and press Enter:
```
sudo iwconfig
```
You'll need to enter your password when asked and press Enter.  Then copy/paste that too.  That shows us your wireless setup.

Just one more thing.   Type this and press Enter:
```
uname -r
```
and copy/paste that (this one's only one line).  That tells us what version of the Linux kernel you're running.  One particular version is giving people trouble.

With all that in hand, we should be able to figure out what's going on.  Thanks!

(And if anyone else in this thread is still around, feel free to reply with all that also.)

---

### Post by baldurmen on 2010-12-31
ok just wait a little, i'm using 2 computers, so i'll have to usb copy paste the results

---

### Post by baldurmen on 2010-12-31
There it goes ( and thanks for the help!):

/1

00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, fast devsel, latency 0  
 	Memory at ec000000 (32-bit, prefetchable) [size=64M]  
 	Capabilities: <access denied>  
 	Kernel driver in use: agpgart-intel  
 	Kernel modules: intel-agp  
 

 00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01) (prog-if 00 [VGA controller])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, fast devsel, latency 0, IRQ 16  
 	Memory at f0000000 (32-bit, prefetchable) [size=128M]  
 	Memory at e8000000 (32-bit, non-prefetchable) [size=512K]  
 	Expansion ROM at <unassigned> [disabled]  
 	Capabilities: <access denied>  
 	Kernel driver in use: i915  
 	Kernel modules: i915  
 

 00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01) (prog-if 00 [UHCI])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 16  
 	I/O ports at 1800 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01) (prog-if 00 [UHCI])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 19  
 	I/O ports at 1820 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01) (prog-if 00 [UHCI])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 18  
 	I/O ports at 1840 [size=32]  
 	Kernel driver in use: uhci_hcd  
 

 00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01) (prog-if 20 [EHCI])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 23  
 	Memory at e8080000 (32-bit, non-prefetchable) [size=1K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: ehci_hcd  
 

 00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81) (prog-if 00 [Normal decode])  
 	Flags: bus master, fast devsel, latency 0  
 	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32  
 	I/O behind bridge: 00002000-00002fff  
 	Memory behind bridge: e8100000-e81fffff  
 	Kernel modules: shpchp  
 

 00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)  
 	Flags: bus master, medium devsel, latency 0  
 	Kernel modules: iTCO_wdt, intel-rng  
 

 00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01) (prog-if 8a [Master SecP PriP])  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 18  
 	I/O ports at 01f0 [size=8]  
 	I/O ports at 03f4 [size=1]  
 	I/O ports at 0170 [size=8]  
 	I/O ports at 0374 [size=1]  
 	I/O ports at 1860 [size=16]  
 	Memory at 50000000 (32-bit, non-prefetchable) [size=1K]  
 	Kernel driver in use: ata_piix  
 

 00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: medium devsel, IRQ 9  
 	I/O ports at 1880 [size=32]  
 	Kernel modules: i2c-i801  
 

 00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 0, IRQ 17  
 	I/O ports at 1c00 [size=256]  
 	I/O ports at 18c0 [size=64]  
 	Memory at e8080c00 (32-bit, non-prefetchable) [size=512]  
 	Memory at e8080800 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: <access denied>  
 	Kernel driver in use: Intel ICH  
 	Kernel modules: snd-intel8x0  
 

 02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)  
 	Subsystem: Trigem Computer Inc. Device 3189  
 	Flags: bus master, medium devsel, latency 64, IRQ 17  
 	I/O ports at 2000 [size=256]  
 	Memory at e8102000 (32-bit, non-prefetchable) [size=256]  
 	Capabilities: <access denied>  
 	Kernel driver in use: 8139too  
 	Kernel modules: 8139too, 8139cp  
 

 02:09.0 Network controller: RaLink RT2500 802.11g (rev 01)  
 	Subsystem: Linksys WMP54G 2.0 PCI Adapter  
 	Flags: bus master, slow devsel, latency 64, IRQ 21  
 	Memory at e8100000 (32-bit, non-prefetchable) [size=8K]  
 	Capabilities: <access denied>  
 	Kernel driver in use: rt2500pci  
 	Kernel modules: rt2500pci  
 

 02:0b.0 Communication controller: Agere Systems LT WinModem (rev 02)  
 	Subsystem: Risq Modular Systems, Inc. Device 044e  
 	Flags: bus master, medium devsel, latency 64, IRQ 3  
 	Memory at e8102400 (32-bit, non-prefetchable) [size=256]  
 	I/O ports at 2800 [size=8]  
 	I/O ports at 2400 [size=256]  
 	Capabilities: <access denied>  
 


/2
eth0      Link encap:Ethernet  HWaddr 00:40:2b:42:9d:be   
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)  
           Interrupt:17 Base address:0x2000  
 

 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0  
           inet6 addr: ::1/128 Scope:Host  
           UP LOOPBACK RUNNING  MTU:16436  Metric:1  
           RX packets:440 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:440 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:0  
           RX bytes:33584 (33.5 KB)  TX bytes:33584 (33.5 KB)  
 

 wlan0     Link encap:Ethernet  HWaddr 00:12:17:8a:bf:e3   
           inet6 addr: fe80::212:17ff:fe8a:bfe3/64 Scope:Link  
           UP BROADCAST MULTICAST  MTU:1500  Metric:1  
           RX packets:160 errors:0 dropped:0 overruns:0 frame:0  
           TX packets:179 errors:0 dropped:0 overruns:0 carrier:0  
           collisions:0 txqueuelen:1000  
           RX bytes:18080 (18.0 KB)  TX bytes:28700 (28.7 KB)  
 


/3
lo        no wireless extensions.  
 

 eth0      no wireless extensions.  
 

 wlan0     IEEE 802.11bg  ESSID:off/any  
           Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated    
           Tx-Power=20 dBm    
           Retry  long limit:7   RTS thr:off   Fragment thr:off  
           Encryption key:off  
           Power Management:off  
 

/4
2.6.35-22-generic

---

### Post by baldurmen on 2010-12-31
XD,  : o (without space) was interpreted as a smiley... sorry

---

### Post by PatchesTheCaveman on 2010-12-31
Is there any way you can plug that computer into a wired Ethernet connection?  There is an updated driver for your wireless card you could download that might help.

If not, I can tell you how to download it on another computer and transfer it with a flash drive, but it will be bit more complicated.

---

### Post by baldurmen on 2010-12-31
Yes i can, but you'll have to guide me through.

---

### Post by baldurmen on 2010-12-31
Ok, internet works fine via ethernet (auto config via eth0)

---

### Post by PatchesTheCaveman on 2010-12-31
Cool.  Open a terminal and run these commands, pressing Enter after each one.
```
sudo apt-get update
sudo apt-get install linux-backports-modules-wireless-maverick-generic
```

Once that's done, reboot.

---

### Post by baldurmen on 2010-12-31
rebooted but still doesn't work... Oh, and I keep getting disconnected by my wireless connection

---

### Post by PatchesTheCaveman on 2010-12-31
Run this command on a terminal:
```
sudo iwconfig wlan0 power off
```

and see if you continue to disconnect.

---

### Post by baldurmen on 2010-12-31
yep

---

### Post by PatchesTheCaveman on 2010-12-31
Run this command and copy and paste what it spits out:
```
dmesg | grep -i rt2500
```

---

### Post by baldurmen on 2010-12-31
[   17.163412] rt2500pci 0000:02:09.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   17.703833] Registered led device: rt2500pci-phy0::radio
[   17.704391] Registered led device: rt2500pci-phy0::quality


You seem to be thinking it's the drivers, ain't it? isn't that type of wifi card common?

---

### Post by PatchesTheCaveman on 2010-12-31
Well if there isn't something wrong with the driver or the config somewhere there's nothing I can do to help you.

It could be the router or the wireless card itself could be FUBAR.  But a little google-fu turned up a possibility.

When you ran iwconfig earlier you were disconnected from the wireless network.  I need you to make sure you are connected to the wireless network, and run this again:
```
sudo iwconfig
```

That'll tell me if it is what I think it is.  If it is it's an easy fix.

---

### Post by baldurmen on 2010-12-31
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BELL069"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:82:FC:0C:64   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/70  Signal level=-42 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I think I was connected on this one... And the card works fine on windows....

If you can't help me, would getting 10.04 be a solution?

---

### Post by PatchesTheCaveman on 2010-12-31
No, it is what I thought it was.  This should fix it.

Run this command:
```
sudo iwconfig wlan0 rate 54M
```

---

### Post by baldurmen on 2010-12-31
Do I have to reboot, because this doesn't seem to work...

And by the way, thanks again for all the help! :D

---

### Post by PatchesTheCaveman on 2010-12-31
I don't think so.  That fixed another guy with the same hardware's connection instantly.

Run ```
sudo iwconfig
``` and see if it took.

Also, did you run it while it was connected to wireless?

---

### Post by baldurmen on 2010-12-31
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BELL069"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:82:FC:0C:64   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


well, I did everything while being connected...

---

### Post by PatchesTheCaveman on 2010-12-31
Try this instead (slightly different from earlier):
```
sudo iwconfig wlan0 rate 11M
```

---

### Post by baldurmen on 2010-12-31
Nope, not better.... sudo iw config , just in case...

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"BELL069"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:26:82:FC:0C:64   
          Bit Rate=11 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by PatchesTheCaveman on 2010-12-31
Bah!  Time to break out the sledgehammer!  

Let's try updating to the absolute latest driver possible from Linus Torvalds & friends.  Run these commands:
```
sudo apt-get install build-essential
wget http://wireless.kernel.org/download/compat-wireless-2.6/compat-wireless-2010-12-26.tar.bz2
tar -jxf compat-wireless-2010-12-26.tar.bz2
cd compat-wireless-2010-12-26
make
sudo make install
sudo make unload
sudo modprobe rt2500pci
```

You might want a somewhat reliable Internet connection for the first two lines but I don't believe the files are big in either case.

---

### Post by baldurmen on 2010-12-31
hahahahaha, this error message shows up! 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package build-essentials

seems Thor has found a rival!

---

### Post by PatchesTheCaveman on 2010-12-31
My bad.  It's ```
sudo apt-get install build-essential
```

---

### Post by baldurmen on 2010-12-31
i executed everything till make, then i get this error: 

baldurmen@baldurmen-DA191A-ABA-514n:~/compat-wireless-2010-12-26$ make
/home/baldurmen/compat-wireless-2010-12-26/config.mk:198: "WARNING: CONFIG_CFG80211_WEXT will be deactivated or not working because kernel was compiled with CONFIG_WIRELESS_EXT=n. Tools using wext interface like iwconfig will not work. To activate it build your kernel e.g. with CONFIG_LIBIPW=m."
make -C /lib/modules/2.6.35-24-generic/build M=/home/baldurmen/compat-wireless-2010-12-26 modules
make: *** /lib/modules/2.6.35-24-generic/build: No such file or directory.  Stop.
make: *** [modules] Error 2

---

### Post by PatchesTheCaveman on 2010-12-31
Run:
```
sudo apt-get install linux-headers-2.6.35-24-generic
```

Then run:
```
make clean
```

Then run make again and go on from there.

---

### Post by baldurmen on 2010-12-31
don't worry, I'm not dead (yet), these commands just takes a hell lot of time to run

---

### Post by PatchesTheCaveman on 2010-12-31
Are you still running make?  There's something you could have done to make it faster, but I didn't want to make it too much more complicated...

I don't remember it taking *this* long last time I had to do it, though. (That was a little less than a year ago, seeing as how this one's almost done with :-).

---

### Post by baldurmen on 2010-12-31
Well, it ain't a top notch computer, and you know what they say about make...''Learning make is like looking into the eyes  of God. Half of the people go insane, the rest of us become programmers  and sysadmins'' XD

---

### Post by baldurmen on 2010-12-31
OK, I finished running the lines you gave me, from what I can see, it ain't working.... I haven't rebooted, but I need some sleep, as the sun' begging risin' here... I'll check on in somewhat 10-so hours.
I haven't given up yep, so think about it!!!!

(and thanks for the patience and the great help!)

---

### Post by PatchesTheCaveman on 2010-12-31
Yeah a reboot might be necessary.  Someone else might have to help you tomorrow.  I'm probably going to be in no condition to be troubleshooting computer issues tomorrow night.  ;-)

---

### Post by baldurmen on 2010-12-31
Indeed... OK just for refreshing the subject, no better after rebooting.

---

### Post by PatchesTheCaveman on 2010-12-31
The only other thing you could try is using the Windows drivers with ndiswrapper.  For a complete HOWTO on how to do that, see:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by baldurmen on 2011-01-01
Well, I'll try that when I'll get in better shape XD. Thanks for all mate!

---

### Post by baldurmen on 2011-01-06
As for my case, finally totally different from the original post, all the drivers were working fine at the beginning. After having played with ndiswrapper for a couple of hours, I found a post saying that older wi-fi PCI cards ( I'm using Linksys Wireless-G PCI Adapter ) aren't WPA2 compatible...

This means I indeed had connection (bitrate, IP), but my card just wouldn't connect, nor ping since it wasn't recognizing the encryption! So I changed my WPA2 key to a WEP one, AND I KILLED WINDOWS!


Le Roy est mort, vive le Roy!
Long live Ubuntu.[B][URL="http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1150490054358&pagename=Linksys%2FCommon%2FVisitorWrapper"]:guitar:
[/URL][/B]

---

### Post by send4m3 on 2011-03-15
Hi all, I have the same problem with my notebook which running Maverick Meerkat. Usually, there is no problem, but suddenly today I can not connect to my router.

I have 2 OS, which the one is Windows XP, and I tried to connect my router with this OS, and got no problem.

Then I tried to boot using my Ubuntu Meerkat, and tried to connect it using direct cable via UTP to my router and again there is no problem.

The problem is always using connection by wireless to my router, which the OSD Notification always said "Connected" but I can't even ping my router IP which is 192.168.1.1 and can not browsing internet either and can not using by browser to see my router config using address 192.168.1.1

This is the result of some command of my machine, and hopefully someone help me, please...

lspci -v
========

00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, fast devsel, latency 0
	Capabilities: <access denied>
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c) (prog-if 00 [VGA controller])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, fast devsel, latency 0, IRQ 45
	Memory at e4600000 (64-bit, non-prefetchable) [size=1M]
	Memory at d0000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4000 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, fast devsel, latency 0
	Memory at e4700000 (64-bit, non-prefetchable) [size=1M]
	Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 16
	I/O ports at 4020 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 17
	I/O ports at 4040 [size=32]
	Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 18
	Memory at e4800000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, fast devsel, latency 0, IRQ 46
	Memory at e4804000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=08, subordinate=08, sec-latency=0
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=10, subordinate=10, sec-latency=0
	I/O behind bridge: 00005000-00005fff
	Memory behind bridge: e4100000-e41fffff
	Prefetchable memory behind bridge: 000000007f800000-000000007f9fffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=18, subordinate=18, sec-latency=0
	I/O behind bridge: 00006000-00006fff
	Memory behind bridge: e4000000-e40fffff
	Prefetchable memory behind bridge: 000000007fa00000-000000007fbfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 03) (prog-if 00 [Normal decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=28, subordinate=28, sec-latency=0
	I/O behind bridge: 00002000-00003fff
	Memory behind bridge: e0000000-e3ffffff
	Prefetchable memory behind bridge: 000000007fc00000-000000007fdfffff
	Capabilities: <access denied>
	Kernel driver in use: pcieport
	Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 20
	I/O ports at 4060 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 21
	I/O ports at 4080 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03) (prog-if 00 [UHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 18
	I/O ports at 40a0 [size=32]
	Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20 [EHCI])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0, IRQ 20
	Memory at e4808000 (32-bit, non-prefetchable) [size=1K]
	Capabilities: <access denied>
	Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01 [Subtractive decode])
	Flags: bus master, fast devsel, latency 0
	Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
	Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, medium devsel, latency 0
	Capabilities: <access denied>
	Kernel modules: iTCO_wdt

00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03) (prog-if 80 [Master])
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
	I/O ports at 01f0 [size=8]
	I/O ports at 03f4 [size=1]
	I/O ports at 0170 [size=8]
	I/O ports at 0374 [size=1]
	I/O ports at 40c0 [size=16]
	I/O ports at 40d0 [size=16]
	Capabilities: <access denied>
	Kernel driver in use: ata_piix

10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
	Subsystem: Hewlett-Packard Company Device 135b
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at e4100000 (32-bit, non-prefetchable) [size=4K]
	Capabilities: <access denied>
	Kernel driver in use: iwl3945
	Kernel modules: iwl3945

18:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
	Subsystem: Hewlett-Packard Company Device 3026
	Flags: bus master, fast devsel, latency 0, IRQ 47
	Memory at e4000000 (64-bit, non-prefetchable) [size=64K]
	Expansion ROM at <ignored> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: tg3
	Kernel modules: tg3




ifconfig -a
===========

eth0      Link encap:Ethernet  HWaddr 00:1f:29:87:72:d9  
          inet6 addr: fe80::21f:29ff:fe87:72d9/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:2904 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2842 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2934269 (2.9 MB)  TX bytes:454518 (454.5 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:833 errors:0 dropped:0 overruns:0 frame:0
          TX packets:833 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70934 (70.9 KB)  TX bytes:70934 (70.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:14:56:a3  
          inet6 addr: fe80::21f:3cff:fe14:56a3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:40513 (40.5 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1f:3c:14:56:a3  
          inet addr:169.254.6.91  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1



sudo iwconfig
=============

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"iCozy"  
          Mode:Ad-Hoc  Frequency:2.412 GHz  Cell: EA:39:B6:63:8B:5C   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Encryption key:7E5B-9745-B26A-C4AC-6384-D556-D8C0-D0EA-C74F-0139-9DF9-DB66-C74F-0139-9DF9-DB66
          Power Management: off


uname -r
========

2.6.35-27-generic

---

### Post by guru_r236 on 2011-03-15
Please also see the thread 
[http://ubuntuforums.org/showthread.php?t=1706906](http://ubuntuforums.org/showthread.php?t=1706906)
Looks like some issue whenever there is a dual OS...

---

