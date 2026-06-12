---
title: "RT2860 Problems on 64 bit"
date: 2011-03-29
forum: Networking &amp; Wireless
---

### Post by Kewbla on 2011-03-29
Hello, I wanted to stop hi jacking the work around thread.
I'm running Kubuntu 64 bit

I started by following this walk through
[http://ubuntuforums.org/showpost.php?p=9951781&postcount=3](http://ubuntuforums.org/showpost.php?p=9951781&postcount=3)

everything is fine until i get to Step 5 this line :

sudo ifconfig wlan0 down (on some hardware it is ra0)

I receive this output: 

wlan0: ERROR while getting interface flags: No such device (tried the ra0 as well)

I started browsing other threads to see what else could be happening. 
I ran this line :  sudo lshw -C network

with an output of:
 *-network:0 UNCLAIMED   
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:ff500000-ff50ffff
  *-network:1
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:8b:93:dd
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A ip=192.168.0.155 latency=32 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10MB/s
       resources: irq:20 memory:ff510000-ff510fff ioport:bc00(size=64)


So my wireless card hasn't been claimed by the driver.  How can i get the driver to claim the card?

thanks,
joel








[FONT=monospace]
[/FONT]

---

### Post by chili555 on 2011-03-29
Please post:```
lspci -nn
lsmod | grep rt2
```Let's see where you are so far.

---

### Post by Kewbla on 2011-03-29
ok first command:

joel@ubuntu:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub [8086:2580] (rev 04)
00:01.0 PCI bridge [0604]: Intel Corporation 82915G/P/GV/GL/PL/910GL PCI Express Root Port [8086:2581] (rev 04)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller [8086:2582] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller [8086:2668] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 [8086:2660] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 [8086:2662] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 [8086:2664] (rev 03)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 [8086:2666] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 [8086:2658] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 [8086:2659] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 [8086:265a] (rev 03)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 [8086:265b] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller [8086:265c] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev d3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge [8086:2640] (rev 03)
00:1f.1 IDE interface [0101]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller [8086:266f] (rev 03)
00:1f.2 IDE interface [0101]: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller [8086:2651] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller [8086:266a] (rev 03)
06:00.0 Network controller [0280]: RaLink Device [1814:3060]
06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 01)

lsmod | grep rt2 is giving me no output in the terminal

---

### Post by chili555 on 2011-03-29
I am doubtful that rt2860sta is the correct driver for your device. Please let me see:```
modinfo rt2860sta | grep 3060
```

---

### Post by Kewbla on 2011-03-29
that command gave no output in the console. (this should have shown something no?)

 i'm using a d-link DWA-525 wireless N-150 card

---

### Post by chili555 on 2011-03-29
There would be no output if the driver does not claim your pci.id:> 06:00.0 Network controller [0280]: RaLink Device [1814:[COLOR="Red"]3060[/COLOR]]Sadly, you have gone to the trouble to compile a driver that is not correct for your device.

