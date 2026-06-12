---
title: "usr 5416, no accesspoints?"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by v3n0m on 2006-06-05
Hi all.

since this is my first post here, I hope that I can give enough information, I'm quite a linux noob at the moment.....

I downloaded the desktop cd of ubuntu 6.06, and it works quite well (only used as livecd at the moment, not yet installed) but I can't seem to get my wlan card to work.

I have a us robotics 5416 card (wireless turbo pci card).
it looks like it is detected like it should, since I see it in the network window (wlan0).

but when I fill in all the properties, including wepkey, the progressbar keeps going from side to side, but nothing happens.
after some time, the window disappears, but the connection isn't made.

I verified that my ESSID & wepkey are correct, so that shouldn't be a problem.

when I do a "iwlist wlan0 ap" command, it says "no accesspoints found", or something like that, but I'm sure that the accesspoint is reachable from this position (when I reboot in windows, it connects straight away).

I also set the channel to 11 by doing "sudo iwconfig wlan0 channel 11", that is the channel I use in windows too.

does anybody have suggestions to make it work?
I really like the ubuntu distro, but without wlan, I can't use it.

thanks in advance.

---

### Post by v3n0m on 2006-06-06
anyone?

It seems I got a bit further yesterday, iwconfig says I'm connected to an accesspoint, I guess changing the mode of the wlan0 connection, did the trick (from managed to master).

but still no internet, or even ping to the router possible?

if anybody can help me, please ;)

V3N0M

--- EDIT ---
I was messing around a bit with the network, and I found some more info, which is probably the problem:

when I set the settings for the network (doesn't matter how, via terminal or via network administration), and I type "sudo ifup wlan0", I get this:

DHCPDISCOVER on wlan0 to 255.255.255.255 port 76 interval [different each time].

but my router is located on ip 192.168.2.1

a static IP doesn't help either, and shouldn't be the problem, since my pc works perfectly with a dhcp connection (same pc, only booted windows right now).

HELP!, I like ubuntu, but can't use it without lan.
wired lan isn't an option :(

thanks in advance

---

### Post by greatmetal on 2006-08-20
I have this problem too please help i hate windows and want to switch completely to linux

---

### Post by greatmetal on 2006-08-21
Please help I cant stand windows any longer i have tried ndiswrapper on ubuntu linux 6.06 lts with kernel 2.6.15-23-368

---

### Post by greatmetal on 2006-08-21
BUMP I have had this article up for 2 days and no one has helped ](*,)

---

### Post by lupine_nickt on 2006-08-21
Righty-ho, let's see then :). Sorry for not responding 2 days ago... I've no experience of these cards, so I thought I'd leave it to someone with experience.

Step one, can you post the output of the following commands in the terminal:-
iwconfig
ifconfig -a 
lspci

As for your problem... firstly, what it's not: 

DHCPDISCOVER (dhclient) is not your problem; 255.255.255.255 is the address you send to in order to get all machines to listen to your packet.

Setting mode to Master turns your card into an access point, so you don't want to do that.

For testing purposes, you should always turn off WEP and WPA (if you have it) - just to eliminate them. Also, do all this stuff from the command line - you can automate it later. 

First things first - you say you're using ndiswrapper but you [should be using Linuxant.](http://www.usr.com/support/product-template.asp?prod=5416) So, open a terminal window and...
```

mkdir /tmp/linuxant-work
cd /tmp/linuxant-work
wget http://www.linuxant.com/driverloader/wlan/full/archive/dldrinstall.run
ifconfig wlan0 down
rmmod -w ndiswrapper
sudo apt-get remove --purge ndiswrapper
chmod a+x dldrinstall.run
wget http://www.linuxant.com/driverloader/ndis_drivers/usr11gv40q.zip
mkdir windriver
mv usr11gv40q.zip windriver
cd windriver
unzip usr11gv40q.zip

./dldrinstall.run

```

