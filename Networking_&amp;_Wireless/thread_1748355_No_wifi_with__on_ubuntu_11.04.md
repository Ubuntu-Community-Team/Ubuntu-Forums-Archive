---
title: "No wifi with  on ubuntu 11.04"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by estebe on 2011-05-03
hi, i've the same problem as lot of people. 

I can not connect to wifi networks, i can see them but not connect.

my wifi device is:



estebe@WSTestebe:~$ lsusb | grep VIA
Bus 002 Device 002: ID 160a:3184 VIA Technologies, Inc. VIA VNT-6656 [WiFi 802.11b/g USB Dongle]

What can I do?

---

### Post by josephmills on 2011-05-03
please open your terminal and type in 
```

sudo lshw -C network

```
and 
```

rfkill list all 

```
and paste here thanks

---

### Post by estebe on 2011-05-03
estebe@WSTestebe:~$ sudo lshw -C network
[sudo] password for estebe: 
  *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:01:2e:27:be:2c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 latency=0 link=no maxlatency=20 mingnt=1 multicast=yes port=MII
       resources: irq:22 memory:fe02b000-fe02bfff ioport:fc00(size=8) memory:fe02a000-fe02a0ff memory:fe029000-fe02900f
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@2:3
       logical name: eth1
       serial: 00:12:7b:49:7f:00
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=vt6656 multicast=yes wireless=802.11-a/b/g
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: 7a:78:65:eb:29:b8
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.68 link=yes multicast=yes

estebe@WSTestebe:~$ rfkill list all
estebe@WSTestebe:~

this last order has no output...

---

### Post by josephmills on 2011-05-03
I do not know this driver all that much but lets see 
```

lsmod | grep vt

```
also try 
```

iwlist scan 

```
and 
```

rfkill list

```
thanks

---

### Post by estebe on 2011-05-03
estebe@WSTestebe:~$ lsmod | grep vt
vt6656_stage          212328  0

estebe@WSTestebe:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: C0:3F:0E:F3:FB:FA
                    ESSID:"EUSKALTELFBFA"
                    Mode:Managed
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/100  Signal level=-78 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: 00:26:24:68:77:D1
                    ESSID:"Thom_D0041905"
                    Mode:Managed
                    Channel:7
                    Frequency:2.442 GHz (Channel 7)
                    Quality=90/100  Signal level=-54 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: 00:22:15:61:8F:BD
                    ESSID:"WebSTAR"
                    Mode:Managed
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=10/100  Signal level=-86 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 04 - Address: 00:23:69:E5:CA:CE
                    ESSID:"Vodafone59F9"
                    Mode:Managed
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=55/100  Signal level=-68 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: 00:24:D2:E8:59:FA
                    ESSID:"Vodafone59F9"
                    Mode:Managed
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/100  Signal level=-82 dBm  Noise level=0 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

usb0      Interface doesn't support scanning.

My network is vodafone59f9

estebe@WSTestebe:~$ rfkill list
estebe@WSTestebe:~$ 

that is all, thank you for your support

---

### Post by estebe on 2011-05-03
perhaps this can help:

this network need authenticate WPA/WPA2 Personal password

---

### Post by josephmills on 2011-05-03
lets see if a
```

iwlist auth 

```

---

### Post by estebe on 2011-05-03
estebe@WSTestebe:~$ iwlist auth
lo        no authentication information.

eth0      no authentication information.

eth1      Authentication capabilities :
		WPA
		WPA2
		CIPHER-TKIP
		CIPHER-CCMP


usb0      no authentication information.

estebe@WSTestebe:~$

---

### Post by josephmills on 2011-05-03
```

cat /etc/network/interfaces 

```

---

### Post by estebe on 2011-05-03
estebe@WSTestebe:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

estebe@WSTestebe:~$

---

### Post by josephmills on 2011-05-03
ok this is the info that I have gathered you have two wifi devices one is internel and the other is the usb both of which do not have all there mods loaded. the interneal one is capable of scanning so I think that is has some thing to do with the mods but not sure. Like I said I am do not know this card. I am sure that some one come along that is more experienced and will be able to help you out.

---

### Post by estebe on 2011-05-03
thanks for all your time. :D
where can you see that i have 
two wifi devices? i'm sure that i havve only one....
sure someone else can help me!

---

### Post by estebe on 2011-05-04
today I have take out the wpa security and now is connect! so is clear that the problem is on how to manage the authenticcation wpa/wpa2.

can someone give me some light on this matter?

If you see my previous post, i have, at the output of iwlist, two networks with the same name, this is because i have a range expander from linksys.

thanks in advance

---

### Post by Jake.Debord on 2011-05-04
I had the same problem a couple days ago. But I had just installed Ubuntu 10.10 and was setting up my wireless for the first time. Try installing WifiRadar or look under ubuntu packages for Network Manager. I was under the impression it was already installed and that I just couldn't find it. When after it was all said and done I never had it. 

If you are trying to setup your wireless connection through the network program already installed on your system, give up. Look up WifiRadar, I'm only about one week into Ubuntu and it was super easy for me :)

Just make sure you have the correct drivers installed, and wifiradar will be a breeze!
[Edit If iwlist shows any results your drivers are probably installed just fine]

---

### Post by estebe on 2011-05-06
hi again,

i have installed first wifi radar, but i do not like it, then i tried with wicd, and always says: password incorrect (but password is ok).

anyone has the same problem as me? i'm :mad: getting nervous with this matter

---

### Post by estebe on 2011-05-09
I have tried with wep password but the same result. so it the system is with no security I can connect.
:confused::confused::confused:

this is "una mierda":-x

---

