---
title: "Configuring Kismet"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by havic54 on 2009-02-11
I have the latest version of Kismet downloaded, but I can't seem to get it configured right. I opened up the .conf file and changed the "suiduser=" to myself, but still nothing. I think I need to change the "source=" to be apply to my comptuer, but I'm not sure exactly how to do this. I'm on an Hp Pavilion zd800 if this helps anyone to help me? As of now, when I run it in the terminal I get

> Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (addme): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.


Any help would be much appreciated. Thanks.

---

### Post by havic54 on 2009-02-12
Gonna give this a quick bump and see if I get anything...

---

### Post by chili555 on 2009-02-12
It's asking you to amend */etc/kismet/kismet.conf* My relevant lines looks like this:```
# User to setid to (should be your normal user)
suiduser=chili

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,eth1,intel
```You can learn more by reading /usr/share/doc/kismet/README.gz, specifically sections 9 and 12.

---

### Post by havic54 on 2009-02-12
I've tried making changes to the .conf file and it won't let me. It says I don't permission to. I have a Broadcom 54g Airforce One wireless card, and I'm not sure if Kismet supports this driver...or if that even matters. I'm usually able to figure these kinds of things out on my own from research, but not this time.

---

### Post by chili555 on 2009-02-12
To edit your file, you must edit as root, like this:```
sudo gedit /etc/kismet/kismet.conf
```When the text editor opens, you can make your changes, save and close.

Read Section 12 of the README like this:```
less /usr/share/doc/kismet/README.gz
```You can then scroll back and forth in the file to read your relevant parts.

Find the driver your card uses with:```
sudo lshw -C network
```One of the entries will relate to your AirForce One and will show the interface and driver.

Post back if you get stuck.

---

### Post by havic54 on 2009-02-13
Alright, I got everything working. Thanks alot!

One last questiong, how do i get my wireless card out of monitor mode or restart it?

---

### Post by azwar on 2009-02-13
Hi chili555,

I have ubuntu 8.10, when I print ```
sudo lshw -C network
```
I get this ```
azwar@linux-intrepid:~$ sudo lshw -C network
[sudo] password for azwar: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:2f:3e:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.3 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

Then, I configure the kismet.conf like this but still not working
```
# User to setid to (should be your normal user)
#suiduser=azwar

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=ath5k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,ath5k
```

Is this the correct way to change the source?

---

### Post by chili555 on 2009-02-14
> **havic54 said:**
> Alright, I got everything working. Thanks alot!

One last questiong, how do i get my wireless card out of monitor mode or restart it?Glad it's working for you!

Try this:```
sudo iwconfig eth1 mode managed
```Substitute your interface if it's not eth1. Network Manager should get busy immediately and connect.

---

### Post by chili555 on 2009-02-14
> **azwar said:**
> Hi chili555,

I have ubuntu 8.10, when I print ```
sudo lshw -C network
```
I get this ```
azwar@linux-intrepid:~$ sudo lshw -C network
[sudo] password for azwar: 
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 01
       serial: 00:19:7e:2f:3e:4c
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.2.3 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg

```

Then, I configure the kismet.conf like this but still not working
```
# User to setid to (should be your normal user)
#suiduser=azwar

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=ath5k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
**source=none,none,ath5k**
```

Is this the correct way to change the source?I doubt it. Isn't the answer given in your question?> source=ath5k,wlan0,atherosTry that, save and close your text editor and start kismet with:```
sudo kismet
```If it doesn't like your source lines, it will tell you.

---

### Post by azwar on 2009-02-14
> If it doesn't like your source lines, it will tell you. 

I get this massage when run ```
sudo kismet
```
```
azwar@linux-intrepid:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ath5k): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.