The somewhat suspect rt2800pci claims your device. ```
$ modinfo rt2800pci | grep 3060
alias:          pci:v0000[COLOR="Red"]1814[/COLOR]d0000[COLOR="Red"]3060[/COLOR]sv*sd*bc*sc*i*

```Let's try it:```
sudo modprobe rt2800pci
iwconfig
```Any improvement?

---

### Post by Kewbla on 2011-03-29
i was mucking about with the blacklist and had blacklisted the 2800pci and i did get some life out of my card.....it can scan and connect to the net but is highly unreliable 

joel@ubuntu:~$ sudo modprobe rt2800pci
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.


joel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA

---

### Post by chili555 on 2011-03-29
ra0??? Let's see what's driving the card.```
lsmod | grep -e rt2 -e rt3 -e ndis
```Thanks.

---

### Post by Kewbla on 2011-03-29
joel@ubuntu:~$ lsmod | grep -e rt2 -e rt3 -e ndis

rt2800pci              10528  0 
rt2800lib              32002  1 rt2800pci
rt2x00usb              11316  1 rt2800lib
rt2x00pci               6993  1 rt2800pci
crc_ccitt               1699  1 rt2800pci
rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
led_class               3393  1 rt2x00lib
mac80211              267099  3 rt2x00usb,rt2x00pci,rt2x00lib
cfg80211              170485  2 rt2x00lib,mac80211
eeprom_93cx6            1789  1 rt2800pci
rt3562sta             973418  0

---

### Post by chili555 on 2011-03-29
Ahh! rt3562sta is trying to drive it. I think that's correct. Please post:```
dmesg | grep rt3
```Thanks.

---

### Post by Kewbla on 2011-03-29
i have lost my  internet totally from that computer.....i don't know what i did . 

re ran some commands hers the outputs

 joel@ubuntu:~$ iwconfig
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  wlan0     IEEE 802.11bgn  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            
  joel@ubuntu:~$ lsmod | grep -e rt2 -e rt3 -e ndis
  rt3562sta             973418  0
  rt2800pci              10528  0
  rt2800lib              32002  1 rt2800pci
  rt2x00usb              11316  1 rt2800lib
  rt2x00pci               6993  1 rt2800pci
  crc_ccitt               1699  1 rt2800pci
  rt2x00lib              31575  4 rt2800pci,rt2800lib,rt2x00usb,rt2x00pci
  led_class               3393  1 rt2x00lib
  mac80211              267099  3 rt2x00usb,rt2x00pci,rt2x00lib
  cfg80211              170485  2 rt2x00lib,mac80211
  eeprom_93cx6            1789  1 rt2800pci
  joel@ubuntu:~$ dmesg | grep rt3

---

### Post by chili555 on 2011-03-29
Let's remove rt2800pci and its dependencies and concentrate on rt3562sta.```
sudo ifconfig wlan0 down
sudo rmmod -f rt2800pci
sudo rmmod -f rt2800lib
sudo rmmod -f rt2x00pci
sudo rmmod -f rt2x00lib
```If they don't remove cleanly, that is, without complaint or errors in the terminal, please reboot.

Next, let's clean up your blacklists:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by Kewbla on 2011-03-29
joel@ubuntu:~$ sudo ifconfig wlan0 down
  [sudo] password for joel:
  joel@ubuntu:~$ sudo rmmod -f rt2800pci
  joel@ubuntu:~$ sudo rmmod -f rt2800lib
  joel@ubuntu:~$ sudo rmmod -f rt2x00pci
  joel@ubuntu:~$ sudo rmmod -f rt2x00lib
  ERROR: Removing 'rt2x00lib': Resource temporarily unavailable

 joel@ubuntu:~$ cat /etc/modprobe.d/blacklist
  blacklist bcm43xx
  blacklist b43
  blacklist b43legacy
  blacklist ssb
  joel@ubuntu:~$ cat /etc/modprobe.d/blacklist.conf
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
   
  #wireless black listing

---

### Post by chili555 on 2011-03-29
And so you rebooted?```
iwconfig
lsmod | grep rt3
```

---

### Post by Kewbla on 2011-03-29
rebooted

 joel@ubuntu:~$ sudo rmmod -f rt2x00lib
  [sudo] password for joel:
  ERROR: Removing 'rt2x00lib': Resource temporarily unavailable
  joel@ubuntu:~$ iwconfig
  lo        no wireless extensions.
   
  eth0      no wireless extensions.
   
  wlan0     IEEE 802.11bgn  ESSID:off/any  
            Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
            Retry  long limit:7   RTS thr:off   Fragment thr:off
            Power Management:off
            
  joel@ubuntu:~$ lsmod |grep rt3
  rt3562sta             973418  0
  joel@ubuntu:~$

---

### Post by chili555 on 2011-03-29
> **Kewbla said:**
> i didn't due to   ERROR: Removing 'rt2x00lib': Resource temporarily unavailable
But that's what I asked you to do.
> If they don't remove cleanly, that is, without complaint or errors in the terminal, please reboot.
The file named 'blacklist' without conf, has to do with Broadcom wireless drivers, which, unless I'm missing something, you don't have. Let's remove it completely:```
sudo rm /etc/modprobe.d/blacklist
```Also, in your blacklist.conf file, I don't find the rt2800pci lines. ```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add the following at the end:```
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00pci
blacklist rt2x00lib
```Proofread, save and close gedit. Reboot.

Now is your wireless working?

---

### Post by Kewbla on 2011-03-29
i mis-read the reboot directive if there was a failed rm. sorry :)

