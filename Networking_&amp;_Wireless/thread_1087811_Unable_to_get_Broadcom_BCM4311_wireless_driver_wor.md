---
title: "Unable to get Broadcom BCM4311 wireless driver working"
date: 2009-03-05
forum: Networking &amp; Wireless
---

### Post by zlgo on 2009-03-05
Hey guys

To start with i'll list my hardware and device specific info.

Machine Brand and Model (PC/Laptop):
```
HP Pavilion dv6000
```

Wireless Brand, Model and Wireless Chipset:
```

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)

```

The ifconfig for eth1 (my wireless card)
```
eth1      Link encap:Ethernet  HWaddr 00:1a:73:24:a0:97  
          inet6 addr: fe80::21a:73ff:fe24:a097/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:25
          TX packets:0 errors:6 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

```
Note: I installed ("Activated") the Broadcom STA wireless propietary driver and consequently it renamed my wireless to eth1. No problem here just thought id point it out.


```
$ iwconfig eth1
eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated 
```


```
$ sudo lshw -C network
  *-network               
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:24:a0:97
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11bg

```

```
$ iwlist scan
eth1      Interface doesn't support scanning.

```

```
$ uname -mr
2.6.27-7-generic i686

```

```
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                    Ignoring unknown interface eth0=eth0.

```
eth0 is my ethernet connection and that was all that returned (im not sure but my guess would be that it should attempt to restart eth1 aswell?)

Fresh install of Ubuntu 8.10 (Intrepid Ibex) (Dual boot with Windows Vista :()



I've been with linux for at least 2 years or so now but this has really bugged me. I'm not an expert or anything, but whatever problems i run into on linux i usually solve myself.

On this install i didnt use ndiswrapper or any other drivers in case they interfered with the "wl" driver. On my previous install (same version) of ubuntu i tried ndiswrapper first with bcmwl6.inf (from my windows folder on the other partition) and then a bcmwl5.inf from other people/HP website. I understand that the 5/6 represent a firmware number for the wireless card and that ndiswrapper isnt particularly compatible with version 6. I tried alot of tutorials from the Ubuntu forums and never once have i seen/connected to a wireless network while using linux on my laptop.

What confuses me is that i've seen threads where people with the same wireless card as me (BCM4311) have had it working but were on Ubuntu 8.04... does anyone think its worth burning another cd of ubuntu 8.04 and replacing my current Ubuntu with that to see if it works?? (Im not entirely sure about this because i think these people had Dell laptops and Compaq laptops so maybe i have a modified version of BCM4311 or they do?)

I also noticed that broadcom released a driver for linux BCM4311 drivers here
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
which is "for use with Broadcom's BCM4311-, BCM4312-, BCM4321-, and BCM4322-based hardware." meaning it should definitely work with my card... am i right in believing that this IS the propietary driver that ubuntu is on about? If not then could someone give me some commands on how to install it? There dont seem to be any instructions on broadcoms website and im quite used to the terminal.

EDIT: I tried broadcoms official linux drivers, i didnt realize the readme was a separate file :P and yeah.. got no errors removed all other modules/drivers but that didnt work any better than anything else i had tried :S



To sum up:
My BCM4311 wireless is detected on my system but when i left click on network manager in Gnome there are no wireless networks found. If i use the switch to enable/disable my wireless the light next to it changes the same as it would in windows but there is no difference on network manager. Its almost as if the driver works to the extent of detecting and identifying the wireless card, but not using it.

What am i doing wrong? Am i missing something? Will changing my linux installation to Ubuntu 8.04 help?

If anyone can help or point me in the right direction that would be great.

Thanks alot
Zlgo

---

### Post by zlgo on 2009-03-06
Update:

I have installed ubuntu 8.04.1 instead of 8.10 now and i think iv gotten 1 step closer to sorting it out but not sure if il be able to solve it fully

On 8.10 i couldnt install/use the bcm43-fwcutter tool (labeled "Broadcom B43 Wireless Driver") but on 8.04.1 it was in the propietary drivers list (System>Administration>Hardware Drivers) and, being a new solution i tried it and it instantly detected my 2 wireless networks but sadly it wouldnt connect

If anyone else has any speculation on this id be happy to hear it.. so far the best solution iv seen is to buy a chunky usb wireless card and they are rumored not to play well with linux either


Edit:
By the way here is my dmesg from when i attempted to connect to my wireless if anyone understands it (i wasnt using any wep key because my router doesnt use authentication)
```
[  527.920917] wlan0: Initial auth_alg=0
[  527.920926] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  527.920942] wlan0: Initial auth_alg=0
[  527.920946] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  528.022610] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  528.124597] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  528.226576] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  530.823282] wlan0: Initial auth_alg=0
[  530.823293] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  530.922755] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  531.022740] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  531.122724] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  533.777941] wlan0: Initial auth_alg=0
[  533.777950] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  533.778209] wlan0: Initial auth_alg=0
[  533.778214] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  533.879762] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  533.981748] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  534.081745] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  536.723509] wlan0: Initial auth_alg=0
[  536.723518] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  536.723928] wlan0: Initial auth_alg=0
[  536.723933] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  536.823348] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  536.925332] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  537.027396] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  545.555301] wlan0: Initial auth_alg=0
[  545.555312] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  545.654637] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  545.754623] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  545.854605] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  549.539696] wlan0: Initial auth_alg=0
[  549.539705] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  549.539973] wlan0: Initial auth_alg=0
[  549.539977] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  549.640951] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  549.742940] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  549.844921] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  555.426292] wlan0: Initial auth_alg=0
[  555.426301] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  555.426567] wlan0: Initial auth_alg=0
[  555.426572] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  555.528114] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  555.628097] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  555.730083] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out
[  558.379850] wlan0: Initial auth_alg=0
[  558.379859] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  558.380298] wlan0: Initial auth_alg=0
[  558.380304] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  558.481687] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  558.583671] wlan0: authenticate with AP 00:1f:9f:72:f1:ef
[  558.683667] wlan0: authentication with AP 00:1f:9f:72:f1:ef timed out

```

---

