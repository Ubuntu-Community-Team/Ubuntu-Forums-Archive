---
title: "I bucked my wireless!"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by redcrystalmoon on 2009-08-05
Ok, this is pretty stupid but hopefully it's just as easy as someone telling me... "It's this one... (you moron)..."

Here's what I did, I just reinstalled eeebuntu base on my acer aspire one netbook. I wanted to get rid of all support for the cups printer and also bluetooth since I use neither... I went to synaptic and completely uninstalled pretty much everything that had anything to do with either of those two things (except when it came up that there were other dependencies that I wasn't sure about) 

So all seemed to work fine and good last night when I did the chopping but when I woke up this morning my wireless would not work. When I click on the network manager icon, the button to enable wireless is gray and I cannot activate it...

Here's the history log from the synaptic manager and I'm hoping someone can tell me which one(s) of these packages I need to reinstall to be able to enable my wireless again...

Completely removed the following packages:
bluez
bluez-alsa
bluez-gnome
bluez-gstreamer
cups-driver-gutenprint
cupsddk
cupsddk-drivers
foomatic-db
foomatic-filters
libgutenprint2
min12xxy
python-cups
python-cupshelpers

Removed the following packages:
bluetooth
bluez-cups
bluez-utils
cups-common
foo2zjs
foomatic-db-engine
hal-cups-utils
libmbca0
splix
system-config-printer-common
evice
f-spot
gedit
gnome-system-monitor
language-selector
system-config-printer-gnome
tsclient
vinagre


I know I probably shouldn't go in and start chopping stuff out that I'm obviously not sure of... I thought I had it licked though! behh...
I just don't want a bunch of stuff hanging around that I'm never going to use taking up space...

Thank you to all the people who give their time to help others, and sorry for the dumbness of this post... 

-hasty chopper

---

### Post by The Toxic Mite on 2009-08-05
Hey, don't worry :D

So your wireless is borked? Go to Applications > Accessories > Terminal, and post the output of the following commands please:

```

sudo lshw -c network
iwconfig
ifconfig

```

Thanks :)

---

### Post by redcrystalmoon on 2009-08-05
Ahh thank you ;o) Here are the outputs...

*-network               
  description: Ethernet interface
  product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
  vendor: Realtek Semiconductor Co., Ltd.
  physical id: 0
  bus info: pci@0000:02:00.0
            logical name: eth0
version: 02    
           serial: 00:23:8b:59:33:05
    size: 10MB/s
    capacity: 100MB/s
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix  vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd  autonegotiation
    configuration: autonegotiation=on  broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0  link=no module=r8169 multicast=yes port=MII speed=10MB/s
    
       *-network
    description: Wireless interface
    product: AR242x 802.11abg Wireless PCI  Express Adapter
    vendor: Atheros Communications Inc.
    physical id: 0
    bus info: pci@0000:03:00.0
    logical name: wmaster0
    version: 01
    serial: 00:24:2b:37:f7:43
    width: 64 bits
    clock: 33MHz
    capabilities: pm msi pciexpress msix  bus_master cap_list logical ethernet physical wireless
    configuration: broadcast=yes  driver=ath5k latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
    
    louise@louise-laptop:~$ iwconfig
    lo        no wireless extensions.
    
