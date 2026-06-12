---
title: "RT73usb and Natty 11.04"
date: 2011-05-20
forum: Networking &amp; Wireless
---

### Post by danielschonfeld on 2011-05-20
So I have the Hawkings HWUG1 usb dongle.  Chipset RT73.

I hook it up to my Natty Desktop edition and it hotplugs as rt73usb.

I try to use iwpriv commands to no avail (no private ioctl).  If i set wpa_supplicant commands into
/etc/network/interfaces

I get hooked up to the access point but get NO DHCP OFFERS from dhclient.  (It appears that if I set my address staticly I can ping the card from outside, but since no scripts run no config is done on the computer side so i dont have any gateway setup, no name resolving no nothing - but it works... however i need it to work with DHCP as well)

Suggestions?  I'm not sure how to proceed from here.

Thanks!

---

### Post by betaman23 on 2011-05-20
Let's see some more info:


sudo lshw -C network
lsusb
iwconfig


Also, update the kernel to 2.6.39.0-generic it seems to fix wireless issues in 11.04.

Post your: uname -a

---

### Post by danielschonfeld on 2011-05-20
sudo lshw -C network:
*-network               
     description: Ethernet interface
     product: AR8131 Gigabit Ethernet
     vendor: Atheros Communications
     physical id: 0
     bus info: pci@0000:02:00.0
     logical name: eth0
     version: c0
     serial: 6c:62:6d:3d:29:03
     size: 100Mbit/s
     capacity: 1Gbit/s
     width: 64 bits
     clock: 33MHz
     capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
     configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI duplex=full firmware=N/A ip=192.168.2.9 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
     resources: irq:42 memory:febc0000-febfffff ioport:e800(size=128)

lsusb:
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 003: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

uname -a:
Linux dan-one 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

iwconfig ill post later after i try the upgrade since i had to pull the dongle for now...

---

### Post by danielschonfeld on 2011-05-20
wlan0     IEEE 802.11bg  ESSID:"blah network"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:7D:81:9A   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:on
          Link Quality=70/70  Signal level=-28 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:2   Missed beacon:0

now with the following uname -a installed:

Linux miner-zero-one 2.6.39-0-generic #5~20110427-Ubuntu SMP Wed Apr 27 15:27:41 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

still NO DHCP Offers....

