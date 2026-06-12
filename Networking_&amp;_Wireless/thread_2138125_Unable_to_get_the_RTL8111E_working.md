---
title: "Unable to get the RTL8111E working"
date: 2013-04-23
forum: Networking &amp; Wireless
---

### Post by brusapa on 2013-04-23
Hi, this is my first post , and I'm not very well with English but I'll do my best.
 I'm a newbie in linux and I'm trying to install Ubuntu Server 12.04 in one pc which has a RTL8111E network card ( specifically it's a Gigabyte 970A-UD3 motherboard ), during the installation it failed to set up the network, not automatically neither manually, so I finished the installation without internet.

After the installation i tried to install the Realtek *Linux driver for kernel 3.x and 2.6.x and 2.4.x, *when uncompressed, I noticed it has a script for automatic installation so i go for it, this was the script:

```
#!/bin/sh


# invoke insmod with all arguments we got
# and use a pathname, as insmod doesn't look in . by default


TARGET_PATH=$(find /lib/modules/$(uname -r)/kernel/drivers/net -name realtek -type d)
if [ "$TARGET_PATH" = "" ]; then
    TARGET_PATH=/lib/modules/$(uname -r)/kernel/drivers/net
fi
echo
echo "Check old driver and unload it." 
check=`lsmod | grep r8169`
if [ "$check" != "" ]; then
        echo "rmmod r8169"
        /sbin/rmmod r8169
fi


check=`lsmod | grep r8168`
if [ "$check" != "" ]; then
        echo "rmmod r8168"
        /sbin/rmmod r8168
fi


echo "Build the module and install"
echo "-------------------------------" >> log.txt
date 1>>log.txt
make $@ all 1>>log.txt || exit 1
module=`ls src/*.ko`
module=${module#src/}
module=${module%.ko}


if [ "$module" = "" ]; then
    echo "No driver exists!!!"
    exit 1
elif [ "$module" != "r8169" ]; then
    if test -e $TARGET_PATH/r8169.ko ; then
        echo "Backup r8169.ko"
        if test -e $TARGET_PATH/r8169.bak ; then
            i=0
            while test -e $TARGET_PATH/r8169.bak$i
            do
                i=$(($i+1))
            done
            echo "rename r8169.ko to r8169.bak$i"
            mv $TARGET_PATH/r8169.ko $TARGET_PATH/r8169.bak$i
        else
            echo "rename r8169.ko to r8169.bak"
            mv $TARGET_PATH/r8169.ko $TARGET_PATH/r8169.bak
        fi
    fi
fi


echo "DEPMOD $(uname -r)"
depmod `uname -r`
echo "load module $module"
modprobe $module


is_update_initramfs=n
distrib_list="ubuntu debian"


if [ -r /etc/debian_version ]; then
    is_update_initramfs=y
elif [ -r /etc/lsb-release ]; then
    for distrib in $distrib_list
    do
        /bin/grep -i "$distrib" /etc/lsb-release 2>&1 /dev/null && \
            is_update_initramfs=y && break
    done
fi


if [ "$is_update_initramfs" = "y" ]; then
    if which update-initramfs >/dev/null ; then
        echo "Updating initramfs. Please wait."
        update-initramfs -u -k $(uname -r)
    else
        echo "update-initramfs: command not found"
        exit 1
    fi
fi


echo "Completed."
exit 0

```
When ran it, finished with a "Completed" so I assumed that worked as it's suppose to work.

I restart my server and i check this:
```
lspci -v

```

And this is what I get:
IMAGE REMOVED

[B]Sorry about the photos instead screenshots, but i don't know how to do them in Ubuntu server, or even if it's really possible.

[/B]It seems to recognize the network card so i tried an 
```
ifconfig
```
but it only shows the loopback interface, with an
```
ifconfig -a
```
shows both, the loopback and eth0, so I thought the problem was that it was not configured.

I've edited the /etc/network/interfaces file and i add the two last lines manually:
IMAGE REMOVED

After that I tried to restart the network with 
```
[COLOR=#111111][FONT=Consolas]sudo /etc/init.d/networking restart[/FONT][/COLOR]
```
but it freezes in the second step, reconfiguring network interfaces, and it stays there forever...

I tried to restart the computer but it can't initiate the network, so it doesn't finish booting.

This is what i get in ifconfig right now:
IMAGE REMOVED

Anybody can help me to get this working? Would greatly appreciate it

Regards, and sorry again for my bad English

---

### Post by chili555 on 2013-04-23
Your English is just fine, there is no problem there.> Sorry about the photos instead screenshots, but i don't know how to do them in Ubuntu server, or even if it's really possible.I don't believe it is possible to do screenshots from a server which is not running a graphical desktop. There are various methods to transfer the terminal output to a text document and then to a USB drive, but they are cumbersome and probably more than we need. Instead, I recommend you write down the essential elements and post them here, such as:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```And:```
lspci -v

Realtek RTL8111/8168B Ethernet
<snip>
Kernel Module: r8168
```I hope that will be a bit easier to do.

Let's troubleshoot. Please run and post:```
sudo ifdown eth0 && sudo ifup -v eth0
```We want to see if the interface gets an IP address or, if not, where it stopped. As I said above, you can condense the results down to the essentials. Also let us see:```
sudo ethtool eth0
```All we need to see is the line I have highlighted here as well as anything else that looks unusual:> Settings for eth0:
	Supported ports: [ TP ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Speed: Unknown!
	Duplex: Unknown! (255)
	Port: Twisted Pair
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	MDI-X: Unknown
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000007 (7)
			       drv probe link
	[COLOR="#FF0000"]Link detected: no[/COLOR]
Once we have this all working as expected, we'll want to set a static IP address so you can ssh, ftp, etc. in to the server.

---

### Post by brusapa on 2013-04-23
Ok, first, for trying those things I need to set /etc/network/interfaces as default, so I can boot the pc :biggrin:
Now it seems like this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).


# The loopback network interface
auto lo
iface lo inet loopback

```
After that i've tried the first command:
```
sudo ifdown eth0 && sudo ifup -v eth0
```
and this is what I'm getting:
```
ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.
```

I suppose this is caused because now it doesn't appear in ifconfig, only in ifconfig -a

And this is the reply to the ethtool command:
```
Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Speed: 1000Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    MDI-X: Unknown
    Supports Wake-on: pumbg
    Wake-on: g
    Current message level: 0x00000033 (51)
                   drv probe ifdown ifup
    Link detected: no



```

Thank you very much for spending your time with my problem!

---

### Post by chili555 on 2013-04-23
> and this is what I'm getting:
[QUOTE]ifdown: interface eth0 not configured
Ignoring unknown interface eth0=eth0.

I suppose this is caused because now it doesn't appear in ifconfig, only in ifconfig -a
[/QUOTE]Not quite. You got that because it no longer appears in /etc/network/interfaces. ifdown/ifup is supposed to read the file and bring the declared interface, in this case eth0, down and then up. Since eth0 doesn't appear, it can't proceed and gives the error.
I assume the computer is actually booting normally, but it appears not since it is taking forever to get an IP address and it tries and tries again. Is that correct? 

Please try:```
sudo ifconfig eth0 up
sudo dhclient -v eth0
```Since it doesn't work on boot, we are pretty certain it won't work here, but we are interested in why and where it fails. Once again, please feel free to omit and condense the output in order to post it here.

---

### Post by brusapa on 2013-04-24
> **chili555 said:**
> I assume the computer is actually booting normally, but it appears not since it is taking forever to get an IP address and it tries and tries again. Is that correct? 
Yes, when I keep the two last lines of /etc/network/interfaces, the ones about eth0, the computer doesn't boot, it could be what you say, but i'm not really sure...

I've tried the commands you told me
The first one: ```
[COLOR=#000000][FONT=Ubuntu Mono]sudo ifconfig eth0 up[/FONT][/COLOR]
```apparently works well, it doesn't return any error, and now eth0 appears in ifconfig:
```
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX           inet6 addr: fe80::96de:80ff:fe21:3914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10950 (10.9 KB)  TX bytes:0 (0.0 B)
          Interrupt:74 Base address:0xa000 
```

But it gets stucked on the second one:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dhclient -v eth0[/FONT][/COLOR]
```
This is what I get:
```
...
Listening on LPF/eth0/XX:XX:XX:XX:XX:XX  
Sending on  LPF/eth0/XX:XX:XX:XX:XX:XX  
Listening on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
...
#I get about 20 lines like that
...
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

It seems like the problem is with dhcp, but I'm absolutely sure that I have it activated on my router, in fact, I've got many others devices working with dhcp in that router... =(

---

### Post by chili555 on 2013-04-24
> DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
...
#[COLOR="#FF0000"]I get about 20 lines like that[/COLOR]I'm fairly certain that's what's going on behind the scenes when it appears the computer won't boot. It is actually booting as expected but the DHCP problem is taking so much time that it appears to be hung. > It seems like the problem is with dhcp, but I'm absolutely sure that I have it activated on my router,I'm quite certain it is enabled. Somewhere in the negotiation between your computer and the router, something is going wrong and the router refuses to give an IP address. Please check the obvious things; the cable is attached and it is plugged in to a correct LAN port on the router. Please be sure the only module loaded is r8168 and not r8169:```
lsmod | grep r81
```Do you know the address of the router? It may be 192.168.1.1 or similar. It will be identified as 'gateway' on any of the other computers. Please try to manually assign an IP address:```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.1.101 up
```...where x.101 is an address in the range of the router. Then see if you actually connected:```
ping -c3 192.168.1.1
```If your router (gateway) address is 192.168.0.1 or some other, please adjust accordingly.

---

### Post by brusapa on 2013-04-25
First of all I've tried to plug the network cable of the computer to a laptop, just to check that everything was working as it was supposed, it actually does.

I've checked that only r8168 module is loaded:
```
[COLOR=#000000][FONT=Ubuntu Mono]lsmod | grep r81[/FONT][/COLOR]
r8168                 248628  0 

```

Then I manually assign an IP address:
```
sudo ifconfig eth0 down
sudo ifconfig eth0 192.168.0.105 up


```

And checked that works:
```
ifconfig
eth0      Link encap:Ethernet  HWaddr XX:XX:XX:XX:XX:XX  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fe21:3914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:685 (685.0 B)  TX bytes:0 (0.0 B)
          Interrupt:74 Base address:0xa000 

```

But the ping still doesn't work:
```
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.From 192.168.0.105 icmp_seq=1 Destination Host Unreachable
From 192.168.0.105 icmp_seq=2 Destination Host Unreachable
From 192.168.0.105 icmp_seq=3 Destination Host Unreachable


--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 2015ms
pipe 3

```

Now I really don't understand anything, it's not a problem with DHCP I guess?

---

### Post by chili555 on 2013-04-26
It is not a DHCP problem. The device and the router just fail to connect either with a static address or DHCP. What version of the driver did you build? The latest, newest and shiniest from Realtek's site?```
modinfo r8168 | grep vers
``` It's mysterious to me that the device is getting a few probes, I assume, from the router and evidently not transmitting:> ifconfig
eth0      Link encap:Ethernet  HWaddr 94:de:80:21:39:14  
          inet addr:192.168.0.105  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::96de:80ff:fe21:3914/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          [COLOR="#FF0000"]RX bytes:685 (685.0 B)  TX bytes:0 (0.0 B)[/COLOR]
          Interrupt:74 Base address:0xa000Are there any clues here?```
dmesg | grep r816
```

---

### Post by brusapa on 2013-04-26
Right now I'm in a business trip until Monday, I'll check that when I arrive. Thank you very much for your time and knowledge ;-)

---

### Post by brusapa on 2013-04-28
Well, I've just arrived home and I've check both things, but I'm afraid we haven't got luck.
All seems to be good with the driver (Yes, it's the last one from Realtek webpage)
```
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/ethernet/realtek/r8168.koversion:        8.035.00-NAPI
srcversion:     C7041A3D9074A1575512C13
vermagic:       3.5.0-23-generic SMP mod_unload modversions 

```

And in dmesg nothing seems strange...
```
[    1.562677] r8168 Gigabit Ethernet driver 8.035.00-NAPI loaded[    1.562783] r8168 0000:03:00.0: irq 74 for MSI/MSI-X
[    1.728314] r8168: This product is covered by one or more of the following patents: US5,307,459, US5,434,872, US5,732,094, US6,570,884, US6,115,776, and US6,327,625.
[    1.728326] r8168  Copyright (C) 2012  Realtek NIC software team <nicfae@realtek.com> 

```

I'm starting to think of buying a new pci network card... :(

---

### Post by chili555 on 2013-04-28
The version you have is indeed the latest. As a last ditch experiment, please try one thing before we give up:```
sudo modprobe -r r8168
sudo modprobe r8168 eee_enable=1
sudo dhclient eth0
```Any improvement?

I am out of ideas/suggestions/crazy hunches.

---

### Post by brusapa on 2013-04-28
I'm afraid that neither works, well, the time that we're losing trying to fix this is more valuable tan one network card, so that will be the solution ;)

Thank you very much for your time and effort, and if you ever come to the north of Spain, remind me that I owe you a beer :D

---

### Post by brusapa on 2013-05-13
I manage to get it working!!!! It was a BIOS level problem, there is a setting in the Gigabyte BIOS called IOMMU (which comes disabled by default), that must be enabled for get it working, no idea of what is that option for, but it works! :)

---

### Post by chili555 on 2013-05-13
Awesome! I'm glad you explained it because I suspect it will help some searchers down the road.

---

### Post by RichardBlaine on 2013-06-25
This is 100% the problem with the GA-970A-UD3 under Ubuntu.  Thank you [COLOR=#000000]brusapa!  This post saved me an untold number of headaches and allowed me to get my modest new server up and running.[/COLOR]

[COLOR=#000000]Now the IOMMU (Input / Output Memory Management Unit) is like the traffic cop for Network and Graphic Processing Units.  It's mostly used in a virtual setting.  Why it's needed for Ubuntu is perplexing.  If anyone knowledgeable on the subject can shed some light on this topic I'd be interested in expanding my understanding.
[/COLOR]
Cheers!

---

