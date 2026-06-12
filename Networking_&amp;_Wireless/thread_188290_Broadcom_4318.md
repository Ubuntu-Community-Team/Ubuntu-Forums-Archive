---
title: "Broadcom 4318"
date: 2006-06-03
forum: Networking &amp; Wireless
---

### Post by Burke on 2006-06-03
Let me preface this by saying I've looked everywhere and nothing has worked.

Does anyone *actually* have a BCM4318 working in Dapper? What did you do?

I've tried the bcm43xx-fwcutter and ndiswrapper approached, and my wireless still won't work. I'm currently trying to make it work with ndiswrapper. Here's some information that may be relevant:

ndiswrapper -l
```
Installed ndis drivers:
bcmwl5          driver present, hardware present
burke@burke-gw:~$ iwconfig
lo        no wireless extensions

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"home network"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```


iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  Nickname:"home network"
          Mode:Auto  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate=54 Mb/s   Tx-Power:25 dBm
          RTS thr=2347 B   Fragment thr=2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

lspci | grep Broadcom
```
0000:03:07.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

btw, I tried wpa-psk, then wep, and neither work.

Anyone?



EDIT: Okay, now I'm back on with the bcm43xx approach, and I'm getting closer. I've followed the guide to Broadcom cards, and I did the "blacklist ndiswrapper" thing, but it's still not working.

When I try to connect, I'm asked for a wep key. I enter it, and network manager seems to work for a while. The bottom light turns green (on the nm-applet icon), and it just sits there; it can't get any further.... and I only get the bottom light the first time I try. I can't even get that until I reboot.

I'm hopeless. I'd be extremely thankful if anyone can point me in the right direction.

---

### Post by Braino on 2006-06-04
I have found the fwcutter didn't work, I was able to see the card but I couldn't get an IP from the router, although I could find its essid. Instead, blacklist bcm43xx, and un-blacklist ndiswrapper. This can be done by adding 'blacklist bcm43xx' to
```

 sudo gedit /etc/modprobe.d/blacklist

```

A working driver can be found from Acer [here]("ftp://ftp.support.acer-euro.com/notebook/aspire_3020_5020/driver/80211g.zip").

Then, unzip that, get rid of the bad driver and hook up the good driver to ndiswrapper
```

sudo ndiswrapper -e bcmwl5

```
```

sudo ndiswrapper -i Desktop/bcmwl5.inf

```
Check it:
```

sudo ndiswrapper -l

```
Then, if you need to put the ndiswrapper module back:
```

sudo modprobe ndiswrapper

```

Here is my /etc/network/interfaces:

```

# The loopback network interface
auto lo
iface lo inet loopback

iface eth1 inet dhcp
wireless-essid YOURESSIDHERE
wireless-key open
iface eth0 inet dhcp
auto eth1
auto eth0

```


Hope this helps :)

---

### Post by Burke on 2006-06-04
Thanks, I'll try this out.  If I decide to install dapper64 (I have an Athlon 64) instead, will the instructions vary at all (can I use the same driver?)

EDIT: Nevermind, I found the 64-bit driver. Well, here goes nothing, I hope it works.

---

### Post by piracyrocks on 2006-06-04
could u post the 64 bit driver?...thats the one i need

---

### Post by Burke on 2006-06-04
Absolutely. Here it is:

[libbey.name/bcmwl5.zip]("libbey.name/bcmwl5.zip")

I'm pretty sure this is the right driver. I'm going to try it out now.

---

### Post by Burke on 2006-06-04
So I've followed all the instructions, but here's what I get when I do /etc/init.d/networking restart:
```

 * Reconfiguring network interfaces... Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:03:25:35:1a:cb
Sending on   LPF/eth1/00:03:25:35:1a:cb
Sending on   Socket/fallback
DHCPRELEASE on eth1 to 192.168.1.1 port 67
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth0 ; No such device.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFADDR: No such device
eth0: ERROR while getting interface flags: No such device
eth0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth0.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:03:25:35:1a:cb
Sending on   LPF/eth1/00:03:25:35:1a:cb
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPOFFER from 192.168.1.1
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 269702 seconds.
```

What's going on?

It seems like the card isn't recognized, but ndis says the hardware is present.

---

### Post by dtlinker on 2006-06-05
It looks like you are copying the commands for eth0 from a previous post, but from your first post, it looks like your wireless is wlan0. It looks like that is the problem you are having now.

I have finally gotten it to work with a Dell Inspiron B130, which has the Broadcom 4318 wireless controller. I tried the built-in drivers, but got an error which other notes said needed a re-install of the firmware. I tried doing that using bcm43xx-fwcutter and the driver that came with the Dell, but was unable to get that to work. In particular, it seemed to detect the signal, and report it as 100%, but then would not connect at all.

I then blacklisted bmc43xx, and followed the instructions for ndiswrapper and used the Dell driver. This worked right away! In fact, it worked better than on  Breezy, I was never able to get WEP to work at all, but now it works perfectly. Overall, I am very happy with Dapper, which has solved this problem I had with Breezy, and is working very well so far.

---

### Post by Patsoe on 2006-06-05
Hi Burke,

I actually do have it working, with WPA. Output from lspci: 

```
0000:02:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g]  802.11g Wireless LAN Controller (rev 02)