### Post by josephmills on 2011-05-09
try and reset your router and your network card ```
/etc/init.d/networking restart 
``` also if the handshakes and not happen (wpa/wpa2) we could try and crack the password on wep to see if that is the troubles also but I would try to restet the router (button on the bottom of it) What kind of router is this? but I think that it is your firmware or mods that is the trouble

---

### Post by estebe on 2011-05-09
Hi, again.

I've already done this. so I think that is something that works different than on 10.10. the router is a huawei HG553 from vodafone.

---

### Post by josephmills on 2011-05-09
lets see a ```
dmesg | grep vt 
```

---

### Post by estebe on 2011-05-10
```

estebe@WSTestebe:~$ dmesg | grep vt
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.38-8-generic-pae root=UUID=4b56b1dd-0103-49a4-a246-a6bd61736f1e ro quiet splash vt.handoff=7
[    0.000000] vt handoff: transparent VT on vt#7
[    0.333295] devtmpfs: initialized
[    5.750459] vt6656_stage: module is from the staging directory, the quality is unknown, you have been warned.
[    6.000734] usbcore: registered new interface driver vt6656

```

hope this can help...

---

### Post by josephmills on 2011-05-10
lets see a ```
modinfo vt6656
``` anything come up?

---

### Post by estebe on 2011-05-10
```

estebe@WSTestebe:~$ modinfo vt6656
ERROR: modinfo: could not find module vt6656
estebe@WSTestebe:~$ 

```

Is this possible? Now i'm connectting without safety...but connect to internet

---

### Post by josephmills on 2011-05-10
so you are connected but with no security code? If this is so 
open your terminal and type in ```
sudo apt-get install wpasupplicant 
``` is it all ready installed? if so go to synaptic then type in wpa do you see the wpasupplicant? Mark it for removal then reboot then reinstall it then reboot then sign into your router and change the security to wpa2 try to connect nothing drop it a level anything no repeat yes Great

---

### Post by estebe on 2011-05-10
I've already this packet installed on its newer version. 

what i mean is that i can connect only if my router has no security. i tried with wpa and wep with no success.

---

### Post by estebe on 2011-05-10
I've already this packet installed on its newer version. 

what i mean is that i can connect only if my router has no security. i tried with wpa and wep with no success.

should i have some module call vt6656?

---

### Post by josephmills on 2011-05-10
yes you need that those mods to load it is your driver for the wireless card > *-network:0
description: **Wireless interface**
physical id: 1
bus info: usb@2:3
logical name: eth1
serial: 00:12:7b:49:7f:00
capabilities: ethernet physical wireless
configuration: broadcast=yes **driver=vt6656** multicast=yes wireless=802.11-a/b/g
*-network:1
description: Ethernet interface
physical id: 2
logical name: usb0
serial: 7a:78:65:eb:29:b8
capabilities: ethernet physical
configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.68 link=yes multicast=yes

---

### Post by estebe on 2011-05-11
joseph, i found this

```

estebe@WSTestebe:~$ modprobe -l  | grep vt
kernel/drivers/video/vt8623fb.ko
kernel/drivers/xen/xen-evtchn.ko
kernel/drivers/media/video/ivtv/ivtv.ko
kernel/drivers/media/video/ivtv/ivtvfb.ko
kernel/drivers/hwmon/vt1211.ko
kernel/drivers/hwmon/vt8231.ko
kernel/drivers/staging/vt6656/vt6656_stage.ko
estebe@WSTestebe:~$ 


```

this seems that the kernel has the driver, 

Has anyone works with this on unbutu 11.04 or is my computer fault? I'm using a zotac gforce 9300 motherboard with this usb wifi card vt 6656

---

### Post by mike3244 on 2011-05-11
I have exactly the same problem on a Dell Latitude D630 using an internal Intel wireless adapter. I can connect to unsecured networks but not secured.

---

### Post by originofstorms on 2011-05-13
Same problem here, also on the Zotac GeForce 9300 mobo with "onboard" wifi via a VIA VNT-6656 dongle. Worked fine on 10.10, only connects to unsecured networks with 11.04. Makes me wish downgrading was easier!

Any more ideas on how to further narrow down the issue?

---

### Post by originofstorms on 2011-05-13
I tried booting with the 2.6.35-28 kernel from Maverick, and it appears to work fine. Seems like there's a regression in the vt6656_stage driver somewhere between 2.6.35-28 and 2.6.38-8. We should probably report this problem upstream, but I'm not sure where or how. Anyone?

---

### Post by celafon on 2011-08-09
There's already bug for this. Please mark it 'affects me' if you are affected -- hopefully it will speed up the resolution time...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/813200](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/813200)

Thanks.

---

### Post by rtsang on 2012-08-25
[FONT=Arial]I'm having the same problem...

I recently bought VIA Artigo A1100 with this vt6656 wireless card. I tried the following versions of ubuntu, not a single one like to work with this wireless card.

12.04: Installed. Can use wired connection. Cannot use wireless.
followed instructions here: [https://help.ubuntu.com/community/WifiDocs/Driver/vntwusb](https://help.ubuntu.com/community/WifiDocs/Driver/vntwusb)
failed at:[/FONT][FONT=Arial]
[/FONT][FONT=Arial]> $ sudo dkms build -m vntwusb -v 1.20.03forgot the exact wording, but something like "Kernel gave unexpected return value".

10.04: Can boot, but screen messed up, cannot install.
[/FONT][FONT=Arial]11.04: Live CD (or Live USB rather). Can use wired connection. Can recognize wireless and see network but cannot auth even though correct password is entered. 
I found this post and become frustrated :sad:

Edit: Upgraded to 11.10 and installed Wicd Network Manager (Disabled the built-in network manager). And now it works perfectly !! 

[/FONT]

---

