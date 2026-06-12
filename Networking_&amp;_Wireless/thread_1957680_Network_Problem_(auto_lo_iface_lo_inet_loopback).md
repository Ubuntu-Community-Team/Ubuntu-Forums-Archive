---
title: "Network Problem (auto lo iface lo inet loopback)"
date: 2012-04-12
forum: Networking &amp; Wireless
---

### Post by The Black Night on 2012-04-12
(running Ubuntu 10.04.4 LTS AMD 64)

Ok, I need some help with the final part of some instructions I found elsewhere on this board.

> Run this:
Code:

sudo lshw -C network
sudo lspci
sudo ifconfig -a
sudo cat /etc/network/interfaces

Post the output.

I suspect your /etc/network/interfaces reads this:
Code:

auto lo
iface lo inet loopback

Append this to the file and reboot:
Code:

auto eth0
iface eth0 inet dhcp

That should work for wired nics (i assume you don't use wireless).Did all that, got this


> desktop:~$ sudo lshw -C network  *-network DISABLED     
       description: Ethernet interface
       product: RTL-8169 Gigabit Ethernet
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 10
       serial: 00:01:80:5c:7d:93
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:23 ioport:e000(size=256) memory:f8021000-f80210ff memory:80100000-8011ffff(prefetchable)
desktop:~$ sudo lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:0b.0 PCI bridge: PLX Technology, Inc. PEX8112 x1 Lane PCI Express-to-PCI Bridge (rev aa)
00:0d.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
00:0f.0 RAID bus controller: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
02:00.0 VGA compatible controller: nVidia Corporation G98 [GeForce 8400 GS] (rev a1)
-desktop:~$ sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:80:5c:7d:93 
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:23 Base address:0x2000

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:6560 (6.5 KB)  TX bytes:6560 (6.5 KB)

ldesktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

desktop:~$ sudo cat /etc/network/interfaces auto eth0 iface eth0 inet dhcp
[sudo] password for lopez: 
auto lo
iface lo inet loopback

cat: auto: No such file or directory
cat: eth0: No such file or directory
cat: iface: No such file or directory
cat: eth0: No such file or directory
cat: inet: No such file or directory
cat: dhcp: No such file or directory
desktop:~$ This is where I don't get it 

> 
Append this to the file and reboot:
Code:

auto eth0
iface eth0 inet dhcpWhat is this telling me to do

Thank you all in advance :)

---

### Post by Iowan on 2012-04-12
If you're using Network Manager, check those settings first. Network Manager and the */etc/network/interfaces* don't always play nicely with each other. At one time, *interfaces* would override NM - more recent versions???

NM *should* have an **Auto eth0** line with  **Connect automatically** and **Available to everyone** checkboxes.

To answer the question you asked: You can edit the /*etc/network/interfaces * with your preferred editor (you'll need to use **sudo**) and add the aforementioned lines to the end of the file.

My machine  uses NM -thus does not have settings for eth0 in the */etc/network/interfaces* file.

Have I added enough confusion, yet?

---

### Post by The Black Night on 2012-04-13
Thank you for your prompt reply (didn't expect it to happen so quickly)

I still don't get it (which is embarrassing sense I've been a user since 7.04) but I did try these and a few (many) others!

> desktop:~$ sudo cat /etc/network/interfaces
auto lo
iface lo inet loopback

desktop:~$ sudo cat /etc/network/interfaces/auto eth0 iface eth0 inet dhcp
cat: /etc/network/interfaces/auto: Not a directory
cat: eth0: No such file or directory
cat: iface: No such file or directory
cat: eth0: No such file or directory
cat: inet: No such file or directory
cat: dhcp: No such file or directory
desktop:~$ sudo cat /etc/network/interfaces code auto eth0 iface eth0 inet dhcp
auto lo
iface lo inet loopback

cat: code: No such file or directory
cat: auto: No such file or directory
cat: eth0: No such file or directory
cat: iface: No such file or directory
cat: eth0: No such file or directory
cat: inet: No such file or directory
cat: dhcp: No such file or directory
desktop:~$ sudo cat /etc/network/interfaces auto eth0 iface eth0 inet dhcp
auto lo
iface lo inet loopback

cat: auto: No such file or directory
cat: eth0: No such file or directory
cat: iface: No such file or directory
cat: eth0: No such file or directory
cat: inet: No such file or directory
cat: dhcp: No such file or directoryso please if you could tell me the command line protocol I'd appreciate it because I'm apparently too ignorant to figure it out