eth0      no wireless extensions.
    
    wmaster0  no wireless extensions.
    wlan0     IEEE 802.11bg  ESSID:"WLAN"  
    Mode:Managed  Frequency:2.412 GHz  Access Point: 00:13:F7:FA:EE:C6   
    Bit Rate=1 Mb/s   Tx-Power=27 dBm   
    Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
    Power Management:off
    Link Quality=31/100  Signal level:-88 dBm  Noise level=-99 dBm
    Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
    Tx excessive  retries:0  Invalid misc:0   Missed beacon:0
    
     louise@louise-laptop:~$ ifconfig
    eth0      Link encap:Ethernet  HWaddr 00:23:8b:59:33:05  
    UP BROADCAST MULTICAST  MTU:1500   Metric:1
    RX packets:0 errors:0 dropped:0  overruns:0 frame:0
    TX packets:0 errors:0 dropped:0  overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
    Interrupt:28 Base address:0x2000 
    
     lo        Link encap:Local Loopback  
    inet addr:127.0.0.1  Mask:255.0.0.0
    inet6 addr: ::1/128 Scope:Host
    UP LOOPBACK RUNNING  MTU:16436   Metric:1
    RX packets:16 errors:0 dropped:0  overruns:0 frame:0
    TX packets:16 errors:0 dropped:0  overruns:0 carrier:0
    collisions:0 txqueuelen:0 
    RX bytes:1216 (1.2 KB)  TX bytes:1216 (1.2 KB)
    
    wlan0     Link encap:Ethernet  HWaddr 00:24:2b:37:f7:43  
    inet6 addr:  fe80::224:2bff:fe37:f743/64 Scope:Link
    UP BROADCAST RUNNING MULTICAST  MTU:1500   Metric:1
    RX packets:6 errors:0 dropped:0  overruns:0 frame:0
    TX packets:6 errors:0 dropped:0  overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:655 (655.0 B)  TX bytes:576 (576.0 B)
    
     wmaster0  Link encap:UNSPEC  HWaddr  00-24-2B-37-F7-43-37-34-00-00-00-00-00-00-00-00  
    UP BROADCAST RUNNING MULTICAST  MTU:1500   Metric:1
    RX packets:0 errors:0 dropped:0  overruns:0 frame:0
    TX packets:0 errors:0 dropped:0  overruns:0 carrier:0
    collisions:0 txqueuelen:1000 
    RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by superprash2003 on 2009-08-05
wmaster0 seems to be connected to WLAN , but not getting any ip.. post output of **sudo dhclient wmaster0**

---

### Post by redcrystalmoon on 2009-08-05
If it's connected to WLAN it doesn't show up on the network manager, nor does my home network... usually there is a list of possible networks to connect to but it's not even giving me that...

  wmaster0: unknown hardware   address type 801                  wmaster0: unknown hardware   address type 801
     Listening on LPF/wmaster0/
          Sending on   LPF/wmaster0/
          Sending on   Socket/fallback
          DHCPDISCOVER on wmaster0 to   255.255.255.255 port 67 interval 7
          DHCPDISCOVER on wmaster0 to   255.255.255.255 port 67 interval 11
          DHCPDISCOVER on wmaster0 to   255.255.255.255 port 67 interval 15
          DHCPDISCOVER on wmaster0 to   255.255.255.255 port 67 interval 15
          DHCPDISCOVER on wmaster0 to   255.255.255.255 port 67 interval 13
          No DHCPOFFERS received.
          No working leases in persistent   database - sleeping.

---

### Post by redcrystalmoon on 2009-08-05
I know it has to be something I did when messing around with adding/removing stuff last night because everything worked fine then and also, I still have the live boot from my usb stick and when I plug that in everything connects automatically no problem. I may just have to do a fresh install and that's that, but I would like to figure out what I did to cause this so I can avoid it in the future...

---

### Post by The Toxic Mite on 2009-08-06
Is your wireless working? If not, click on this link:

