---
title: "network and terminal"
date: 2013-02-21
forum: Networking &amp; Wireless
---

### Post by alabamatoy on 2013-02-21
total newb here.  2 questions.  

First: Installed 12.04LTS from CDROM.  Its installed as dual-boot with WXP.  WXP network works fine.  Ubuntu says network is disconnected.  Yes, its "enabled".  I have enabled and disabled and unplugged/plugged the NW cable etc.

Second - how the heck do you open a terminal window or get to command prompt?  Searching in help only tells about altF2 which apparently wont give you the text response to the command entered.  I tried to run ifconfig and could get nowhere.

TIA...

---

### Post by MG&amp;TL on 2013-02-21
What network card do you have? Possibly a driver issue.
 
To open a terminal, press Ctrl+Alt+T, or press the dash button (Ubuntu logo, top left) and search for "terminal". 
 
Have fun with that terminal, I think you'll find it's a little better than the default windows one. :)

---

### Post by fdrake on 2013-02-21
can you please provide us with the output of these commands:
```

ifconfig -v
sudo lshw -class network
route

```

---

### Post by alabamatoy on 2013-02-21
> **fdrake said:**
> can you please provide us with the output of these commands:
```

ifconfig -v
sudo lshw -class network
route

```

 Here is result:   ```
doc@upstairsPC-Linux:~$ ifconfig 
```
eth0
```
Link encap:Ethernet  HWaddr 00:11:11:04:b9:65
UP BROADCAST MULTICAST  MTU:1500  Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B)  TX bytes:187813 (187.8 KB)  

```

lo
```
Link encap:Local Loopback
inet addr:127.0.0.1  Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING  MTU:16436  Metric:1
RX packets:2328 errors:0 dropped:0 overruns:0 frame:0
TX packets:2328 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:189640 (189.6 KB)  TX bytes:189640 (189.6 KB)  

```

```

doc@upstairsPC-Linux:~$ sudo lshw -class network
*-network
description: Ethernet interface
product: 82562EZ 10/100 Ethernet Controller
vendor: Intel Corporation
physical id: 8
bus info: pci@0000:02:08.0
logical name: eth0
version: 02
serial: 00:11:11:04:b9:65
size: 10Mbit/s
capacity: 100Mbit/s
width: 32 bits
clock: 33MHz
capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s    
resources: irq:20 memory:fcfff000-fcffffff ioport:df40(size=64) doc@upstairsPC-Linux:~$
```

---

### Post by alabamatoy on 2013-02-21
Obviously this forum doesnt work like the one I manage, sorry for the all-in-one-line response, I dont know what tags will fix that, code didnt work.

---

### Post by fdrake on 2013-02-21
> **alabamatoy said:**
> Obviously this forum doesnt work like the one I manage, sorry for the all-in-one-line response, I dont know what tags will fix that, code didnt work.