```

Can you advice me what should I put, that I maybe missing in the kismet.conf

---

### Post by chili555 on 2009-02-15
Please post the part of your kismet.conf that corresponds to this part of mine:```
# User to setid to (should be your normal user)
suiduser=chili

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,eth1,intel
```Also please post:```
ifconfig
```We'll figure it out!

---

### Post by azwar on 2009-02-15
Here,
```
azwar@linux-intrepid:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1b:24:07:19:fb  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123272 (123.2 KB)  TX bytes:123272 (123.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:7e:2f:3e:4c  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:7eff:fe2f:3e4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9545 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7040345 (7.0 MB)  TX bytes:1994931 (1.9 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-7E-2F-3E-4C-65-34-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

kismet.conf

```
# User to setid to (should be your normal user)
#suiduser=azwar

# Sources are defined as:
# source=ath5k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,ath5k
```
I've manually change the 
# source=ath5k,wlan0,atheros[11] 
and I also add ath5k at the end of this line 
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,ath5k

---

### Post by chili555 on 2009-02-15
Please change this:```
#suiduser=azwar
```to remove the leading # so it reads like this:```
suiduser=azwar
```Also, change this:```
# Sources are defined as:
# source=ath5k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,ath5k
```to read like this:```
# Sources are defined as:
# source=ath5k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath5k,wlan0,atheros
```I apologize if I was not clear in my previous posts that the line you quoted was *incorrect.* Perhaps you are unaware that the lines behind the # symbol are comments that are ignored by the program; they are there to explain things to the human reader only.

After you make the changes, save and close your text editor, please re-run:```
sudo kismet
```Please let us know how it goes.

---

### Post by azwar on 2009-02-16
Hi chili555,

At last I can used the kismet. Thank you so much for helping me. just one more question. Does kismet should be in monitor mode just like the aircrack-ng. If yes, I will change the network interface.

Thank you so much.

---

### Post by chili555 on 2009-02-17
Your interface *does *need to be in monitor mode. however, Kismet takes care of this for you, as you know if you got it working! If you can successfully run Kismet, then don't change a thing.

---

### Post by kevdog on 2009-02-17
I would just like to add a few things

Thanks Chili555 for great input.

Running kismet places your card in monitor mode on the interface specified in the kismet.conf file.  Again for kismet to work you need to make sure your card can go into monitor mode (that means all you ndiswrapper users out there -- you are out of luck)

Second when quitting kismet, it leaves your wireless card stuck in monitor mode.  To revert back to Managed mode (client mode), the commands would be similar to the following:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up

After possibly waiting a few seconds or minutes -- iwlist scan should repopulate the local networks.

---

### Post by azwar on 2009-02-23
> **kevdog said:**
> I would just like to add a few things

Thanks Chili555 for great input.

Running kismet places your card in monitor mode on the interface specified in the kismet.conf file.  Again for kismet to work you need to make sure your card can go into monitor mode (that means all you ndiswrapper users out there -- you are out of luck)

Second when quitting kismet, it leaves your wireless card stuck in monitor mode.  To revert back to Managed mode (client mode), the commands would be similar to the following:

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode Managed
sudo ifconfig wlan0 up

After possibly waiting a few seconds or minutes -- iwlist scan should repopulate the local networks.

yes, my card get stuck when quitting kismet. I'm not able to connect to existing network. Thank you valueable posting.

---

### Post by bgalfond on 2009-03-16
so I'm guessing that with this, my driver will not work with kismet?

lshw -C network
  *-network DISABLED
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wifi0
       version: 01
       serial: 00:21:63:aa:8b:98
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes **driver=ath_pci** latency=0 module=ath_pci multicast=yes promiscuous=yes wireless=IEEE 802.11g

---

### Post by JayUK20 on 2009-07-19
Thought I'd post here instead of starting a new thread. When I sudo kismet I get the following:

> wubi@ubuntu:~$ clear
wubi@ubuntu:~$ sudo kismet
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (ath9k): Opening none source interface none...
FATAL: Please configure at least one packet source.  Kismet will not function if no packet sources are defined in kismet.conf or on the command line.  Please read the README for more information about configuring Kismet.
Kismet exiting.
Done.


kismet.conf looks like this:

> # Sources are defined as:
# source=ath9k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=none,none,ath9k

---

### Post by chili555 on 2009-07-19
I suggest you amend your kismet.conf thus:```
# Sources are defined as:
# source=ath9k,wlan0,atheros[11]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ath9k,wlan0,atheros
```I hope I am not being too blunt, but I hoped this was all very clear if you read the entire thread. Kismet is not going to work with *source=none*.

---

### Post by JayUK20 on 2009-07-19
Thanks I forgot to quote the fixed version, it's the same as you have quoted there, when I fix the errors there and I run sudo kismet I then get the following:

> Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: Unknown capture source type 'ath9k' in source 'ath9k,wlan0,atheros'

My chipset is AR928X, it looks like ath9k does not support injection, maybe thats the problem

---

### Post by chili555 on 2009-07-19
> it looks like ath9k does not support injectionKismet is not injection, it is merely monitoring. ath9k is not mentioned in the README:```
less /usr/share/doc/kismet/README.gz
```I see that ath5k is listed, however. I'd suggest blacklisting ath9k and try, at least experimentally, loading ath5k and see if Kismet works.

---

### Post by JayUK20 on 2009-07-20
Right ok I know how to blacklist my driver but I do not understand how to enable ath5k:

> Enabling ath5k

To enable ath5k in the kernel configuration, you must first enable mac80211:

Networking  --->
  Wireless  --->
    <M> Improved wireless configuration API
    <M> Generic IEEE 802.11 Networking Stack (mac80211)

Please note that there is another 802.11 networking stack:

    <M> Generic IEEE 802.11 Networking Stack

You do not need this. This option enables the old SoftMAC stack we hope to kill one of these days. You can still safely enable this though.

You can then enable ath5k in the kernel configuration under

Device Drivers  --->
  [*] Network device support  --->
        Wireless LAN  --->
          <M>   Atheros 5xxx wireless cards support

---

### Post by chili555 on 2009-07-20
Do you not have ath5k natively in your system?```
chili@LAPTOP60:~$ locate ath5k
/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath5k
/lib/modules/2.6.28-11-generic/kernel/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/ath5k
/lib/modules/2.6.28-13-generic/kernel/drivers/net/wireless/ath5k/ath5k.ko
/lib/modules/2.6.28-13-generic/updates/ath5k.ko
```I'd think all you need to do is:```
sudo modprobe ath5k
```Let us know.

---

### Post by JayUK20 on 2009-07-20
Hey, thanks for the reply. When I type what you suggested it doesn't return anything:

> wubi@ubuntu:~$ sudo modprobe ath5k
wubi@ubuntu:~$ 

However I ran modprobe -l and went through the list and everything in your posted you quoted above is there.

---

### Post by chili555 on 2009-07-20
When you issue a command and it returns nothing, that means it was completed with no errors or warnings. Did you blacklist ath9k and reboot? Are you sure ath9k is *not* loaded? ```
lsmod | grep ath
```If all you have loaded now is ath5k, amend your kismet.conf and see if it runs.

---

### Post by JayUK20 on 2009-07-20
The ath5k is now loaded but I no longer have access to the wireless connection.

---

### Post by chili555 on 2009-07-20
Well, it's pretty clear now. ath5k won't bind to and drive your wireless card. ath9k drives your card well, I am assuming. ath9k is not supported in Kismet. Therefor, it seems Kismet won't work for you. Perhaps a newer version of Kismet will add ath9k support. I'd unblacklist ath9k and reload it:```
sudo modprobe ath9k
```

I just saw this: [http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456](http://www.kismetwireless.net/Forum/General/Messages/1231702725.208456)

You might try changing your kismet.conf to read like this:```
source=ath5k,wlan0,atheros
```Then run:```
sudo kismet
```Does it run?

---

### Post by JayUK20 on 2009-07-20
I get this error here:

> Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (atheros): Enabling monitor mode for ath5k source interface wlan0 channel 6...
FATAL: GetIFFlags: interface wlan0: No such device

I know the ath5k drivers are loaded but do I need to turn the wireless on? I tried **sudo wlan0 up** but I get another error which says:

> wlan0: ERROR while getting interface flags: No such device

---

### Post by chili555 on 2009-07-20
> I know the ath5k drivers are loadedWe want the driver that actually works with your card loaded; that's *not* ath5k.> do I need to turn the wireless on?Yes, indeed.> sudo wlan0 upI assume you meant **sudo [COLOR="Red"]ifconfig[/COLOR] wlan0 up**. Just to clarify, we want to try, experimentally:
#un-blacklist and load ath9k
#unload ath5k: ```
sudo rmmod ath5k
```
#amend kismet.conf to tell it you are using ath[COLOR="Red"]5[/COLOR]k, even though we know you are using ath[COLOR="Red"]9[/COLOR]k. 
#run kismet.

Does the little trick we palyed on Kismet allow it to run and gather data?

---

### Post by JayUK20 on 2009-07-20
That little trick worked a treat! Thanks very much for helping out, however it seems my card does not support injection of packets but this thread has been very useful nonetheless.

---

### Post by chili555 on 2009-07-20
Glad Kismet is working for you!

---

### Post by zuruntu on 2009-11-08
Hello i am a newbie in ubuntu, andwont to use kismet, but i dont know how tocongigure correctly kismet.conf.
After configured kismet.conf and start sudo kismet i have this message:

launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (kismet): Enabling monitor mode for orinoco source interface wlan0 channel 6...
FATAL: Failed to retrieve list of private ioctls 95:Operation not supported
Done.

so, who know please help me....

---

### Post by chili555 on 2009-11-08
May we please see the part of your kismet.conf file that looks like this:```
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=blah,blah,blah
```As well as:```
sudo lshw -C network
```Thanks.

---

### Post by zuruntu on 2009-11-09
sudo lshw -c network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 02
       serial: 00:18:de:37:97:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:29 memory:64000000-64000fff
  *-network
       description: Ethernet interface
       product: NetLink BCM5787M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:16:36:ab:84:a1
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.99 duplex=full firmware=5787m-v3.13 ip=192.168.1.101 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:28 memory:64100000-6410ffff
  *-network
       description: HFA384x/IEEE
       product: Version 01.02
       vendor: INTERSIL
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network
       description: Wireless interface
       physical id: 2
       logical name: eth1
       serial: 00:07:13:68:13:50
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco driverversion=0.15 firmware=Intersil 1.5.6 link=no multicast=yes wireless=IEEE 802.11b

---

### Post by zuruntu on 2009-11-09
# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=orinoco,wlan0,kismet

---

### Post by chili555 on 2009-11-09
> # YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=orinoco,wlan0,kismetPlease change this to:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=[COLOR="Red"]ipw3945[/COLOR],wlan0,[COLOR="Red"]Intel[/COLOR]
```Proofread carefully, save and close your text editor. Rerun sudo kismet and please let us know.

---

### Post by zuruntu on 2009-11-09
thanks, but i have a prism 2 one adapter, what i must to change to use this one? THANK

---

### Post by zuruntu on 2009-11-09
After change of kismet conf
source=[COLOR=Red]ipw3945[/COLOR],wlan0,[COLOR=Red]Intel[/COLOR]i have this message
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
FATAL: No packsources were enabled.  Make sure that if you use an enablesource line that you specify the correct sources.
Done.

---

### Post by chili555 on 2009-11-09
I was confused. Now I see that you have *two* wireless devices and wish to use the prism for Kismet. It should read:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=orinoco,eth1,Prism
```This may or may not work correctly, as shown in the README:> The Orinoco drivers which have mainlined into the Linux kernel do support monitor mode, however only specific firmware versions are supported and often they do not work. An up-ported version of the older Orinoco drivers which more reliably supported rfmon may be available at: [http://www.projectiwear.org/~plasmahh/orinoco.html](http://www.projectiwear.org/~plasmahh/orinoco.html)   Generally, Orinoco cards are not recommended for use with Kismet due to these limitations.I use Kismet successfully with my Intel 3945 ABG, although it is a bit difficult to get back out of monitor mode.

---

### Post by zuruntu on 2009-11-09
thanks but is work with 2007 version, :)
(i reinstall kismet)

---

### Post by zuruntu on 2009-11-12
it work, :)

---

### Post by georg.65 on 2009-11-24
Hello, yes I'm new on Linux/Ubuntu, before I posting this, I've read same thread, but still can't get working kismet.

Maybe the **Broadcom STA wireless driver (for BCM4312) **work to well for getting me online to forget to shutdown on monitor mode.


ABOUT MY WIRELESS CARD (Info from WINXP)
-----------------------------------------------------------------------------------
Ethernet adapter Wireless Network Connection: 
 
        Media State . . . . . .. . . : Media disconnected 
        Description . . . . . . . . . : **Dell Wireless 1395 WLAN Mini-Card **
        Physical Address. . . . . . : 00-21-00-D8-BD-56

-----------------------------------------------------------------------------------


Ok here is my result with Ubuntu 9.10 Karmic&#65279;

-----------------------------------------------------------
orion@orion-laptop:~$ sudo lshw -c network
  *-network               
       [B]description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth2
       version: 01
       serial: 00:21:00:d8:bd:56[/B]
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:9c000000-9c003fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:23:5a:45:17:a4
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:32 ioport:3000(size=256) memory:96010000-96010fff(prefetchable) memory:96000000-9600ffff(prefetchable) memory:96020000-9602ffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
-----------------------------------------------------------------------

orion@orion-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:5a:45:17:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:32 Base address:0xc000 

**eth2      Link encap:Ethernet  HWaddr 00:21:00:d8:bd:56  **
          inet6 addr: fe80::221:ff:fed8:bd56/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:119.31.33.47  P-t-P:192.200.1.21  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:40 errors:0 dropped:0 overruns:0 frame:0
          TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:10706 (10.7 KB)  TX bytes:2882 (2.8 KB)
--------------------------------------------------------

orion@orion-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[B]eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
[/B]           
vboxnet0  no wireless extensions.

pan0      no wireless extensions.

ppp0      no wireless extensions.

---------------------------------------------------------------------------

And now from my modificated kismet.conf


orion@orion-laptop:~$ sudo gedit /etc/kismet/kismet.conf
[sudo] password for orion:


# Kismet config file
# Most of the "static" configs have been moved to here -- the command line
# config was getting way too crowded and cryptic.  We want functionality,
# not continually reading --help!

# Version of Kismet config
version=2007.09.R1

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to (should be your normal user)
[B]suiduser=orion
[/B] 
# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[B]source=bcm43xx,eth2,Broadcom
[/B] 
-------------------------------------------------------------------
and the result after I'm starting kismet

orion@orion-laptop:~$ sudo kismet
[sudo] password for orion: 
Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (Broadcom): Enabling monitor mode for bcm43xx source interface eth2 channel 6...
**FATAL: Failed to set monitor mode: Invalid argument.  This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it.  Make sure you have a version of your drivers that support monitor mode, and consult the troubleshooting section of the README.**
Done.


Yes it's a problem about the driver,


with the System->Administration->Synaptic Package Manager I've removed the package bcmwl-kernel-source for Broadcom 802.11 Linux STA wireless driver source

System->Administration->HardwareDrivers I get the info, now b43 is activeted but I still can't get kismet in monitor mode and don't have internet connection to.

When I've do this I was online with USB EDGE Modem Stick.

Please help ;)

---

### Post by serejj on 2009-11-25
for atheros users and others...

suiduser=your user here

if you use madwifi:
source=madwifi_g,wifi0,Atheros

if you use ath5k or ath9k:
source=ath5k,wlan0,Atheros

since kismet don't support the ath9k driver you must use ath5k in the conf file like above and everything work's fine.

"for advance users only"
if anybody need help to config the kismet_ui.conf or put kismet talking :D or some other advance config's post here

remember this §erejj is your friend but google is your best friend

---

### Post by thebigbradwolf on 2009-12-26
So after reading through this and several other forums on the topic I'm still having a bit of difficulty configuring kismet, but after the success rate of this thread I decided not to give up. I've got a Wireless WiFi Link 5100. My output for sudo lshw -C network is:
```
description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wmaster0
       version: 00
       serial: 00:22:fa:af:3e:0a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.102 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:b8100000-b8101fff
```

my output for ifconfig is:
```
wlan0     Link encap:Ethernet  HWaddr 00:22:fa:af:3e:0a  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::222:faff:feaf:3e0a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11365 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10570 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9142627 (9.1 MB)  TX bytes:1882004 (1.8 MB)
```
and this is how i edited my kismet.conf:
```
# Sources are defined as:
# source=iwlagn,wlan0,intel[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwlagn,wlan0,intel
```

as well as: 
```
# User to setid to (should be your normal user)
#suiduser=anon
```

Thank you in advance for saving all of us newbs from i newbiness.

---

### Post by chili555 on 2009-12-28
The module *iwlagn* is not listed in the README for Kismet, however, there are reports that this may work:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl4965,wlan0,intel
```Please try it and let the searchers know.

---

### Post by Gi0tis on 2009-12-28
> **chili555 said:**
> The module *iwlagn* is not listed in the README for Kismet, however, there are reports that this may work:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl4965,wlan0,intel
```Please try it and let the searchers know.
Tried it on my laptop with an intel wifi 5100 and kismet was up after
```
sudo kismet
```However there are no wireless networks around at the time to test it but the fact that no errors came up,sounds like its working.Or am i wrong? 
I tried 
```
source=ath5k,wlan0,Atheros
```which also started kismet without errors after
```
sudo kismet
```Sounds ok or should i find a wireless for testing?

(if my ifconfig and my lshw -C network are needed,will post it in my next post)

Either way,thanx a lot for your contribution:)

---

### Post by chili555 on 2009-12-28
Which do you have, an Intel wireless card or an Atheros? Obviously, you should use the *source=* to match.

---

### Post by thebigbradwolf on 2009-12-28
That was the charm. Thank you very much guys. One more example of the supportive linux community.

---

### Post by z3uSS on 2010-06-14
> **chili555 said:**
> The module *iwlagn* is not listed in the README for Kismet, however, there are reports that this may work:```
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl4965,wlan0,intel
```Please try it and let the searchers know.

worked like a charm !!! and on 10.04 lucid ... thx
iwlagn does not work :(

---

### Post by z3uSS on 2010-06-15
ok ... i was too happy ... now kismet stop working ... i managed to use it only once ... worked just fine ... after that i used the following comands :

sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode monitor
sudo ifconfig wlan0 up 

wifi was back online ... i connected succesfully to www ... all just peachy :)

but this morning .. when i tried to run kismet_server i got this error :

tbbt@VAIO-Ubuntu:~$ sudo kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (intel): Enabling monitor mode for iwl4965 source interface wlan0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument

can someone give me an ideea to what should i do next ? 
i don't have iwl4965 driver but iwlagn ... i modified kismet.conf with that so i could work ... but now ...

---

### Post by chili555 on 2010-06-15
> i don't have iwl4965 driver but iwlagn ... i modified kismet.conf with that so i could work ... but now ...Kismet does not recognize iwlagn, but it does know what iwl4965 is. If you have an Intel 4965 ABG card, then Kismet should work with iwl4965 in the sources= line. It may even work with other Intel cards driven by iwlagn. 

You shouldn't have to manually put your card in monitor mode before starting Kismet; however, in my experience, you will need to take the interface down and return it to Managed mode and then bring the interface back up *after* running Kismet.> $ sudo kismet_serverI don't understand why this is not simply:```
sudo kismet
```

Last, I am not quite sure what is set in your kismet.conf as far as channel is concerned. Why not let it scan all channels? Are you concentrating on just one wireless access point?

---

### Post by z3uSS on 2010-06-15
> **chili555 said:**
> Kismet does not recognize iwlagn, but it does know what iwl4965 is. If you have an Intel 4965 ABG card, then Kismet should work with iwl4965 in the sources= line. It may even work with other Intel cards driven by iwlagn. 

You shouldn't have to manually put your card in monitor mode before starting Kismet; however, in my experience, you will need to take the interface down and return it to Managed mode and then bring the interface back up *after* running Kismet.I don't understand why this is not simply:```
sudo kismet
```

Last, I am not quite sure what is set in your kismet.conf as far as channel is concerned. Why not let it scan all channels? Are you concentrating on just one wireless access point?

in kismet.conf i have iwl4965 so it should be ok ...
with monitor it was a typo mistake ( big one :) ) ... i ment Managed and i did that after exiting kismet ... the problem is that since then kismet gives me that error .. 

lol as i typed this i tried once more to run kismet and now it works ... i really don't get it ... i didn't change a thing .... i'll get back if it get's stuck again ....

---

### Post by fcigoi on 2010-07-31
Hi all,

I have followed this post to try and configure Kismet, and I managed to find the right parameters for my card, but when I try to run kismet here's what I get:


Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (intel): Enabling monitor mode for iwl3945 source interface wlan0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument
Done.


Any ideas why ? Help most appreciated

---

### Post by chili555 on 2010-07-31
> **fcigoi said:**
> Hi all,

I have followed this post to try and configure Kismet, and I managed to find the right parameters for my card, but when I try to run kismet here's what I get:


Launching kismet_server: //usr/bin/kismet_server
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Non-RFMon VAPs will be destroyed on multi-vap interfaces (ie, madwifi-ng)
Enabling channel hopping.
Enabling channel splitting.
NOTICE: Disabling channel hopping, no enabled sources are able to change channel.
Source 0 (intel): Enabling monitor mode for iwl3945 source interface wlan0 channel 6...
FATAL: channel get ioctl failed 22:Invalid argument
Done.


Any ideas why ? Help most appreciatedLet's have a look at:```
sudo lshw -C network
```Thanks.

---

### Post by fcigoi on 2010-08-01
There you go....


 *-network               
       description: Ethernet interface
       product: 88E8055 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 13
       serial: 00:13:a9:e2:ab:29
       size: 1GB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.1.14 latency=0 link=yes multicast=yes port=twisted pair speed=1GB/s
       resources: irq:29 memory:f6000000-f6003fff ioport:3000(size=256) memory:f0000000-f001ffff(prefetchable)
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 02
       serial: 00:1b:77:3c:30:f4
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:30 memory:fa000000-fa000fff

---

### Post by chili555 on 2010-08-01
That looks pretty normal. I wonder if Network Manager is not allowing the wireless to work when your wired ethernet is hooked up and has an IP address:```
description: Ethernet interface
product: 88E8055 PCI-E Gigabit Ethernet Controller
....
logical name: eth0
version: 13
....
 ip=192.168.1.14 
```Please detach the cable, wait a few moments for NM to notice the change of state and try again. Do you get the same or another error message?

---

### Post by fcigoi on 2010-08-01
Same error message I'm afraid.

---

### Post by chili555 on 2010-08-01
May I see the sources section of your kismet.conf? Thanks.> # CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=ipw3945,wlan0,Intel

---

### Post by fcigoi on 2010-08-02
Here it is...


# Sources are defined as:
# source=sourcetype,interface,name[,initialchannel]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
source=iwl3945,wlan0,intel


In the meantime I installed the updated version of kismet, and the GUI starts, but in the message queue there still is the same error on ioctl

---

### Post by vinte on 2010-11-08
I got the same problem with iwl3945 driver, ubuntu 10.10, kismet 2008.05.R1 
Somebody helps me, pls.

---

### Post by vinte on 2010-11-17
It worked.
Thank chili555

---

### Post by mrwave2002 on 2010-11-17
Hellow.
About Kismet i want to ask you. I have a Realtec 8191SE and i want to use it.

I give to terminal this:
root@tasos-HP-620:/home/tasos# ifconfig
eth0      Link encap:Ethernet  HWaddr d8:d3:85:2f:41:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

wlan0     Link encap:Ethernet  HWaddr 70:f1:a1:4e:69:b3  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:fe4e:69b3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2368 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1991 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2691302 (2.6 MB)  TX bytes:206703 (206.7 KB)
          Interrupt:17 Memory:f8958000-f8958100

Then i give:

sudo gedit /etc/kismet/kismet.conf

# Name of server (Purely for organizational purposes)
servername=Kismet

# User to setid to tasos
suiduser=tasos

# Do we try to put networkmanager to sleep?  If you use NM, this is probably
# what you want to do, so that it will leave the interfaces alone while
# Kismet is using them.  This requires DBus support!
networkmanagersleep=true

# Sources are defined as:
# [COLOR=DarkRed]source=rtl8191,wlan0,realtec[,13][/COLOR]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[COLOR=DarkRed]source=rtl8191,wlan0,realtec[/COLOR]

I don't know about the lines with red what do i put?

I give:

root@tasos-HP-620:/home/tasos# sudo lshw -C network
  *-network               
       description: Wireless interface
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 10
       serial: 70:f1:a1:4e:69:b3
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0018.1025.2010 firmware=63 ip=192.168.1.2 latency=0 link=yes multicast=yes wireless=802.11bg
       resources: irq:17 ioport:7000(size=256) memory:98800000-98803fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:85:00.0
       logical name: eth0
       version: 02
       serial: d8:d3:85:2f:41:24
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:45 ioport:2000(size=256) memory:90410000-90410fff memory:90400000-9040ffff memory:90420000-9043ffff

---

### Post by chili555 on 2010-11-17
> # Sources are defined as:
# [COLOR="Red"]source=rtl8191,wlan0,realtec[,13][/COLOR]
# Source types and required drivers are listed in the README under the
# CAPTURE SOURCES section.
# The initial channel is optional, if hopping is not enabled it can be used
# to set the channel the interface listens on.
# YOU MUST CHANGE THIS TO BE THE SOURCE YOU WANT TO USE
[COLOR="Red"]source=rtl8191,wlan0,realtec[/COLOR]

I don't know about the lines with red what do i put?
The first line in red is commented out with #. It doesn't matter what you put there; it will be ignored.

In the second section, it wants your actual, real wireless driver; I do not have a driver called rtl8191 on my system. You can find out the driver that is actually being used with:```
lsmod | grep 819
```Did you try it as written? What, if any errors were given?

According to this:```
less /usr/share/doc/kismet/README.gz
```The Realte[COLOR="Red"]k[/COLOR] drivers in the r819xx series are not supported, but I'd try anyway.

---

### Post by mrwave2002 on 2010-11-17
Hello, that i get from terminal:

tasos@tasos-HP-620:~$ lsmod | grep 819
r8192se_pci           470073  0 
cfg80211              144470  1 r8192se_pci

---

### Post by Hardtech on 2010-11-17
Hi I am trying to set up kismet with my ae1000 but I cant figure out how/where exactly to modify the kismet.conf, and I am not sure what to do with the network output when I sudo lshw -C network. but here it is...


 *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 68:7f:74:72:30:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.2 ip=192.168.1.118 multicast=yes wireless=Ralink STA

i installed the ralink 3572 driver

---

### Post by mrwave2002 on 2010-11-18
Hello what step we doing next?

---

### Post by chili555 on 2010-11-18
> **mrwave2002 said:**
> Hello, that i get from terminal:

tasos@tasos-HP-620:~$ lsmod | grep 819
r8192se_pci           470073  0 
cfg80211              144470  1 r8192se_pciAnd so did you change your kismet.conf? And did it work? Did it throw an error?

---

### Post by chili555 on 2010-11-18
> **Hardtech said:**
> Hi I am trying to set up kismet with my ae1000 but I cant figure out how/where exactly to modify the kismet.conf, and I am not sure what to do with the network output when I sudo lshw -C network. but here it is...


 *-network
       description: Wireless interface
       physical id: 1
       logical name: ra0
       serial: 68:7f:74:72:30:b4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN driverversion=2.4.0.2 ip=192.168.1.118 multicast=yes wireless=Ralink STA

i installed the ralink 3572 driverThe file is /etc/kismet/kismet.conf. Did you read the REAME, especially Section 12?```
less /usr/share/doc/kismet/README.gz
```

---

### Post by mrwave2002 on 2010-11-20
Chilli555 Hello again. I try something else now.
can i ask you a question? How can i see properties in other connections i see to Ubuntu 10.10 connection manager?
I want the channels each one of the and encryption type like wep or wpa.
To see what has specific each one of them.

---

### Post by chili555 on 2010-11-20
> **mrwave2002 said:**
> Chilli555 Hello again. I try something else now.
can i ask you a question? How can i see properties in other connections i see to Ubuntu 10.10 connection manager?
I want the channels each one of the and encryption type like wep or wpa.
To see what has specific each one of them.With Kismet running, press 's' to sort the networks. I then press 'f' for 'first seen.' Then highlight a network and press 'Enter' to see details. Press 'x' to go back to the network list.

---

### Post by Hardtech on 2010-11-23
Thanks chili yea i read it now im trying to get the 2780 to work with some difficulties :(

---

### Post by mrwave2002 on 2010-11-23
> **chili555 said:**
> With Kismet running, press 's' to sort the networks. I then press 'f' for 'first seen.' Then highlight a network and press 'Enter' to see details. Press 'x' to go back to the network list.
Hi again!
I've mannaged to get it work!
I found an Alpha usb card with rtl8187L Chipset and i changed this:

source=rt8180,wlan0,rt8180
enablesources=rt8180

So Kismet is oppening now!

But i have another problem. I want to change Txpower to reduce transmiter Power.
Can i do it from Ubuntu 10.10?

Or maybe is because my card is Usb and these commands are only for Onboard Cards?

Is there a utility to do it from Ubuntu 10.04 or 10.10?

---

### Post by chili555 on 2010-11-23
Doesn't the usual command work?```
sudo iwconfig wlan0 txpower 15
```Using whatever number you need, of course.

---

### Post by mrwave2002 on 2010-11-23
> **chili555 said:**
> Doesn't the usual command work?```
sudo iwconfig wlan0 txpower 15
```Using whatever number you need, of course.

Hi the link of my card is this for information:

 [http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036H&Category=105463](http://www.alfa.com.tw/in/front/bin/ptdetail.phtml?Part=AWUS036H&Category=105463)

About the TxPower here i give to terminal:

root@tasos-HP-620:/home/tasos# iwconfig wlan2 txpower 30mW
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan2 ; Operation not permitted.
root@tasos-HP-620:/home/tasos# sudo iwconfig wlan2 rate auto
root@tasos-HP-620:/home/tasos# sudo iwconfig wlan2 txpower 20
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan2 ; Operation not permitted.

root@tasos-HP-620:/home/tasos# iwlist wlan2 txpower
wlan2     unknown transmit-power information.

According to this i can only manage TxPower only by a Utility:

 FAQ - some common questions about Alfa AWUS036NH
2000mW USB adapter w/ 5 dBi antenna kit:

Can I manually adjust the output power?

Output power is controlled internally by the adapter. It is not user adjustable.
Though you may find a utility that lets you tinker with that, it is not recommended.

I am using a 5 metre usb cable but i 'll go to buy an 8 metre cable,
to avoid the transmited power of microwaves near to me.

Thanks for the help!

---

### Post by chili555 on 2010-11-23
> root@tasos-HP-620:/home/tasos# sudo iwconfig wlan2 txpower 20
Error for wireless request "Set Tx Power" (8B26) :
SET failed on device wlan2 ; Operation not permitted.This is the correct form of the command, but I think the power number is higher than the wireless card will accept. Please try:```
sudo iwconfig wlan2 txpower 15
```Then try 16, 17, etc. until it errors out. If 15 errors, try 10 or 12.

---

### Post by mrwave2002 on 2010-11-24
> **chili555 said:**
> This is the correct form of the command, but I think the power number is higher than the wireless card will accept. Please try:```
sudo iwconfig wlan2 txpower 15
```Then try 16, 17, etc. until it errors out. If 15 errors, try 10 or 12.
Hello, i 'll try that you said.
I found a utility in Ubuntu 10.10 In Centre of Software, which called RutilT Wlan Manager.
In the Tab Options the reading Maximum Tx Rate will do the job?
When it says 54Mbps and i lower the value is it correct?
Or this is just for the rate connection speed?
E.g. the default setting is 54Mbps and i lower it to 12Mbps?

---

### Post by chili555 on 2010-11-24
I am not familiar with RutilT Wlan Manager. 54Mb/s describes the connection speed between the wireless access point and your wireless card. Generally, it is correctly negotiated between the access point and your card without any input on your part. They figure out the highest speed that data can reliably be transferred. It is influenced not only by the distance between the access point and the wireless card in the laptop, but also radio frequency interference (RFI) in the area, such as microwave ovens, wireless telephones, etc. Some RFI can be avoided by setting the wireless access point to a different channel. By default, most consumer routers are set to channel 6; mine is set to channel 11.

txpower is an entirely different subject, although it influences speed. You really only enough txpower to reach the access point reliably. More power creates heat and, if running on battery power, runs down the battery faster.

There is another factor called Power Management. Wireless cards respond to power management schemes that are supposed to determine when the card hasn't been used in a few moments and turn the power down and then, when wireless is needed again, turn it back up.

All of this is not needed at all in Kismet. The wireless card is not speaking to the wireless access point; it is only listening.

You can see all these settings in *iwconfig*; for example:> wlan0     IEEE 802.11abg  ESSID:"my_router"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 88:24:66:2A:D7:99   
          [COLOR="Red"]Bit Rate=54 Mb/s[/COLOR]   [COLOR="Red"]Tx-Power=14 dBm [/COLOR]  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          [COLOR="Red"]Power Management:off[/COLOR]
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mrwave2002 on 2010-11-24
> **chili555 said:**
> I am not familiar with RutilT Wlan Manager. 54Mb/s describes the connection speed between the wireless access point and your wireless card. Generally, it is correctly negotiated between the access point and your card without any input on your part. They figure out the highest speed that data can reliably be transferred. It is influenced not only by the distance between the access point and the wireless card in the laptop, but also radio frequency interference (RFI) in the area, such as microwave ovens, wireless telephones, etc. Some RFI can be avoided by setting the wireless access point to a different channel. By default, most consumer routers are set to channel 6; mine is set to channel 11.

txpower is an entirely different subject, although it influences speed. You really only enough txpower to reach the access point reliably. More power creates heat and, if running on battery power, runs down the battery faster.

There is another factor called Power Management. Wireless cards respond to power management schemes that are supposed to determine when the card hasn't been used in a few moments and turn the power down and then, when wireless is needed again, turn it back up.

All of this is not needed at all in Kismet. The wireless card is not speaking to the wireless access point; it is only listening.

You can see all these settings in *iwconfig*; for example:

Thanks for the information!

The resaults of the terminal are these:

root@tasos-HP-620:/home/tasos# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

[COLOR=DarkRed]Power Management period:0us[/COLOR]  mode:All packets received
          Link Quality=76/100  Signal level=-64 dBm  Noise level=-108 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

But the command still does not doing any effect:
root@tasos-HP-620:/home/tasos# iwconfig wlan0 txpower 10
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device wlan0 ; Operation not supported.

Should i try any Tx Power Adjustment Utility? Do you suggest any Utility? For 10.10?
I putted back again my onboard Wlan Rtl8191Se.
The configuration is the same as before.

Any Thoughts?

---

### Post by chili555 on 2010-11-24
> Any thoughts?First, don't post your encryption key! Please edit your post and remove it at once. Second, maybe your card doesn't support manipulating txpower. Find out with:```
sudo iwpriv wlan0
```

---

### Post by mrwave2002 on 2010-11-24
> **chili555 said:**
> First, don't post your encryption key! Please edit your post and remove it at once. Second, maybe your card doesn't support manipulating txpower. Find out with:```
sudo iwpriv wlan0
```

I'm sorry i corrected that!

Terminal;

root@tasos-HP-620:/home/tasos# sudo iwpriv wlan0
wlan0     Available private ioctls :
          set_debugflag    (8BE0) : set   1 int   & get   0      
          activescan       (8BE1) : set   1 int   & get   0      
          rawtx            (8BE2) : set   1 int   & get   0      
          forcereset       (8BE3) : set   1 int   & get   0      
          force_mic_error  (8BE4) : set   1 int   & get   0      
          firm_ver         (8BE5) : set   0       & get   1 int  
          set_power        (8BE6) : set   1 int   & get   0      
          radio            (8BE9) : set   1 int   & get   0      
          lps_interv       (8BEA) : set   1 int   & get   0      
          lps_force        (8BEB) : set   1 int   & get   0      
          adhoc_peer_list  (8BEC) : set   0       & get 2047 char 
          setpromisc       (8BF6) : set   3 int   & get   0      
          getpromisc       (8BF7) : set   0       & get  45 char

---

### Post by chili555 on 2010-11-24
I suggest:```
sudo iwpriv wlan0 set_power
```Try it without any qualifiers and see what comes back. Try it with 5 or 10 or whatever. Monitor with:```
sudo iwconfig wlan0
```Note any change and try again. I don't have your device so I can't tell you what the exact setting is, I think you'll have to play around with it a bit until you understand what command does what you wish. If you accidently turn it all the way off, and can't get it back, you can always reboot.

---

### Post by H@RD5 on 2011-09-11
Hello all first post, I need help when I attempt to edit the kismet.conf file I get the following errors.

```
(gedit:10624): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.1PFJ1V': No such file or directory

(gedit:10624): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

```I used
```
sudo gedit etc/kismet/kismet.conf
```but still I get this error, I am soo confuzeled any help is much appreciated!

I am running Ubuntu 11.04 installed inside windows, and Kismet 2008.05.R1

---

### Post by Dr_Lion on 2011-10-14
That is not the right path for the file, i dont remember the right one now.

---

### Post by CharlesA on 2011-10-14
Closed for necro.

---

