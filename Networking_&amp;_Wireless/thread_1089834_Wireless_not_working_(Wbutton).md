---
title: "Wireless not working (Wbutton?)"
date: 2009-03-07
forum: Networking &amp; Wireless
---

### Post by thrikulam on 2009-03-07
I've been researching this for over a week, and am getting pretty frustrated :).

I am aware that there are guides on how to get Ubuntu to recognize your wireless card, but as far as I am aware, they only work if your Wi-Fi is *enabled*. There is a program that I have in Windows to enable my Wi-Fi, called wbutton.exe, but this program doesn't work in Linux under Wine.

Does anyone have a remedy to my nightmare? I have a  Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02) Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10) wireless card, if that helps. I have tried ndiswrapper as well, but again, it can't help much if my Wi-Fi isn't enable, right?

Also, I do not have an Acer PC, as most other people have (who have this issue). I'm not sure if the methods they use for their computers will work for mine. So at the risk of being sent to other threads, I was hoping someone would baby me through this process. :)

---

### Post by ugm6hr on 2009-03-07
Do you mean you have to manually enable your wifi in Windows every time you reboot?

What happens if you shutdown Windows with it enabled and reboot?

What about switching users?

Do you have a hardware switch on the outside, or a keyboard shortcut to enable?

Check the wifi help link below; specifically the point about Windows power-saving.

You probably don't need ndiswrapper - the b43 driver in Intrepid should work.

---

### Post by thrikulam on 2009-03-07
**Do you mean you have to manually enable your wifi in Windows every time you reboot? **
Yes.

**What happens if you shutdown Windows with it enabled and reboot?**
It will not enable until it hits Windows.

**What about switching users? **
What about it? I am confused by this question. I don't have multiple user accounts, and I would assume I would have to enable wireless the same as I usually would.
[B]
Do you have a hardware switch on the outside, or a keyboard shortcut to enable?[/B]
Keyboard shortcut. It's a specific wireless button on my keyboard, which links to the program [wbutton.exe]("http://www.sendspace.com/file/ur8g1q") (uploaded to SendSpace).
[B]
You probably don't need ndiswrapper - the b43 driver in Intrepid should work.[/B]
I've recently come to that conclusion, and I've tried to reinstall bcm43xx-fwcutter, but I'm not sure if that was successful. At the very least, it's not showing up in the Drivers section as it once used to.


**1. How were you trying to get online? e.g. dial-up, USB-wired ADSL modem, ethernet-wired ADSL modem, ethernet-wired ADSL modem-router, wireless router / modem-router, 3G-mobile internet etc.**
WiFi