the cards light is flashing on boot up. once the desktop loads knetwork manager doesn't load automatically to mange the wireless connection. once i stat that manually i can scan all networks in the area. connect to my home network. 

info from knetworkmanger:

type:wireless 802.11
interface: ra0
Hardware address: 
Driver: rt3060
Status: connected
bit rate: 135Mbit/s
ip address: 192.168.0.155
name servers: 192.168.0.1

firefox or rekonq still won't connect to the net. Is knetworkmanger a crap program? or is there a background program causing conflict?

oel@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       Ralink STA  ESSID:""  Nickname:"RT3562STA"
          Mode:Auto  Frequency=2.412 GHz  Access Point: 00:18:E7:C5:6B:B6   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=58/100  Signal level:-81 dBm  Noise level:-115 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by chili555 on 2011-03-29
I'm not very familiar with knetworkmanager. I assume it's just Network Manager with a KDE wrapper. Can you right-click the knetworkmanager icon, select Edit Connections and check off Connect Automatically? What does this tell us?```
ping -c3 192.168.0.1
ping -c3 74.125.157.147
ping -c3 www.google.com
cat /etc/resolv.conf
```Thanks.

---

### Post by Kewbla on 2011-03-29
joel@ubuntu:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.155 icmp_seq=1 Destination Host Unreachable
From 192.168.0.155 icmp_seq=2 Destination Host Unreachable
From 192.168.0.155 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
pipe 3
joel@ubuntu:~$ ping -c3 74.125.157.147
PING 74.125.157.147 (74.125.157.147) 56(84) bytes of data.
64 bytes from 74.125.157.147: icmp_req=1 ttl=52 time=56.8 ms
64 bytes from 74.125.157.147: icmp_req=2 ttl=52 time=46.0 ms
64 bytes from 74.125.157.147: icmp_req=3 ttl=52 time=46.4 ms

--- 74.125.157.147 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 46.059/49.786/56.890/5.028 ms
joel@ubuntu:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
joel@ubuntu:~$ cat /etc/resolv.conf                                                                                                  
# Generated by NetworkManager                                                                                                        
domain phub.net.cable.rogers.com                                                                                                     
search phub.net.cable.rogers.com                                                                                                     
nameserver 192.168.0.1

---

### Post by chili555 on 2011-03-29
> **Kewbla said:**
> joel@ubuntu:~$ ping -c3 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.155 icmp_seq=1 Destination Host Unreachable
From 192.168.0.155 icmp_seq=2 Destination Host Unreachable
From 192.168.0.155 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2000ms
pipe 3
joel@ubuntu:~$ ping -c3 74.125.157.147
PING 74.125.157.147 (74.125.157.147) 56(84) bytes of data.
64 bytes from 74.125.157.147: icmp_req=1 ttl=52 time=56.8 ms
64 bytes from 74.125.157.147: icmp_req=2 ttl=52 time=46.0 ms
64 bytes from 74.125.157.147: icmp_req=3 ttl=52 time=46.4 ms