[http://ubuntuforums.org/showpost.php?p=6895635&postcount=2](http://ubuntuforums.org/showpost.php?p=6895635&postcount=2)

---

### Post by nothingspecial on 2009-08-06
The latest kenel update seems to have broken atheros wireless. I`ve not had time to find a fix yet.

The simplest solution for now is to boot into the previous kernel.

Reboot and when you see grub loading press escape quickly and select

```
Ubuntu 9.04, kernel 2.6.28-13-generic
```

Hopefully that should work

---

### Post by superprash2003 on 2009-08-06
post output of **sudo iwlist scanning**

---

### Post by redcrystalmoon on 2009-08-07
Thank you guys again for replying! 
Yes you must be right that it's a problem with the updates because there's really nothing in the list of things I removed that should mess with the wireless. I went through them all and in fact reinstalled them all to see if that would make a difference but it hasn't. I'm running from my usb right now.

I tried the suggestion about rebooting into a new kernel but no dice... The options that were there were 2.6.28.14-generic as well as one that said (recovery mode) and also a *netbook option which also had a recovery mode option, and a few more that said generic. I tried three different options. I managed to write down some of what it spit back to me when it didn't work... I don't know if this will help or not. I'm still fairly new to Linux (Before April I had no idea what it was, but I'm trying to learn as much as I can...) so I'm not sure what information is relevant or not but here goes:

Gave up waiting for root device
Common problems:
-Boot args (cat/proc/cmdline)
-Check rootdelay=(did the system wait long enough?)
-Check root=
(did the system wait for the right device?)
-Missing modules (cat/proc/modules)
ALERT /dev/disk/by-guid/3d78f4e0-9829-4d82-9000-8f09f398855d  does not exist
Dropping to a shell!

Ok, that came up twice, so then I tried one of the recovery mode options, I think it was the netbook one and it send me to a blue screen of death with a recovery menu on it listing:
resume
clean
dpkg
fsck
grub
netroot
root
xfix

I selected resume and it booted me up as normal, still no wireless...

I haven't tried the method outlined in the link yet but will do so and post what happens...

Output of **sudo iwlist scanning is:**
 lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:21:04:68:39:CE
                    ESSID:"alison"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/100  Signal level:-72 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 0006616C69736F6E
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=0000007e8583a170
                    Extra: Last beacon: 464ms ago
          Cell 02 - Address: 00:18:D1:2D:65:31
                    ESSID:"home"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/100  Signal level:-87 dBm  Noise level=-99 dBm
                    Encryption key:on
                    IE: Unknown: 0004686F6D65
                    IE: Unknown: 010582848B962C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0106
                    IE: Unknown: 32080C1218243048606C
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:tsf=00000000d172c122
                    Extra: Last beacon: 888ms ago

pan0      Interface doesn't support scanning.

---

### Post by redcrystalmoon on 2009-08-08
I can't really try the option from the link right now. 1) I'm running from my flash drive and 2) when I click on the ath5k link, I get a pop-up saying: Could not find package 'linux-backports-modules-intrepid-generic'. so I guess it's a dead link or something... 
I'm running the latest version of eeebuntu I'm assuming it's 9.04 Jaunty. 
I was running the previous version before and had updated to jaunty when it first came out and had no problems with updates/wireless then. But it started to lag so last week I decided to try xubuntu and the xfce interface because I thought it would take up less room and use less resources. Also I figured I would be able to try ext4 instead of ext3. I foolishly installed the os without thoroughly checking it out and it ended up being even slower then the eeebuntu and way more buggy on my machine. I wasn't given an option to switch to ext4 either so I guess I have to find a way to do it manually. 
Anyway, I decided to go back to ubuntu and with the fresh install it is much faster and slicker too, I like it, but wireless it pretty much the only way I use the internet so it's not much good to me without it... Hopefully I'll be able to get it fixed soon so I can keep tweaking out ha! ;o) 
I am grateful for everyone's help. :o}
~

---

### Post by redcrystalmoon on 2009-08-08
[FONT=monospace]Found this on another thread, don't know if this info would help too... It's seeming to be a common problem with the newer updates...

Output for:[/FONT] iwlist auth
lo        no authentication information.

eth0      no authentication information.

wmaster0  no authentication information.

wlan0     Authentication capabilities :
        WPA
        WPA2
        CIPHER-TKIP
        CIPHER-CCMP
          Current Authentication algorithm :
        open


pan0      no authentication information.

---