```

seems to be the same card :) 

I used ndiswrapper, with 64bit drivers (since I'm running the AMD64 flavour) from Acer. I installed NetworkManager to handle the wpa_supplicant stuff.

Before associating, my iwconfig output looks the same as yours in your start post. Then, I got NetworkManager to do the associating.

---

### Post by Burke on 2006-06-05
Okay, I'm getting closer. Here's what I get now when I try to restart networking:

```
burke@burke-laptop:~$ sudo emacs /etc/network/interfaces
burke@burke-laptop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces... Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth0 ; Invalid argument.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:c0:a8:ae:ae:72
Sending on   LPF/eth0/00:c0:a8:ae:ae:72
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth1/00:03:25:35:1a:cb
Sending on   LPF/eth1/00:03:25:35:1a:cb
Sending on   Socket/fallback
DHCPREQUEST on eth1 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.102 -- renewal in 267193 seconds.
                                                                         [ ok ]

```

Do I need to be able to authenticate to the network before I get a dhcpoffer?

Nm-applet still doesn't recognize my wifi, even though the little blue light on my touchpad is on now.

---

### Post by Patsoe on 2006-06-05
> Nm-applet still doesn't recognize my wifi, even though the little blue light on my touchpad is on now.
I think you can only either use nm-applet or the standard networking scripts. Seeing that you get dhcp-queries when you restart networking, I'm guessing you did not un-configure your interfaces? (also, you need to remove any config for wpa-supplicant - see wiki.ubuntu.com/NetworkManager for a complete description)

---

### Post by frolic54 on 2006-07-02
Hi Patsoe
I spent many, many hours to get the bloody WLAN running.
When ever I try the NDIS way I am loosing the WLAN-Card entry in System->Admin->Network, its not existing any more :-(

How did you manage to have a working WLAN? 
I have exactly the same hardware (Dapper 6.06 for AMD64 on HP Compaq nx6125)

When I try this [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
the notbook is freezing a few seconds after the files are placed in /lib/firmware

---

### Post by Patsoe on 2006-07-02
> When ever I try the NDIS way I am loosing the WLAN-Card entry in System->Admin->Network, its not existing any more

I suppose you mean using ndiswrapper? Did you check if the module ndiswrapper loaded correctly? (type "lsmod | grep ndis" and see if it is listed)
Also note that you need WinXP 64bit drivers for ndiswrapper on amd64.

> When I try this [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
the notbook is freezing a few seconds after the files are placed in /lib/firmware

So you get a system freeze, even before you load the bcm43xx driver? That's spooky. I wonder what just placing files there could do. 

Could it be that other modules you're running are using the /lib/firmware directory (this is a very wild guess)?

Anyway, I could get the card recognized using the method in your link, but then it refused to connect to the WPA protected network here. This is why I went the ndiswrapper route.

---

### Post by frolic54 on 2006-07-03
Thank you for the reply

I tried with the wl_apsta.o from [http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)
And also with the latest XP64 drivers from HP (there I got an invalid checksum error from the fwcutter)

[QUOTE=Patsoe]So you get a system freeze, even before you load the bcm43xx driver? That's spooky. I wonder what just placing files there could do.[/QUOTE]

Just a few seconds after the: sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/driver.file

[QUOTE=Patsoe]Could it be that other modules you're running are using the /lib/firmware directory (this is a very wild guess)?[/QUOTE]

There are no other files in /lib/firmware (except the subdir of the current firmware).

[QUOTE=Patsoe]Anyway, I could get the card recognized using the method in your link, but then it refused to connect to the WPA protected network here. This is why I went the ndiswrapper route.[/QUOTE]

I also want to use at least WPA, so I will try the ndiswrapper way again and put the error log from the installation later to this tread.
First I will use your sugested: type "lsmod | grep ndis" and see if it is listed
There was always a invalid driver message when I used the 64bit file from [http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+howto)

[QUOTE=Patsoe]Also note that you need WinXP 64bit drivers for ndiswrapper on amd64.[/QUOTE]
From HP for the nx6125?
If so, then I can't use the sudo ./ndiswrapper_setup?
But then I am absolutly helpless to do this installation, because I am a Windowz crack and Linux dummy :confused:

---

### Post by Patsoe on 2006-07-03
No, you don't need the HP driver; that's just a repackaged driver written by Broadcom, just like any other. I got mine from Acer, for example, because everyone else seemed to use that driver.

The howto in the link you're giving looks like a smooth way to do it. Wish that guy had made it back when I was struggling with this - would probably have been a real timesaver :)

If you get it working, could you perhaps add your experience to this thread: [http://ubuntuforums.org/showthread.php?t=189337&](http://ubuntuforums.org/showthread.php?t=189337&) - I'm sort of hoping it will serve to gather all useful stuff for the nx6125 :)

---

### Post by Chemroydal Tissue on 2006-07-10
Thank you, Braino, for posting yr solution, and Burke, for posting the drivers for 64 bit. My card (Belkin 54g Wireless G Desktop Card (F5D7000) Rev4000 works perfectly with WPA.

---

### Post by Chemroydal Tissue on 2006-09-23
Just installed on a new hard disk, and thought I should mention the following:

To get ndiswrapper to load on startup, add> ndiswrapperto /etc/modules

I did this automatically the first time through, and forgot to post it. Then forgot to do it the second time through - a serious PITA at startup.

---