--- 74.125.157.147 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 46.059/49.786/56.890/5.028 ms
joel@ubuntu:~$ ping -c3 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
joel@ubuntu:~$ cat /etc/resolv.conf                                                                                                  
# Generated by NetworkManager                                                                                                        
domain phub.net.cable.rogers.com                                                                                                     
search phub.net.cable.rogers.com                                                                                                     
nameserver 192.168.0.1Most interesting; you can't reach the presumed gateway but you can reach the internet. Please post:```
route -n
```

---

### Post by Kewbla on 2011-03-29
joel@ubuntu:~$ route -n                                                                                            
Kernel IP routing table                                                                                                              
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface                                                        
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0                                                         
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 ra0                                                          
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0                                                         
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 ra0                                                          
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

---

### Post by Kewbla on 2011-03-29
even plugging in with Ethernet is providing very choppy internet. other computers on network are completely fine running good speeds from speedtest.net. i think i'm going to do  fresh install and go back to 32 bit i'll repost here when fresh install is done. should the wireless work out of the box?

---

### Post by chili555 on 2011-03-29
It probably won't work out of the box. Any idea what the other computers on the network think the gateway is? DNS nameservers?

---

### Post by Kewbla on 2011-03-29
Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.

C:\Users\Jillian>ipconfig

Windows IP Configuration


Wireless LAN adapter Wireless Network Connection:

   Connection-specific DNS Suffix  . : phub.net.cable.rogers.com
   Link-local IPv6 Address . . . . . : fe80::84a:4f49:c58f:7ecf%12
   IPv4 Address. . . . . . . . . . . : 192.168.0.101
   Subnet Mask . . . . . . . . . . . : 255.255.255.0
   Default Gateway . . . . . . . . . : fe80::218:e7ff:fec5:6bb6%12
                                       192.168.0.1

Ethernet adapter Local Area Connection:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . :

Tunnel adapter isatap.phub.net.cable.rogers.com:

   Media State . . . . . . . . . . . : Media disconnected
   Connection-specific DNS Suffix  . : phub.net.cable.rogers.com

Tunnel adapter Teredo Tunneling Pseudo-Interface:

   Connection-specific DNS Suffix  . :
   IPv6 Address. . . . . . . . . . . : 2001:0:4137:9e76:1464:3e60:52de:fee9
   Link-local IPv6 Address . . . . . : fe80::1464:3e60:52de:fee9%13
   Default Gateway . . . . . . . . . : ::



would it be better to just fresh install so we can start on a clean slate?

---

### Post by chili555 on 2011-03-29
Before we do a reinstall, let's try a few other things. I notice, in Windows, that you have an IPv6 address. When you right click the Network Manager icon and Edit Connections, is IPv6 enabled or disabled? Please see attached. Have you done anything else to disable IPv6? What does this tell us?```
ifconfig ra0
```

This is quite mysterious; it ought to spring to life.

---

### Post by Kewbla on 2011-03-29
joel@ubuntu:~$ ifconfig ra0                                                                                                          
  ra0       Link encap:Ethernet  HWaddr f0:7d:68:5e:1c:1d                                                                              
            inet addr:192.168.0.155  Bcast:192.168.0.255  Mask:255.255.255.0                                                           
            inet6 addr: fe80::f27d:68ff:fe5e:1c1d/64 Scope:Link                                                                        
            UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1                                                                         
            RX packets:2188 errors:0 dropped:0 overruns:0 frame:0
            TX packets:635 errors:0 dropped:0 overruns:0 carrier:0
            collisions:0 txqueuelen:1000
            RX bytes:502874 (502.8 KB)  TX bytes:5280 (5.2 KB)
            Interrupt:21
  


no ivp4 or ivp 6 settings in knetworkmanger


router is configured to hand out ips through dhcp. ivp6 is disabled

i think i have just screwed something up big time before i looked for help on here

i have to manually start up knetwork after i login would this cause an issue?

---

### Post by chili555 on 2011-03-29
> i think i have just screwed something up big time before i looked for help on hereUnless there is a lot you haven't told us, I doubt it. I've seen a lot worse.> i have to manually start up knetwork after i login would this cause an issue? Not likely; that's a fairly minor annoyance we can troubleshoot later. I feel like we're staring right at it and can't see it. The stumper is that you can ping Google by IP address but can't actually ping your own router! 

Let's try an experiment. Let's back up resolv.conf so we can restore it later:```
sudo mv /etc/resolv.conf /etc/resolv.conf.bak
```Now, let's write a new one:```
sudo kate /etc/resolv.conf
```Add one line:```
nameserver 8.8.8.8
```Proofread, save and close kate. Now try again:```
ping -c3 192.168.0.1
ping -c3 74.125.157.147
ping -c3 www.google.com
```Meanwhile, I will get a pain-killer and a big glass of wine.

---

### Post by Kewbla on 2011-03-29
i have to step out for a little bit i'll try to get this done as soon as i get back.

enjoy the wine :)

---

### Post by Kewbla on 2011-03-29
pings wouldnt connect to anything
new file made post ping results in a second. hows the wine?

gotta re-install. wife needs her computer back and my net is no longer working  at all. i will post back here to set up the wireless from scratch. thank you for all your help so far! i appreciate it a lot

---

### Post by Kewbla on 2011-03-29
Fresh 32 bit install. loaded up drivers from d-links site. blacklisted 2800 and 2x00 pci and usb and it works :) thanks again for all your help Chili555

---