Go through the install process (can't help you with that, sorry). The .inf file is at /tmp/linuxant-work/windriver/usr11g.inf

xF,

...Nick

---

### Post by greatmetal on 2006-08-21
thanks for the responce

heres my output

ifconfig
eth0      
Link encap:Ethernet  HWaddr 00:13:D4:BF:32:80

UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          
Interrupt:225 Base address:0xa800

lo        
Link encap:Local Loopback
          
inet addr:127.0.0.1  
mask:255.0.0.0
          
inet6 addr: ::1/128 Scope:Host

UP LOOPBACK RUNNING  MTU:16436  Metric:1

RX packets:117 errors:0 dropped:0 overruns:0 frame:0

TX packets:117 errors:0 dropped:0 overruns:0 carrier:0

collisions:0 txqueuelen:0
 
RX bytes:8736 (8.5 KiB)  TX bytes:8736 (8.5 KiB)
sit0      Link encap:IPv6-in-IPv4
          
NOARP  MTU:1480  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:0
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


wlan0     Link encap:Ethernet  HWaddr 00:C0:49:D7:AF:FD
          
UP BROADCAST MULTICAST  MTU:1500  Metric:1
          
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:1000
          
RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          
Interrupt:209


--------------------------------------------------


iwconfig



lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     
IEEE 802.11b+/g+  ESSID:"linksys"  Nickname:"acx v0.3.21"
          
Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          
Bit Rate:54 Mb/s   Tx-Power=15 dBm   Sensitivity=1/3
          
Retry min limit:7   RTS thr:off
          
Power Management:off
          
Link Quality=34/100  Signal level=8/100  
Noise level=0/100
          
Rx invalid nwid:0  
Rx invalid crypt:0  
Rx invalid frag:0
          
Tx excessive retries:0  Invalid misc:0   Missed beacon:0
sit0      no wireless extensions.
----------------------------------------------


lspci
0000:00:00.0 Host bridge: Silicon Integrated Systems [SiS] 760/M760 Host (rev 02)

0000:00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202

0000:00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)

0000:00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
0000:00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] Sound Controller (rev a0)

0000:00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

0000:00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

0000:00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)

0000:00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
0000:00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 90)

0000:00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)

0000:00:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
0000:00:09.0 Communication controller: Conexant HSF 56k Data/Fax Modem

0000:00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)

---

### Post by lupine_nickt on 2006-08-21
Try "sudo iwconfig wlan0 ap <ap-mac>" ?

xF,

...Nick

---

### Post by greatmetal on 2006-08-21
The dldrinstall.sh did not work because my only connection for my pc is a wireless connection plus my dad is to lazy to drill holes in the walls for my ethernet.

And the sudo iwconfig wlan ap <ap-mac> did not work

---

### Post by lupine_nickt on 2006-08-21
I don't really know what to suggest, then. You're using the wrong driver; unless you change it, your chances of getting this thing working are minimal.

If you can copy the files needed onto a CD from another computer (any line starting with wget can be substituted for by d/l'ing the file at the URL specified, and copying into the /tmp/linuxant-work folder) and move them over to your computer like that, then you should be able to continue. Otherwise, a trip to eBay might be in order to buy a slightly saner card.

xF,

...Nick

---

### Post by greatmetal on 2006-08-21
Somthing good happened I got a full install for my distro on the site i am now able to select a network from a list!!! But the bad thing is I am haveing trouble connectiong to them.

You have helped alot thanks

---

### Post by greatmetal on 2006-08-21
Any more tips would be appreciated to be able to connect to the networks

---

### Post by lupine_nickt on 2006-08-22
OK, by the looks of it linuxant is actually a charge product :(. I didn't realise that before. What that means is, to use it on a permanent basis, they'll take $20 off of you. You can get a 30-day trial license from [here](https://www.linuxant.com/store/) (free!), to see if it'll actually work.

xF,

...Nick

---

### Post by greatmetal on 2006-08-22
thats okay i will continue renewing the license ;P or find cough a
spare key

---

### Post by greatmetal on 2006-08-22
Well cant renew the licence because it goes by mac address
And it does not work very well i have only got one page to load
about 1/8th of the way and my signal strenght lis really low too
when i do iwlist scanning and the signal in windoze is "Very Good"

---

### Post by diesel440 on 2006-10-15
Yeah, I hear ya..

 I have the same USR5416 card and I use Ubuntu 6.06 LTS. After I turn my computer on it will work for like maybe 12 hours and then it gets disconnected from the access point, but the whole thing is theres no way to reconnect it. In the gnome network monitor it shows that the link is there but you`re not connected. And issuing the command to reconnect it does nothing:
 
 iwconfig wlan0 ap XX:XX:XX:XX:XX:XX 

You have to reboot the whole system to get back online. Anyways, stay away from their cards, cause this seems like a silly problem but nobody bothered to fix it. I`m looking to replace my card with something more compatible myself..  Anyone can recomend a very well supported wireless PCI card??

---

### Post by diesel440 on 2006-10-15
Ok, I did a little experimenting. Try this:

 sudo ifdown wlan0

 sudo ifup wlan0

It will not stop the disconnects, but atleast  you wont have to reboot the        
system to get back online.

---

