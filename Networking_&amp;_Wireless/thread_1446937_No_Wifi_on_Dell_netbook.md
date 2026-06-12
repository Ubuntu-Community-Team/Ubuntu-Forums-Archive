---
title: "No Wifi on Dell netbook"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by stanhalen on 2010-04-04
When I go to network connections wifi does not come up for a choice. 
It just lists wired connections.
I am on a dell inspiron 910.
also has xfce 4

---

### Post by stanhalen on 2010-04-04
when i type the command 

lshw -C network

i get
 *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff

---

### Post by chili555 on 2010-04-04
Can you walk the Dell over to the router, hook up a wired connection and then go to System > Administration > Hardware Drivers and activate your Broadcom drivers?

---

### Post by stanhalen on 2010-04-04
> **chili555 said:**
> Can you walk the Dell over to the router, hook up a wired connection and then go to System > Administration > Hardware Drivers and activate your Broadcom drivers?

ok i activated the driver.
is that it? because wireless options are still not coming up.

---

### Post by alexdelprogramador on 2010-04-04
> **stanhalen said:**
> 
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation


Hello stanhalen

Im new in that forum, but not as well on wireless under linux :guitar:


Ok, I think I can help you.

you have an broadcom pci wireless card with a BCM4312 chip.

On start, It will work on Unbuntu debian linux without troubles,but....

can you type this:

> iwconfig

and also this command, because Im afraid you dint up the device.


> ifconfigyou can have troubles with the card because it couldn't be up when you try to connect to a wireless ap.


write as what happend ;)

Wating your response :popcorn:

---

### Post by stanhalen on 2010-04-04
> **alexdelprogramador said:**
> Hello stanhalen

Im new in that forum, but not as well on wireless under linux :guitar:


Ok, I think I can help you.

you have an broadcom pci wireless card with a BCM4312 chip.

On start, It will work on Unbuntu debian linux without troubles,but....

can you type this:



and also this command, because Im afraid you dint up the device.


you can have troubles with the card because it couldn't be up when you try to connect to a wireless ap.


write as what happend ;)

Wating your response :popcorn:

laptop@laptop-laptop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

laptop@laptop-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:70:d0:d7:c1  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fed0:d7c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2622803 (2.6 MB)  TX bytes:431468 (431.4 KB)
          Interrupt:27 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:840 (840.0 B)  TX bytes:840 (840.0 B)

---

### Post by bkratz on 2010-04-04
How about the contents of 

rfkill list

?

---

### Post by stanhalen on 2010-04-04
> **bkratz said:**
> How about the contents of 

rfkill list

?
rkill list?

---

### Post by bkratz on 2010-04-04
rfkill list

r[COLOR="Red"]f[COLOR="Black"]kill list
[/COLOR][/COLOR]

---

### Post by stanhalen on 2010-04-04
laptop@laptop-laptop:~$ rfkill list
0: compal-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: compal-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

---

### Post by bkratz on 2010-04-04
since you tried to activate the driver earlier, do you remember if it said STA?

Could you post the following again?

sudo lshw -C network

and with the wired connection unplugged

sudo iwlist scan


The reason for the last one was just to see if the wireless switch was on! Sorry!

---

### Post by stanhalen on 2010-04-04
sudo lshw -C network
sudo] password for miriam: 
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:f0200000-f0203fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d0:d7:c1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.104 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0610000-f0610fff(prefetchable) memory:f0600000-f060ffff(prefetchable) memory:f0620000-f063ffff(prefetchable)

---

### Post by stanhalen on 2010-04-04
laptop@laptop-laptop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by alexdelprogramador on 2010-04-04
ok, I have one solution: install it manualy :lolflag:

that conclussion is made that Im really disapointed to use ndiswrapper to use a simple wireless card to connect to a wireless ap.

Ndiswrapper emulate a possible firmware card in linux ussing a windows drivers.... ahjjj :mad:

Its difficult if you are an unexperienced user, but you have to try it.... or not? :p


I can see that this type of chip is supported under linux:

