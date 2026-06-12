---
title: "Wireless problems"
date: 2005-12-25
forum: Networking &amp; Wireless
---

### Post by cloudy2 on 2005-12-25
I have been trying for hours to get by wireless network to work consistantly
in 5.10. I have an RT 2400 PCI card. The system is dual boot with Windows XP. The wireless card is my only means to connecting to the internet through Linux - there is no other kind of connection available on this particular machine. The connection works perfectly, every time, on windows. Most of the time it does not work on Ubuntu. Every once in a while it will but there seems to be no reason why when it doesnt, which is most of the time. There is currently no security, I took it off on the router to simplify this problem. 

Ive checked [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-07.0031507315/view?searchterm=Network%20settings](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-10-07.0031507315/view?searchterm=Network%20settings)
[https://wiki.ubuntu.com/WiFiHowto](https://wiki.ubuntu.com/WiFiHowto) and tried what they suggested without any luck. 



Here is the output of "sudo ifup ra0":

There is already a PID file /var/run/dhclient.ra.pid with pid 0 
Internet Systems DHCP client V3.02
Copyright Internet Systems Consortium
All rights reserved

For info, please visit (a website)

sit 0 unknown hardware address Type 776
sit 0 unknown hardware address Type 776
Listening on: LPF/(a MAC address)
Sending on: LPF/(same MAC address as above)
Sending on Socket/Fallback

DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 3
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 4
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 11
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 11
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 9
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 14
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 8
DCHPDISCOVER on RA0 to 255.255.255.255 port 67 interval 1
No DHCP offers recieved
No working leases in persistant database, sleeping.

---

### Post by tktreload on 2005-12-25
are you setting the correct ESSID for the given network?
or are you just pinging a dhcp server in the blind?

you can adjust your network settings in the network settings area in gnome. this should just work

---

### Post by cloudy2 on 2005-12-25
The network ID is set, but there is a space in it and it starts with a number-"110 Brookside" perhaps that is the problem? 

I have used Network settings in Gnome and that doesnt work. Doing it manually gave the result listed above. 

It is on the correct channel, and there is currently no security. 

It works sporadically - sometimes it works, most of the time it doesnt. The first time "out of the box" it worked but as soon as I rebooted the problem started. I didn't change anything network related - well, I did install Tomcat 5 and change its port from 8080 to 80 - perhaps this is a problem? 

Windows always works (Its a dual boot system - maybe that has something to do with it...)

---

### Post by tktreload on 2005-12-26
if your network works sporadically then there is something else wrong. I think linux does not get the correct mac address from the accespoint.
If you dont get the correct mac address then you can not get the IP address from the DHCP server. maybe you need to check wether iwconfig gets the right info from the accesspoint.

---

### Post by cloudy2 on 2005-12-26
[QUOTE=tktreload]if your network works sporadically then there is something else wrong. I think linux does not get the correct mac address from the accespoint.
If you dont get the correct mac address then you can not get the IP address from the DHCP server. maybe you need to check wether iwconfig gets the right info from the accesspoint.[/QUOTE]

If my card is not getting the right info from the access point, how can I manually set it? iwconfig returns "SET failed on device ra0, operation not permitted" when I try to change the channel, for instance. I looked arround to see how I could manually tell the card the router's MAC address and couldn't find anything. iwconfig without arguments would not tell me the router's MAC address.

Thanks for your help...

---

### Post by cloudy2 on 2005-12-26
[QUOTE=cloudy2]If my card is not getting the right info from the access point, how can I manually set it? iwconfig returns "SET failed on device ra0, operation not permitted"
Thanks for your help...[/QUOTE]

Dumb me, i forgot to use "sudo". Still, how can I manually give it the router's IP address,etc?

---

### Post by GoUbuntu on 2005-12-26
I have exactly the same problem:

- RT 2400 Wireless LAN card
- Dual boot with Windows (XP) where wireless works every time
- Sometimes when I boot in 5.10 it works, some times it doesn't

I have encryption but I have checked with sudo iwconfig that the key is correct.  Also, I don't change the key and the WLAN either works, or it doesn't.

I've also tried doing things in the following order:
1. Kill dhclient3
2. ra0 down (my wlan interface)
3. ra0 up
4. set essid and key
5. dhclient3 ra0

This fixed it on two occasions, but not every other time.

Here is some other info:

```
brendon@ubuntu:~$ lspci | grep RaLink
0000:00:09.0 Network controller: RaLink Wireless PCI Adpator RT2400 / RT2460

brendon@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0
       description: Wireless interface
       product: Wireless PCI Adpator RT2400 / RT2460
       vendor: RaLink
       physical id: 9
       bus info: pci@00:09.0
       logical name: ra0
       version: 00
       serial: 00:08:a1:6e:b5:2e
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2400 multicast=yes wireless=RT2400PCI
       resources: iomemory:dfff8000-dfff9fff irq:17
  *-network:1 DISABLED
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 10
       bus info: pci@00:10.0
       logical name: eth0
       version: 10
       serial: 00:0d:61:ab:af:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too multicast=yes
       resources: ioport:d800-d8ff iomemory:dfff7700-dfff77ff irq:17

brendon@ubuntu:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:109306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:109306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:13800270 (13.1 MiB)  TX bytes:13800270 (13.1 MiB)

ra0       Link encap:Ethernet  HWaddr 00:08:A1:6E:B5:2E
          inet6 addr: fe80::208:a1ff:fe6e:b52e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000

brendon@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT2400PCI  ESSID:"HSH"
          Mode:Managed  Channel=10  Bit Rate:11 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

sit0      no wireless extensions.

```

I would really appreciate help on this as Ubuntu might become unworkable for me if this continues.

Thanks.

---

### Post by Lambert on 2005-12-26
Try this.

bring down the interface.

sudo ifconfig ra0 down

remove the driver

sudo modprobe -r rt2400 

reinsert driver with debugging option (this may not work as driver needs to be compiled with this option)

sudo modprobe rt2400 debug=1

now open another tab in your terminal and run this command

tail -f /var/log/syslog (errors will show up and be logged in this file)

now bring interface back up

sudo ifconfig ra0 up


now if you want to specify your router try this command

sudo iwconfig ra0 essid ____ channel __ mode managed ap __:__:__:__:__:__ commit

the ap command specifies the routers mac address. fill in the blanks with what looks appropriate.

then 

sudo dhclient ra0

---

### Post by GoUbuntu on 2005-12-26
Lambert, thanks a bundle! 

It works for me now! Yay!

Hopefully this solution will work next time.

You're instructions were fantastic.  I really appreciated them.  It was great they way  you said what you were about to do, then gave the terminal text to achieve it.

I could post the debug output, but is there much point since it works now?

Thanks.

---

### Post by cloudy2 on 2005-12-26
sudo iwconfig ra0 essid ____ channel __ mode managed ap __:__:__:__:__:__ commit

the ap command specifies the routers mac address. fill in the blanks with what looks appropriate.

then 

sudo dhclient ra0[/QUOTE]

Thank you! Manually specifying the MAC address and channel did work. I did not need to change out the driver. At least, it worked this time. My guess is I may have to put this in one of the startup files. 

One page I found usefull was [http://www.linuxforum.com/man/iwconfig.8.php?close_left=true](http://www.linuxforum.com/man/iwconfig.8.php?close_left=true)
It took me awhile to find this, but it contains all the uses of iwconfig.

---

### Post by Lambert on 2005-12-26
[quote=GoUbuntu]
I could post the debug output, but is there much point since it works now?

Thanks.[/quote] 
As long as it is working then there is no need to. But if you have problems go to the /var/log/syslog to look what's being logged there. The best place to get help with the errors is not here. (you might be able to find some help) It's best to go to the drivers home page and ask for help as they know their driver better.

[http://rt2x00.serialmonkey.com/phpBB2/]("http://rt2x00.serialmonkey.com/phpBB2/")

Now when you reboot you will have to go through those instructions again but I'll try to explain how to set this up so it happens during boot(commands I use copy text to the file. You can always just sudo gedit /file/name I use and type it into the file)

add a line to /etc/hotplug/black list so it doesn't load the driver during boot.

sudo echo rt2400 >> /etc/hotplug/blacklist

then add the driver with the debut option to the modprobe file

sudo echo "rt2400 debug=1" >> /etc/modules

Now I'm not sure if this will cause a conflict but it's worth a try. If it does then just open these two files and delete these lines.

Now open your interfaces file and make it look like this

sudo gedit /etc/network/interfaces


iface ra0 inet dhcp
up iwconfig ra0 essid.... (same command I gave you before)

this is sort of a hack and I might be missing something but let me know if it works for you.

Do you travel and use other access points? You may want to look into gtkwifi or networkmanager.

---

### Post by GoUbuntu on 2006-01-07
Hi Lambert,

Thanks for all your help.  Unfortunately the instructions that you gave did not work.  I used gedit for the changes, there's not much to go wrong there really, so I'm pretty sure that I did the changes as asked.

It would be nice if there was a way for it to work automatically on startup.

This computer doesn't travel, so I don't have to worry about other APs, however thanks for the info about that.

Thanks.

Edit: An update - it has just worked with the following lines in /etc/network/interfaces, instead of the up iwconfig line:

wireless-essid "essid"
wireless-key thekey

Those lines were already there.  I hope it continues working.

---

### Post by GoUbuntu on 2006-01-07
Well, my latest idea (in the post above) didn't work the last time I booted up.

I'd like to find out how to get my wireless working every time I boot up.  Any other ideas?

Thanks.

---