# dhclient -v wlan0
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:0e:3b:39:03:c9
Sending on   LPF/wlan0/00:0e:3b:39:03:c9
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2011-05-20
Where is your wireless device?> Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 05ac:0220 Apple, Inc. Aluminum Keyboard (ANSI)
Bus 001 Device 003: ID 05ac:0304 Apple, Inc. Optical USB Mouse [Mitsumi]
Bus 001 Device 002: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Manual methods, i.e. dhclient, ifconfig, et al are not likely to work when an automated process like Network Manager is installed and running. Is it?```
ps aux | grep -i network
```Moreover, Network Manager is designed to *disallow* a wireless connection if wired ethernet is available; in your case, it clearly is:> -network
description: Ethernet interface
product: AR8131 Gigabit Ethernet
vendor: Atheros Communications
physical id: 0
bus info: pci@0000:02:00.0
logical name: eth0
--- snip ---
driverversion=1.0.1.0-NAPI duplex=full firmware=N/A [COLOR="Red"]ip=192.168.2.9[/COLOR] latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:42 memory:febc0000-febfffff ioport:e800(size=12
Please plug in the USB dongle, detach the ethernet cable and run and post:```
lsusb
sudo iwlist wlan0 scan
```Thanks.

---

### Post by danielschonfeld on 2011-05-20
I'm not entirely sure how to copy paste to you when I don't have any connection so i'm gonna try to just retype it.

lsusb:

Produces among the rest of the stuff (i disconnected the eth0/wired device)

Bus 001 Device 003: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

and iwlist wlan0 scan produces a list of networks around me among them is the blah network with WPA2 and CCMP as pairwise and group cipher.

I went back to 2.6.38-8 however i can switch back and forth.  

I've stopped network manager using "stop network-manager" and tried dhclient and still no offers.

---

### Post by chili555 on 2011-05-20
> I've stopped network manager using "stop network-manager" and tried dhclient and still no offers.Usually, even if you stop it, it respawns like the evil seed it is. Is it nevertheless still running?```
ps aux | grep -i network
```Your device is claimed by two drivers that conflict like four hands on the steering wheel.```
chili@LAPTOP60:~$ modinfo rt73usb | grep 2573
alias:          usb:v148Fp[COLOR="Red"]2573[/COLOR]d*dc*dsc*dp*ic*isc*ip*
chili@LAPTOP60:~$ modinfo rt2500usb | grep 2573
alias:          usb:v148Fp[COLOR="Red"]2573[/COLOR]d*dc*dsc*dp*ic*isc*ip*
```Let's blacklist rt2500usb:```
sudo su
echo "blacklist rt2500usb" >> /etc/modprobe.d/blacklist.conf
rmmod -f rt2500usb
exit
```Any improvement? It may take a reboot.

---

### Post by danielschonfeld on 2011-05-20
I have verified it not to be respawning by issuing the ps -aux | grep -i network command and its not there... its shutdown.

I have blacklisted the rt2500usb driver and have rebooted

and no luck :(

Still no dhcp offers.

It is worth noting that its automatically trying dhclient3 program and not dhclient... but either one does not produce an IP

---

### Post by danielschonfeld on 2011-05-20
small progress:

I have the NTP daemon running.  When I stopped it and also remarked the following line in dhclient.conf :

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

Something weird happened.... i ran dhclient and it got an offer and just skipped it and continued making DHCP requests.... so still same result but suddenly there were signs of life.

Would you happen to know how those two are related?

---

### Post by chili555 on 2011-05-20
> i ran dhclient and it got an offer and just skipped it and continued making DHCP requests.... so still same result but suddenly there were signs of life.I suggest rechecking your /etc/network/interfaces setup, particularly the wpa parts. > Would you happen to know how those two are related? Not the faintest clue.

You might also try:```
sudo rmmod -f rt73usb
sudo modprobe rt73usb nohwcrypt=1
```If the module won't unload, you might have to down the interface first. If it works, we can write an options file.

---

### Post by danielschonfeld on 2011-05-20
I removed the WPA2 security and made my wifi an open network and i still cannot get DHCP...

On the other hand, i installed the mac drivers for this dongle on my macbook hooked it up and got connected to my wifi network right away.

So the problem is not with WPA2 and its not with my network or my card.... its the settings or driver in ubuntu....

---

### Post by chili555 on 2011-05-20
> I removed the WPA2 security and made my wifi an open network and i still cannot get DHCP...What did your /etc/network/interfaces look like at the time?

---

### Post by danielschonfeld on 2011-05-20
/etc/network/interfaces:

auto wlan0
iface wlan0 inet dhcp
wpa-ssid "blah network"
wpa-psk "mysecretpsk"


I have tried again tweaking with dhclient.conf and wheni remove the last line of request that tries to ask for ntp-servers etc it worked.  But only when the network was without security and open.

when I put back on CCMP it reverted back to not getting a reply.  I tried changing to TKIP... same thing.

I suspect that dhclient does not want to work together with wpa_supplicant.... does that sounds familiar?

MY output is identical to this guys': (excuse me for linking to fedora forum... i just googled this)
[http://www.fedoraforum.org/forum/archive/index.php/t-178526.html](http://www.fedoraforum.org/forum/archive/index.php/t-178526.html)

As you can see their convo got cut and the guy never returned... but my output and experience is identical.

---

### Post by chili555 on 2011-05-20
> I suspect that dhclient does not want to work together with wpa_supplicant.... does that sounds familiar?Not really. I suspect that dhclient and wpa_suppicant don't want to work with the always twitchy in-tree Realtek driver. Did my nohwcrypt=1 suggestion change nothing? I'd hoped there would be an improvement or even a regression by switching from encryption in hardware to encryption in software; i.e. wpa_supplicant.

You can test your dhclient theory easily:```
auto lo
iface lo inet loopback
#chili says never mess with loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.155
netmask 255.255.255.0
gateway 192.168.1.1
wpa-ssid "blah network"
wpa-psk "mysecretpsk"
```Is mysecretpsk the actual key in clear text? It should be.

Then check with:```
sudo ifdown wlan0 && sudo ifup wlan0
ping -c3 www.google.com
cat /etc/resolv.conf
```Make sure your successful connection populated resolv.conf with proper DNS nameservers.

---

### Post by danielschonfeld on 2011-05-20
When I followed your example the discovery of my dongle didn't invoke wpa_supplicant at all so no connectivity what so ever.

There was no essid automatically set and therefore the device wasn't brought up in ifconfig.

It is interesting to note though, i'm not sure why but when i returned to the computer after a long while (about 45 minutes) it had a dhcp ip received - Not sure why?  I'm trying to replicate that again right now.

---

### Post by danielschonfeld on 2011-05-20
So now im pretty much lost.  It's working now...

I'm gonna try a couple more restarts but it seems to be coming up right away and I cannot explain what's different.

The only thing I really changed dramatically was disabling network-manager from even coming up to begin with vs just stopping it afterwards.  Either way it was stopped before too.... however now I changed the upstart script to remove the start on and stop on stanzas.

I'll keep you posted.

So now that i have restarted a couple times we're back to not working..... im gonna let it sit and see if in an hour or so it will finally get the IP... but for now its the same old DHCP REQUEST....

---

### Post by marceloguedes on 2011-06-04
I have this exact same problem here. And it seems to be random.
Always I start Ubuntu I need to unplug and plug again the USB dongle several times. Eventually it works in one of the attempts. But it's really annoying. More than that, the connection is slower than when I use in Windows.

I have problems with this wireless connection since 10.04. In that time I could use ndiswrapper. In 10.10 it doesn't work anymore but a small script helped me. I removed a couple of modules with related resources and it worked. Every time I had to turn on the computer with 10.10, I had to run this script. Annoying but worked:

```

sudo rmmod ndiswrapper
sudo rmmod firewire_ohci
sudo rmmod firewire_core
sudo rmmod rt73usb
sudo modprobe rt73usb

```

So I installed 11.04. And in that day I just didn't need to run the script anymore! It just worked and I was happy but... Someday I just installed one of the Ubuntu updates and the nightmare comes again. I don't know what exactly was, but probably some kernel update mess up things again.

The information on the internet about this problem is a total mess too, because in each Ubuntu version the users used a different workaround and a definitive solution never showed up until now.

I can send more informations from my computer if someone wants to help in this issue. I would really appreciate that.

Thank you and sorry for so long answer.

---