**2. What hardware are you using? The brand & model number (perhaps with a link to an online manual) for your adapters, modems, routers etc. You can generally identify external components from their labeling, and internal components from within an Operating System already installed (e.g. Windows or Ubuntu).**
If you go to [http://www.newegg.com/product/product.aspx?Item=N82E16834228002](http://www.newegg.com/product/product.aspx?Item=N82E16834228002) and hit the Specifications tab on your left, it will tell you everything about my computer.

More specifically, here are my network adapters:

[IMG]http://i44.tinypic.com/33wmi3q.png[/IMG]

**3. Who is your Internet Service Provider (and in which country)?**
Springnet, USA (I'm getting access from my college)

**4. Which version of Ubuntu are you using? e.g. Ubuntu 8.04, Xubuntu 7.10 etc and 32- vs 64-bit.**
Ubuntu 8.10, 32-bit

**5. Can you get online with any other method? e.g. if you have a wifi problem, can you connect with ethernet?**
Yes, I usually connect with an ethernet cord. Using an ethernet cord, I can connect to the internet in both Windows and Linux. My WiFi only works in Windows.

**6. How are you getting online to post on this forum?**
Right now, using my WiFi through Windows.

**7. Include the output from the following commands from Terminal (all case sensitive). They help identify your hardware, so provide further detail to potential helpers. If necessary, just copy and paste the text into a text file and upload from a different computer.**

thrik@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
02:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
02:09.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
02:09.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
thrik@ubuntu:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
thrik@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ae:3a:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 56:c9:49:0b:8d:20
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
thrik@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ae:3a:7c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:746 errors:0 dropped:0 overruns:0 frame:0
          TX packets:746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:57096 (57.0 KB)  TX bytes:57096 (57.0 KB)

thrik@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

thrik@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
thrik@ubuntu:~$ ping -c 3 208.67.219.101
connect: Network is unreachable
thrik@ubuntu:~$ ping -c 3 [www.opendns.com](www.opendns.com)
ping: unknown host [www.opendns.com](www.opendns.com)

**8. For wifi - what encryption are you using? Have you tried an open network?**
Not really doing much of that at the moment, since it doesn't work. I would be using an open network, however.

**9. Do you dual-boot with Windows?**
Yes, and I've just now taken care of this issue.

It seems, at the moment, that my wireless is not even set up in Ubuntu. I was messing around with settings before in attempt to get something working. I'm awaiting your instruction on this issue, since I'm afraid of blowing something up :)

---

### Post by ugm6hr on 2009-03-08
Do you have any settings in BIOS relating to wifi?

Once the XP power-saving issue is sorted, it should default enabled, which lshw appears to suggest.

It is worth installing the b43 driver, since the BCM4318 is supported.  Also, remove ndiswrapper.

Connect with wired internet in Ubuntu, and do the following:

```
sudo apt-get remove ndiswrapper-common
sudo apt-get install b43-fwcutter
```

Then reboot.

How to do it with no internet:
[http://ubuntuforums.org/showpost.php?p=6028741&postcount=4](http://ubuntuforums.org/showpost.php?p=6028741&postcount=4)

---

### Post by thrikulam on 2009-03-08
**Do you have any settings in BIOS relating to wifi?**
Yes, and I already have it enabled by default.

**Once the XP power-saving issue is sorted, it should default enabled, which lshw appears to suggest.**
I'll run lshw again:

thrik@ubuntu:~$ lshw -class network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 5
       bus info: pci@0000:02:05.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 module=ssb
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:02:07.0
       logical name: eth0
       version: 10
       serial: 00:0a:e4:ae:3a:7c
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=10.210.2.252 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a4:44:cb:9b
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:0a:1b:0b:0b:69
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

[B]It is worth installing the b43 driver, since the BCM4318 is supported.  Also, remove ndiswrapper.

Connect with wired internet in Ubuntu, and do the following:

```
sudo apt-get remove ndiswrapper-common
sudo apt-get install b43-fwcutter
```

Then reboot.[/B]
Done and done.






:\ Still not working... I don't have access to wireless here, but I'm assuming my wireless light would come on if it were to work. That's what wbutton.exe does in Windows, it just toggles my wireless on and off.

---

### Post by ugm6hr on 2009-03-08
> **thrikulam said:**
>  but I'm assuming my wireless light would come on if it were to work. 

Not necessarily.  There is no way to check unless you have an access point.

Presumably the b43-fwcutter command correctly located, downloaded and installed the b43 driver?

---

### Post by thrikulam on 2009-03-08
> **ugm6hr said:**
> Not necessarily.  There is no way to check unless you have an access point.

Presumably the b43-fwcutter command correctly located, downloaded and installed the b43 driver?

Alright, I'll go check and post back here.

---

### Post by ugm6hr on 2009-03-08
> **thrikulam said:**
> Alright, I'll go check and post back here.

Try the keyboard shortcut too.

---

### Post by thrikulam on 2009-03-08
Yeah, no dice. The keyboard shortcut never works in Linux, but if it did, it would just run wbutton.

Although, as I am currently in Windows, I went over to the folder where wbutton is located. I noticed a [WmiAcpi.dll]("http://www.sendspace.com/file/tm6umo") file that I didn't notice before, I'm not sure if this would help solve anything.

Also, to answer your question from before, b43-fwcutter correctly installed. It took some doing, because I had blacklisted it before, but it now shows up in the third-party drivers section, activated.

---

### Post by ugm6hr on 2009-03-08
I'm afraid I don't really know how else to help.

You probably need help from someone with similar hardware.

Nevertheless, I did find a few links that may or may not prove useful:
[http://www.zwobbl.de/2007/11/05/fsam7400-rfsam-are-obsolete/](http://www.zwobbl.de/2007/11/05/fsam7400-rfsam-are-obsolete/)
[http://rfswitch.sourceforge.net/?page=laptop_matrix](http://rfswitch.sourceforge.net/?page=laptop_matrix)
[http://legolas558.iragan.com/index.php?option=content&pcontent=1&task=view&id=34&Itemid=91&-fsam7400](http://legolas558.iragan.com/index.php?option=content&pcontent=1&task=view&id=34&Itemid=91&-fsam7400)
[https://bugs.launchpad.net/ubuntu/+bug/48547](https://bugs.launchpad.net/ubuntu/+bug/48547)

I would start by ensuring that your BIOS is fully updated; hopefully a new BIOS will remove the software switch.

---

### Post by thrikulam on 2009-03-08
ugm6hr, I'll try those links that you provided. Thank you for trying, it's appreciated. :)

Right now, I have another issue: my Wubi crapped out. It's giving me busybox errors, as it usually does (like a week after installation). I'm going to now perform a real install of Ubuntu, and after that, I'll try to fix my wireless again.

Hopefully something that I find out will help you too, Simyager :)

---

### Post by thrikulam on 2009-03-09
You HAVE to be joking me.

TWO LINES OF CODE.

```
modprobe acerhk
echo 1 > /proc/driver/acerhk/wirelessled
```

That's all it took. -_-

It was in the second [link]("http://rfswitch.sourceforge.net/?page=laptop_matrix") you provided, ugm6hr, so thank you muchly. :)

*SOLVED*

---

### Post by ugm6hr on 2009-03-09
Wow.

It's easy when you know how, isn't it?

Well done for solving, and welcome to the community full-time.

---

### Post by thrikulam on 2009-03-09
This is slightly off-topic, but do you know of a way to get that code to boot with Ubuntu? It's not a big deal, but it'd be nice :)

---

### Post by ugm6hr on 2009-03-09
I am no expert with scripting, but it should be possible.

I suspect that you could create a script with those 2 lines, then add that script to the autostarted applications list.

If no one more experienced gives the answer, I'll try looking it up.

---

### Post by sadnub on 2009-03-09
I got my Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless card to work with this method. At first it didnt work right, so i went into the bios and had to enable it. THen booted it up and works perfectly fine. Im actually replying to this thread with wireless internet. Btw, I have the card installed in a dell latitude D610 if it tells you anything. Thanks for the help!

---