also I don't have  Manager (I think) I do have,
Network Tools in Administration (but I can't change anything) and Network Connections in Preferences (but there are no connections in it)

also I did have a internet connection but my computer was shut down incorrectly and that's when I lost the connection and I can't get it back.

Never had a Network problem before so I don't know much about it

and I did *sudo /etc/init.d/networking restart* and it said it worked

---

### Post by bab1 on 2012-04-13
> **The Black Night said:**
> Thank you for your prompt reply (didn't expect it to happen so quickly)

I still don't get it (which is embarrassing sense I've been a user since 7.04) but I did try these and a few (many) others!

so please if you could tell me the command line protocol I'd appreciate it because I'm apparently too ignorant to figure it out

also I don't have  Manager (I think) I do have,
Network Tools in Administration (but I can't change anything) and Network Connections in Preferences (but there are no connections in it)

also I did have a internet connection but my computer was shut down incorrectly and that's when I lost the connection and I can't get it back.

Never had a Network problem before so I don't know much about it

and I did *sudo /etc/init.d/networking restart* and it said it worked
Sometimes it helps for: (1) you to understand what you are doing and (2) us to understand more about your system.

As to the first part when you use the incantation ```
sudo cat /etc/network/interfaces
```

You are asking root (that's the *sudo* part) to manipulate and display (that's the *cat* part) the file (/etc/network/interfaces).  All the rest (code auto eth0 iface eth0 inet dhcp) is data that should be displayed.  

Since the cat command doesn't understand the data part you get this ```
cat: eth0: No such file or directory
cat: iface: No such file or directory
cat: eth0: No such file or directory
cat: inet: No such file or directory
cat: dhcp: No such file or directory
```
From the man pages```
**[COLOR="Red"]concatenate files and print on the standard output[/COLOR]**
```

This just means the cat appends the contents of 1 or more files and displays it to the screen.  If you are cat'ing 1 file you are just displaying it's contents.

Let's start with what you are trying to accomplish here.  Do you want to configure an interface statically (via config files); or set up auto configuration via dhcp (via config files) or set an auto interface manager (Network-Manager)?

---

### Post by The Black Night on 2012-04-16
Thanks for explaining the cat command to me :)


I know its not a problem with the internet connection because my other computers can still connect and its not a hardware problem because I can connect to the internet on my windows side of the same computer, Ubuntu can see the Ethernet port in network tools
but I cant change it in Network Connections or anywhere else. I therefore Believe I want to set up an auto configuration via dhcp 


I want to change this (I know you cant change these settings)

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-Devices-NetworkTools.png[/IMG]


to this

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-Devices-NetworkTools-1.png[/IMG]

---

### Post by bab1 on 2012-04-16
> **The Black Night said:**
> Thanks for explaining the cat command to me :)
You are welcome.> 
I know its not a problem with the internet connection because my other computers can still connect and its not a hardware problem because I can connect to the internet on my windows side of the same computer, Ubuntu can see the Ethernet port in network tools
Agreed.> 
but I cant change it in Network Connections or anywhere else. 
There has to be some place that sets the configuration.  That's what we need to find out.  Then we can set the configuration parameters.> 
I therefore Believe I want to set up an auto configuration via dhcp
Maybe, maybe not.  If we can find out where (via a network interface manager), then we can set up how (via static files or DHCP.> 

I want to change this (I know you cant change these settings)

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-Devices-NetworkTools.png[/IMG]


to this

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-Devices-NetworkTools-1.png[/IMG]
Nope.

The loopback interface (lo) is a *[COLOR="Blue"]virtual interface [/COLOR]* that always has an address in the 127.0.0.0/8 network.  It must always be configured.  This is how you test ping yourself (the localhost).

The interface eth[0] is a [COLOR="Green"]*real interface*[/COLOR].  This is the network interface card (NIC) that you plug the Ethernet cable into.  FYI: this card is shown as available but inactive (it does not have an IP address assigned to it.

So our task is twofold.  1. find out via what mechanism (network manager or ...) is being used to manage the eth0 interface and 2. decide whether to configure the interfaces tatically or via dhcp.

First let's see what is in the directory */etc/NetworkManager*.  What is the output of```
ls -la /etc/NetworkManager
```

This is asking the system to list (all and in long format) the contents of the */etc/NetworkManager* directory.  Even though I have no Network-Manager installed I have this```
ls -la /etc/NetworkManager
total 20
drwxr-xr-x   3 root root  4096 2011-03-29 19:13 .
drwxr-xr-x 143 root root 12288 2012-04-16 14:27 ..
drwxr-xr-x   2 root root  4096 2011-03-29 13:26 VPN

```

---

### Post by The Black Night on 2012-04-17
Ok got this


> desktop:~$ sudo ls -la /etc/NetworkManager 
total 32
drwxr-xr-x   5 root root  4096 2012-02-14 05:47 .
drwxr-xr-x 139 root root 12288 2012-04-16 22:27 ..
drwxr-xr-x   2 root root  4096 2012-02-14 05:47 dispatcher.d
-rw-r--r--   1 root root   315 2011-05-26 13:59 nm-system-settings.conf
drwxr-xr-x   2 root root  4096 2011-05-26 14:00 system-connections
drwxr-xr-x   2 root root  4096 2012-02-14 05:47 VPN


---

### Post by bab1 on 2012-04-17
> **The Black Night said:**
> Ok got this

This sure looks like the interfaces are configured via the app Network-Manager.  If this is so then the file /etc/network/interfaces and possibility /etc/resolvconf are not being used.

I don't use network manager at all.  I have removed it from my desktop set up.  Is your machine a workstation or a laptop?  Is is mobile in the sense that you take it places?

---

### Post by newbie-user on 2012-04-17
> **The Black Night said:**
> (running Ubuntu 10.04.4 LTS AMD 64)

Ok, I need some help with the final part of some instructions I found elsewhere on this board.

Did all that, got this


This is where I don't get it 

What is this telling me to do

Thank you all in advance :)

This just tells you to add those lines to your /etc/network/interfaces file. So the file should look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by bab1 on 2012-04-17
> **newbie-user said:**
> This just tells you to add those lines to your /etc/network/interfaces file. So the file should look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
[COLOR="Green"]Edit: Soory I was replying to the wrong person here.  I have amended my reply to:[/COLOR]

I don think the OP needs to do that that.  It won't work as long as Network-Manager is in control.

The forum is full of folks complaining about the *interfaces *file being overwritten.

---

### Post by The Black Night on 2012-04-18
I use a workstation.
because it said I have a network manger I went and looked around for in and came up with this 

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-NetworkConnections.png[/IMG]

[IMG]http://i1055.photobucket.com/albums/s520/The_Black_Night/Screenshot-NetworkConnections-1.png[/IMG]

Does this just need to be re-configured ?

---

### Post by bab1 on 2012-04-18
> **The Black Night said:**
> I use a workstation.
because it said I have a network manger I went and looked around for in and came up with this 
...
Does this just need to be re-configured ?

I believe so. That is the GUI interfaces for Network-Manager. 

But before you do that, could you post the output of this```
cat /etc/Network-Manager/nm-system-settings.conf
```

This will be the configuration file for Network-Manager.

---

### Post by The Black Night on 2012-04-18
> 
desktop:~$ sudo cat /etc/Network-Manager/nm-system-settings.conf
[sudo] password : 
cat: /etc/Network-Manager/nm-system-settings.conf: No such file or directory
whats next?

---

### Post by bab1 on 2012-04-18
> **The Black Night said:**
> whats next?

Somehow you have to learn to be resourceful yourself.  

I made a typo and you blindly followed.  Before what's next; is:  I looked myself land found the file and it is ```
/etc/NetworkManager/nm-system-settings.conf
```

So while I mistyped it and that is a mistake.  You need to be just a little self sufficient, don't you think?

You gave me the file listing in post #7.

---

### Post by Iowan on 2012-04-18
> **bab1 said:**
> ... I mistyped it and that is a mistake. There goes your perfect record ;)

@OP I suspect you can add a connection via Network Manager (the ADD button), but I, too, am curious what's in */etc/NetworkManager/nm-system-settings.conf*

---

### Post by bab1 on 2012-04-19
> **Iowan said:**
> There goes your perfect record ;)

...
Aw... Ya caught me!

---

### Post by The Black Night on 2012-04-19
Sorry I do tend to blindly follow instruction.

> 
desktop:~$ sudo cat /etc/NetworkManager/nm-system-settings.conf
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

---

### Post by bab1 on 2012-04-19
> **The Black Night said:**
> Sorry I do tend to blindly follow instruction.

Okay.  We got to where we need to be.

It appears that the wired network is NOT managed by Network Manager.  This means we can use the /etc/network/interfaces file for configuration.

In looking again at the info you supplied, we have this for the interfaces (eth0 and lo)```
-desktop:~$ sudo ifconfig -a
**[COLOR="Red"]eth0 [/COLOR]**Link encap:Ethernet HWaddr 00:01:80:5c:7d:93
BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:23 Base address:0x2000

**[COLOR="Blue"]lo [/COLOR]**Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:88 errors:0 dropped:0 overruns:0 frame:0
TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:6560 (6.5 KB) TX bytes:6560 (6.5 KB)

```

And we have this for the contents of the /etc/network/interfaces file```
ldesktop:~$ sudo cat /etc/network/interfaces
auto lo
iface **[COLOR="Blue"]lo[/COLOR]** inet loopback
```

If you want to use DHCP to supply the IP addressing then you can the following to the bottom of the */etc/network/interfaces* file ```
auto eth0
iface eth0 inet dhcp
```

What does it mean?  The first line says *"start the interface eth0 automatically upon bootup*.  The second line says *"ask the dhcp server for the Ip addressing parameters.*

To edit the */etc/network/interfaces* file you must be the user *root*.   So to edit this file you need to open the file as root by using the following from the CLI ```
gksudo gedit /etc/network/interfaces
```

With the file open you can add the 2 lines of code and the save the file.  Use the cat command to view your work (*cat /etc/network/interfaces*).  If this looks good you can reboot the system and see what happens.  You can see the configuration with this ```
ifconfig -a
```

Post the output here for us to see.

---

### Post by The Black Night on 2012-04-19
> desktop:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:01:80:5c:7d:93  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::201:80ff:fe5c:7d93/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18161 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12475 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:24161880 (24.1 MB)  TX bytes:1302859 (1.3 MB)
          Interrupt:23 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)I write this from my now functioning Ubuntu computer my Internet  is back :D
Many thanks to all and especially to bab1 for his patience :)

I apologize for my short answers but I'm not a man of many words.

sincerely 

The Black Night



[COLOR=#000000][/COLOR]
[COLOR=#000000][/COLOR]

---

