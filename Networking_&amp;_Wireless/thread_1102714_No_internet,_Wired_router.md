---
title: "No internet, Wired router?"
date: 2009-03-21
forum: Networking &amp; Wireless
---

### Post by Kyall on 2009-03-21
Hey, Am dual booting both VIsta and Ubuntu. Instalation went smoothly yet for some reason i cant use internet, yet on vista, it is fine. Am new to all of this so feel free to ask any questions.
Cheers in advanced

---

### Post by bigbencg on 2009-03-21
I am pretty green myself, but a starting point would be to give the community some information.  What motherboard are you using?  Do you know your chipsets?

run the command in terminal

```
lspci
```

and post the results, that command will list all devices on the PCI bus and your network controller should be listed.

---

### Post by Kyall on 2009-03-22
Hey
Heres the Info you wanted, i added what i found from "iwconfig" and "ifconfig", seeing that other helpers needed that info, i hope that you can use it.
LSPCS 
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07) 
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07) 
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03) 
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03) 
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03) 
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03) 
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03) 
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93) 
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03) 
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03) 
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03) 
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3650 
01:00.1 Audio device: ATI Technologies Inc RV635 Audio device [Radeon HD 3600 Series] 
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02) 
03:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100 
04:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) 
04:06.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22) 
04:06.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12) 
04:06.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12) 
 
IFconfig 
 
eth0      Link encap:Ethernet  HWaddr 00:1e:33:7b:9d:49   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:427133761 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
          Interrupt:218 Base address:0x4000  
 
lo        Link encap:Local Loopback   
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:480 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:480 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0  
          RX bytes:30080 (30.0 KB)  TX bytes:30080 (30.0 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 00:21:6b:24:36:30   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
wmaster0  Link encap:UNSPEC  HWaddr 00-21-6B-24-36-30-00-00-00-00-00-00-00-00-00-00   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000  
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 
 
Iw Config 
 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
wmaster0  no wireless extensions. 
 
wlan0     IEEE 802.11abgn  ESSID:""   
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated    
          Tx-Power=15 dBm    
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B    
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
 
pan0      no wireless extensions.

---

### Post by helgman on 2009-03-22
So is your router supposed to serve you IP (DHCP) or do you use static IP?

The output from ifconfig shows your wired card (I guess) as eth0. If you know what subnet your on you could try and set an static address and ping your router just to try and pinpoint the problem somewhat.

To set an IP address on eth0 try ```
sudo ifconfig eth0 <IP address> netmask <netmask>
``` (yes, netmask can be left out if you use a classfull network).

If you don't know what subnet your on you can always try to find out by using ```
sudo tcpdump -i eth0
``` and then try to find out what subnet your on by looking at the traffic (just hope that you're not alone on the network).

Or, since you dual boot and networking is up and running in Vista, just boot into Windows and grab the information from there ...

With that information, and the information from previous posts, you might be one step closer to being connected.

Regards,
Helgman

---

### Post by bigbencg on 2009-03-22
Thank you for posting the ifconfig print out as well, it is helpful.  What I see looking at that data, is the ethernet device has been detected and a driver loaded.  It does not appear the driver is functioning properly.  I say that because there are not packets sent or received, but the device is receiving and dropping packets.  The ethernet controller looks at the packets as it receives them, if it determines the packet is not for itself, it drops the packet.  Only packets destined for the controller are logged.  My advice would be to visit the realtek website and download a new driver.

[http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP")

---

### Post by Kyall on 2009-03-23
Hey there
I tried to set an IP address on eth0 as you said, here is what i typed

sudo ifconfig eth0 192.168.1.129 netmask 255.255.255.0
(both of the numbers i got from vista OS)

however it came up with this

SIOCSIFADDR: No buffer space available
SIOCSIFNETMASK: Cannot assign requested address




As for reinstalling the driver, i was held by the fact that i did not know how to install a new driver on a linux OS.
Any instructions to install one, plus with the above  will be greatly appreciated as i am willing to learn.

---

### Post by bigbencg on 2009-03-23
I have never loaded a driver myself, I know there are command line entries.  I downloaded the driver for your device and it has instructions to install the driver.  The driver file is in a package, download it in windows, copy to a thumb driver or drive that can be mounted in ubuntu.  Boot into ubuntu and open the driver package, there should be an application already installed that will extract the files.  Then read the readme.

I have attached the driver file to this post, I had a really hard time downloading it from realtek, the connection kept timing out.

---

### Post by Kyall on 2009-03-24
Hey
Thankyou for getting that driver for me.
I managed to get through half of the installation (removing current, extracting data, creating modules etc, yet when i arive at this next code that i have to enter into the terminal, i get no change and i tried to move on, yet it seems that i need the code to work.

The code was "depmod -a"

the last two codes that i used were "make clean module" and "make install"

If anyone who can help needs info, just ask for it and ill try and help

---

### Post by bigbencg on 2009-03-24
What is the error, I tried the command on my computer and received:
```
bigben@8151-KUBU:~$ depmod -a
FATAL: Could not open /lib/modules/2.6.27-11-generic/modules.dep.temp for writing: Permission denied
```
Which just means the command has to be has to have elevated privelages, or sudo.

---