[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

It uses a b43 firmware... um... interesting... :p

so the oficial firmware page is:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

look at the readme.txt file:

[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

there is a note refering of [B]System->Administration->Hardware Driver

[/B]> 

Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.


so, do it

and im sure it will work ;)

---

### Post by bkratz on 2010-04-04
This particular chip is not supported by b43 in the current kernels, not until 2.6.32.

You need the STA driver

Do

sudo apt-get install bcmwl-kernel-source

with the wired connection in, for some reason your earlier activation did not take.

---

### Post by alexdelprogramador on 2010-04-04
> **bkratz said:**
> This particular chip is not supported by b43 in the current kernels, not until 2.6.32.

You need the STA driver

Do

sudo apt-get install bcmwl-kernel-source

with the wired connection in, for some reason your earlier activation did not take.

yeah!!! 

we responsed the same at the same time :lolflag:

bye.
I supose its solved
 ):P

---

### Post by bkratz on 2010-04-04
> **alexdelprogramador said:**
> yeah!!! 

we responsed the same at the same time :lolflag:

bye.
I supose its solved ):P



Well, I type slow and inaccurate, I thought you were saying b43 was ok. Sorry!

See that little bit took me 5 minutes!

---

### Post by alexdelprogramador on 2010-04-04
> **bkratz said:**
> Well, I type slow and inaccurate, I thought you were saying b43 was ok. Sorry!

See that little bit took me 5 minutes!

:lolflag: :lolflag: :lolflag:

---

### Post by stanhalen on 2010-04-04
miriam@miriam-laptop:~$ sudo apt-get install bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmwl-kernel-source

soooooo confused.

---

### Post by bkratz on 2010-04-04
you did have the ethernet plugged in right?

---

### Post by stanhalen on 2010-04-04
yup yup.
I am about to just put normal ubuntu on to this.

---

### Post by bkratz on 2010-04-04
> **stanhalen said:**
> yup yup.
I am about to just put normal ubuntu on to this.

Well normal Ubuntu has this driver on the Live CD, not sure about yours. You could check by following the directions in this post

[http://art.ubuntuforums.org/showpost.php?p=8309372&postcount=5](http://art.ubuntuforums.org/showpost.php?p=8309372&postcount=5)

---

### Post by oleink on 2010-04-04
[LIST]
[*]hey I've got an inspiron too.  I actually wrote a thing on getting wireless on a dell inspiron.  Its not too hard.  You need to plug into your router though.  Plug in use the wired connection to download wine from the software center.  Then go to System->Administration->Hardware Drivers and install STA wireless driver.  it covers your card!!!!!!!!!!:popcorn:
[/LIST]

---

### Post by wojox on 2010-04-04
If it can't find it run:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```

---

### Post by stanhalen on 2010-04-04
> **bkratz said:**
> Well normal Ubuntu has this driver on the Live CD, not sure about yours. You could check by following the directions in this post

[http://art.ubuntuforums.org/showpost.php?p=8309372&postcount=5](http://art.ubuntuforums.org/showpost.php?p=8309372&postcount=5)
I was going to download the live cd.

---

### Post by stanhalen on 2010-04-04
> **wojox said:**
> If it can't find it run:

```
sudo apt-get update && sudo apt-get install bcmwl-kernel-source
```
thanks but that did not work as well.

---

### Post by bkratz on 2010-04-04
> **stanhalen said:**
> thanks but that did not work as well.

One more try, how about going to synaptic package manager( system>>administration>>synaptic package manager) and press reload and just search for it, then select it and install from there.

---

### Post by stanhalen on 2010-04-04
> **bkratz said:**
> One more try, how about going to synaptic package manager( system>>administration>>synaptic package manager) and press reload and just search for it, then select it and install from there.

ok i searched for 
bcmwl but all I got was  bcmwl-modaliases
so I reinstalled it. i don't think that did anything.

---

### Post by bkratz on 2010-04-04
> **stanhalen said:**
> ok i searched for 
bcmwl but all I got was  bcmwl-modaliases
so I reinstalled it. i don't think that did anything.




Sorry, I looked there too, I must have been wrong or it is in a different repository. I don't know. Well I do know this will work if you are willing to try

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Read the readme before you decide.

---

### Post by alexdelprogramador on 2010-04-04
> **bkratz said:**
> you did have the ethernet plugged in right?

ok, on oldest posts, i've seen that he wrote:

> 

laptop@laptop-laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:21:70:d0:d7:c1  
          inet addr:192.168.0.104  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::221:70ff:fed0:d7c1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2287 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2622803 (2.6 MB)  TX bytes:431468 (431.4 KB)
          Interrupt:27 

It says to me that is connected with wired interface called **eth0** and hast 192.168.0.104 ip

so, just only type:

> sudo apt-get update && apt-get upgradeand then:

> sudo apt-get install bcmwl-kernel-source

or

> Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

Its all

tell us what happend

---