just copy and paste from the terminal into the (#) code tag.

---

### Post by MG&amp;TL on 2013-02-21
> **alabamatoy said:**
> Obviously this forum doesnt work like the one I manage, sorry for the all-in-one-line response, I dont know what tags will fix that, code didnt work.
 
Eh..I just copy-paste between code tags. I don't know what you did...

---

### Post by alabamatoy on 2013-02-21
> **fdrake said:**
> just copy and paste from the terminal into the (#) code tag.  Yeah, I would, but the box cant access the NW.  I had to paste it into a new document on a USB stick and then carry that to a working windows box to post it.  Apparently the default text editor in Ubuntu removed all the carriage returns.  Lesson learned, I will attempt to edit the txt to make it look right.

---

### Post by alabamatoy on 2013-02-21
```
doc@upstairsPC-Linux:~$ ifconfig
eth0
      Link encap:Ethernet  HWaddr  00:11:11:04:b9:65
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:187813 (187.8 KB)
lo
        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2328 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2328 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:189640 (189.6 KB)  TX bytes:189640 (189.6 KB)
doc@upstairsPC-Linux:~$ sudo lshw -class network
[sudo] password for doc: 
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:02:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:04:b9:65
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half latency=64
       link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:20 memory:fcfff000-fcffffff ioport:df40(size=64)
doc@upstairsPC-Linux:~$ 


```

---

### Post by sandyd on 2013-02-21
sandyd looks up from tv

To indicate a newline in text files, a newline indicator is used.

They are different in windows & linux.

Linux: '\n'
Windows: '\r\n'
I don't remember the ones for Mac.

sandyd fixes text, and goes back to watching TV.

---

### Post by sandyd on 2013-02-21
> size: 10Mbit/s
capacity: 100Mbit/s

Interesting. For some reason, your network card is refusing to run the line at full speeds.

Have you tested the line/card with another computer/ethernet port?

---

### Post by fdrake on 2013-02-21
i don't like this line:
```

       logical name: eth0
       version: 02
[COLOR="Red"]_**serial: <removed MAC Address>**_[/COLOR]
       size: 10Mbit/s
       capacity: 100Mbit/s

```

> 
eth0
      Link encap:Ethernet  [COLOR="Red"][U][B]HWaddr <removed MAC Address>  
[/B][/U][/COLOR]

---

### Post by fdrake on 2013-02-21
follow these steps and try to add the mac address to your interface"
[http://linuxpoison.blogspot.com/2010/10/how-to-find-and-change-network-card-mac.html](http://linuxpoison.blogspot.com/2010/10/how-to-find-and-change-network-card-mac.html)

and restart.


to get the interface address use a live cd or another present OS(windows)

---

### Post by alabamatoy on 2013-02-22
I thought Ubuntu was supposed to be real easy.  So far, its nothing of the sort.

I have an Intel Pro/100 VE NIC.  I rebooted in WXP and verified, the NIC works fine.  Boot in Ubuntu and no network.  

Anyway, I need some help getting the bloody network card working.  Any assistance would be appreciated.  I dont know what to do next.

---

### Post by alabamatoy on 2013-02-22
> **fdrake said:**
> follow these steps and try to add the mac address to your interface"
[http://linuxpoison.blogspot.com/2010/10/how-to-find-and-change-network-card-mac.html](http://linuxpoison.blogspot.com/2010/10/how-to-find-and-change-network-card-mac.html)

and restart.


to get the interface address use a live cd or another present OS(windows)

The MAC is there and correct, but in my text one of the forum admins removed it.  When I run the command, the MAC is shown, but Sandy removed it from my post.  While watching TV.  :-)

---

### Post by fdrake on 2013-02-22
> **alabamatoy said:**
> I thought Ubuntu was supposed to be real easy.  So far, its nothing of the sort.

that is not due to a security hole but to a bad configuration, it looks like.

---

### Post by alabamatoy on 2013-02-22
> **fdrake said:**
> that is not due to a security hole but to a bad configuration, it looks like.

No disagreement on that, and I know its my fault, but I dont know how to fix it.

---

### Post by steeldriver on 2013-02-22
Can we see the contents of your /etc/network/interfaces file please?

```
cat /etc/network/interfaces
```Also, if you are running a newer version of network-manager, you should be able to get detailed info about eth0 via

```
 nmcli dev list iface eth0 | grep -v HWADDR
```

That will also tell us whether network-manager thinks it should be managing eth0

---

### Post by alabamatoy on 2013-02-22
```
doc@upstairsPC-Linux:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
```

```
doc@upstairsPC-Linux:~$ nmcli dev list iface eth0 | grep -v hwaddr
GENERAL.DEVICE:                         eth0
GENERAL.TYPE:                           802-3-ethernet
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        82562EZ 10/100 Ethernet Controller
GENERAL.DRIVER:                         e100
GENERAL.HWADDR:                         xx:xx:11:04:B9:xx
GENERAL.STATE:                          70 (connecting (getting IP configuration))
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1e.0/0000:02:08.0/net/eth0
GENERAL.IP-IFACE:                       eth0
GENERAL.NM-MANAGED:                     yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     /org/freedesktop/NetworkManager/ActiveConnection/60
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     10 Mb/s
WIRED-PROPERTIES.CARRIER:               off

```

I munged the mac address so the admin doesnt have to remove it again.

---

### Post by steeldriver on 2013-02-22
OK so it looks like the connection may be stuck waiting for a DHCP response from your network? did you configure the connection manually via the GUI nm-applet? if so what values did you put in the IPv4 tab?

---

### Post by alabamatoy on 2013-02-22
> **steeldriver said:**
> OK so it looks like the connection may be stuck waiting for a DHCP response from your network? did you configure the connection manually via the GUI nm-applet? if so what values did you put in the IPv4 tab?

Its all set to auto, or whatever the default is.  I didnt enter anything.

Note the ifconfig results farther back in the thread - its transmitting, but not receiving.

---

### Post by steeldriver on 2013-02-22
well since there's no assigned IP address in your ifconfig, I would guess any TX bytes are just DHCPDISCOVER packets maybe?

what happens if you do

```
sudo dhclient -v eth0
```

---

### Post by DiabolicalClaptrap on 2013-02-22
Interesting. Your connection is running in half duplex. Maybe force full duplex 100baseTx?

```
 sudo mii-tool --force=100baseTx-FD
```You can always revert by replacing everything after = with: 10baseT-HD

---

### Post by varunendra on 2013-02-24
*Thread moved to **Networking & Wireless**.*

(/me doesn't like watching TV, so watching this thread instead :) - indeed looks interesting)
.

---

### Post by alabamatoy on 2013-02-24
> **steeldriver said:**
> 
what happens if you do

```
sudo dhclient -v eth0
```

```
doc@upstairsPC-Linux:~$ sudo dhclient -v eth0
Internet Systems Consortium DHCP Client 4.1-ESV-R4
Copyright 2004-2011 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/xx:xx:xx:04:b9:xx
Sending on   LPF/eth0/xx:xx:xx:04:b9:xx
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
^C
```

IOW, nuttin....

---

### Post by alabamatoy on 2013-02-24
> **DiabolicalClaptrap said:**
> 

```
 sudo mii-tool --force=100baseTx-FD
```You can always revert by replacing everything after = with: 10baseT-HD

Tried that, it doesnt give back any response, so Im assuming it just did it.

---

### Post by alabamatoy on 2013-02-24
OK - UPDATE.

I dug through my drawer full of cables and parts and found an old Linksys USB NIC.  Plugged it in, and instantly had NW connectivity.  Im posting this from the Ubuntu box.

This is a driver problem, right?  Its gotta be either a corrupted driver or incorrect driver.  The NIC works fine in WXP, but boot to Linux and it wont work when nothing else has changed, and you can see from this painful newb thread that I have beat on the config.  Havent I?

So school me.....how do I forcibly update/replace/reload the driver?  

I went to the Intel site and for the correct NIC, it has a Linux driver, but the readme says "This driver supports 2.4.x and 2.6.x kernels."  How do I tell what kernel I have and will this driver work with it?

Thanks for everyone's patience and help in schooling the newb......

---

### Post by matt_symes on 2013-02-24
Hi

Check your router. Do you have enough DHCP IP addresses. Are you whitelisting MAC addresses.

Assign a static IP on your routers subnet in network manager. Does that then give you connectivity ?

Ubuntu is trying to get an ip address but it is never being offered one.

Kind regards

---

### Post by alabamatoy on 2013-02-24
> **matt_symes said:**
> Hi

Check your router. Do you have enough DHCP IP addresses. Are you whitelisting MAC addresses.

I will check this (I am away from the box for a while) but since it works fine in WXP on same box, shouldnt that be ruled out?  The H/W MAC shouldnt change when booting from XP versus Linux, right? and the fact that I put a new NIC on the box and it works fine (to me) should rule out the router.

But I will verify later.  Thx

---

### Post by matt_symes on 2013-02-24
Hi

I think we posted at the same hence you had already completed some checking while i posted.

It sounds like the router is not the problem.

I would still try putting a static ip address on the card and see if you get network connectivity. I doubt it but i would check.

Kind regards

---

### Post by matt_symes on 2013-02-24
HI

You may have the wrong driver.

> [SIZE=2]**NAME**[/SIZE][SIZE=2]     **fxp** -- Intel EtherExpress PRO/100 Ethernet device driver[/SIZE][http://manpages.ubuntu.com/manpages/precise/man4/fxp.4freebsd.html](http://manpages.ubuntu.com/manpages/precise/man4/fxp.4freebsd.html)

Your system is using the e100 driver.

Kind regards

---

### Post by Hadaka on 2013-02-24
Hi, following along and got curious..
I dug through my drawer full of cables and parts and found an old  Linksys USB NIC.  Plugged it in, and instantly had NW connectivity.  Im  posting this from the Ubuntu box.

was this usb wireless or old school wired?

---

### Post by varunendra on 2013-02-24
> **matt_symes said:**
> You may have the wrong driver.

Just to be sure, let's see -
```
lspci -nn | grep -i net
```

---

### Post by alabamatoy on 2013-02-24
> **matt_symes said:**
> I would still try putting a static ip address on the card and see if you get network connectivity. I doubt it but i would check.

Kind regards

I tried that early on (I should have put it in one of the posts, sorry) and it made no difference.

---

### Post by alabamatoy on 2013-02-24
> **Hadaka said:**
> was this usb wireless or old school wired?

Wired.

---

### Post by matt_symes on 2013-02-24
Hi

> **alabamatoy said:**
> I tried that early on (I should have put it in one of the posts, sorry) and it made no difference.

That was a long shot but it does now really point to the driver.

Kind regards

---

### Post by Hadaka on 2013-02-24
Hi, sounds like everything in the router is ok, just the ethernet card
giving you problems. Do you also have a wireless card in the computer?
if yes..then please do..

```
lspci -nnk | grep -iA3 net 
```

this will show what drivers are loaded for
the wireless and wired card.

---

### Post by DiabolicalClaptrap on 2013-02-24
You asked how to check your kernel version. You'd just type
```
uname -a
```To the person above me, I believe this was posted. The result was: 82562EZ 10/100 Ethernet Controller. No wireless.


Edit: Come to think of it, I had an error similar to this a few days ago (I have a different card, however). I ended up having to just try and reconnect a few times.

---

### Post by varunendra on 2013-02-24
> **varunendra said:**
> Just to be sure, let's see -
```
lspci -nn | grep -i net
```

> **Hadaka said:**
> then please do..

```
lspci -nnk | grep -iA3 net 
```

These are logical questions to help us help you. Please consider answering, if you are already not too frustated which is understandable.

@ hadaka,
I think post #4 already has the details (lshw) you are interested in, except explicitly showing [noparse]vid:pid[/noparse] code for which -nn is sufficient. Of course unless I'm missing something ;)


**PS :**
HINT for Everyone : [http://ubuntuforums.org/showthread.php?t=2118634&pp=50](http://ubuntuforums.org/showthread.php?t=2118634&pp=50) is the url to display this thread with 50 posts 'per page', so you don't have to jump between pages to review it. :popcorn:

---

### Post by alabamatoy on 2013-02-24
> **varunendra said:**
> Just to be sure, let's see -
```
lspci -nn | grep -i net
```

 ```
doc@upstairsPC-Linux:~$ lspci -nn | grep -i net 
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)  
```

---

### Post by alabamatoy on 2013-02-24
> **Hadaka said:**
> ```
lspci -nnk | grep -iA3 net 
```

```
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [8086:1050] (rev 02)
    Subsystem: Dell Device [1028:0157]
    Kernel driver in use: e100
    Kernel modules: e100
```

---

### Post by varunendra on 2013-02-24
> **alabamatoy said:**
> ```
doc@upstairsPC-Linux:~$ lspci -nn | grep -i net 
02:08.0 Ethernet controller [0200]: Intel Corporation 82562EZ 10/100 Ethernet Controller [**[COLOR="Navy"]8086[/COLOR]**:**[COLOR="Red"]1050[/COLOR]**] (rev 02)  
```

'modinfo e100' in my PC gives -
```
modinfo e100
filename:       /lib/modules/3.2.0-36-generic/kernel/drivers/net/ethernet/intel/e100.ko
firmware:       e100/d102e_ucode.bin
firmware:       e100/d101s_ucode.bin
firmware:       e100/d101m_ucode.bin
version:        3.5.24-k2-NAPI
license:        GPL
author:         Copyright(c) 1999-2006 Intel Corporation
description:    Intel(R) PRO/100 Network Driver
srcversion:     3CF569461A087DBBBD0E2BD
alias:          pci:v00008086d000027DCsv*sd*bc02sc00i*
alias:          pci:v00008086d0000245Dsv*sd*bc02sc00i*
..
*<snip>*
alias:          pci:v0000**[COLOR="Navy"]8086[/COLOR]**d0000**[COLOR="Red"]1050[/COLOR]**sv*sd*bc02sc00i*
*<snip>*
..
depends:        
intree:         Y
vermagic:       3.2.0-36-generic SMP mod_unload modversions 
parm:           debug:Debug level (0=none,...,16=all) (int)
parm:           eeprom_bad_csum_allow:Allow bad eeprom checksums (int)
parm:           use_io:Force use of i/o access mode (int)
varun@varun-K54C:~$ 

```
..which tells me that the exact card is supported by the e100 driver. So at least the driver is okay.

Will take a deeper look in a couple of hours, meanwhile ideas from others are welcome.

---

### Post by steeldriver on 2013-02-24
Have we looked at dmesg yet?

```
dmesg | grep -w e100
```

or

```
dmesg | grep -w eth0
```

Also if it *is* a DHCP issue, it sometimes helps disabling IPv6 (set to 'Ignore' in the network manager applet IPv6 tab)

---

### Post by varunendra on 2013-02-24
> **steeldriver said:**
> ```
dmesg | grep -w e100
```
or
```
dmesg | grep -w eth0
```
or,
```
dmesg | grep -ie e100 -e eth
```
..would do the same thing (slightly more) in one go :)

To permanently [disable iPv6]("http://ubuntuforums.org/showpost.php?p=12351792") (is rarely used anyway) -
> set IPv6 "Method" to "Ignore" in Network Manager, and disable it permanently by adding the following to your /etc/sysctl.conf file -
[QUOTE]# disable IPv6
net.ipv6.conf.all.disable_ipv6=1
net.ipv6.conf.default.disable_ipv6=1
net.ipv6.conf.lo.disable_ipv6=1
You can easily do so by just copy-pasting the following command in a terminal -
```
echo -e "\n# disable IPv6\nnet.ipv6.conf.all.disable_ipv6=1\nnet.ipv6.conf.default.disable_ipv6=1\nnet.ipv6.conf.lo.disable_ipv6=1" | sudo tee -a /etc/sysctl.conf
```
[/QUOTE]

Still didn't find enough time to take the 'deeper look' though ;), so thanks, *steeldriver*, for the input.

---

### Post by Hadaka on 2013-02-25
Hi, its interesting that all is well when the wired usb connection is made
but the internel card is running half duplex, yet runs fine in windows. I think
the kernel likes the usb driver but not the e100. maybe this will help. Connect
the wired usb and...
please do ..

```
sudo apt-get update
sudo apt-get upgrade 
```

---

