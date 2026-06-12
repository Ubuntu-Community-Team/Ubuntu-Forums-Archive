---
title: "BCM 4318 with Jaunty"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by nicholas28 on 2009-05-21
Hello! Brand new to Linux (!) and still finding my way around. I am using Ubuntu Jaunty. I'd like to get the Wireless card working. (It's a BCM4318.) I have been through several how-to's and tutorials already to get ndiswrapper and the Windows XP drivers installed, but the Network Manager does not show any available Wireless Networks (only the ethernet, which works). Also, no drivers show up in System --> Admin --> Hardware Drivers.

I have been through many many posts about this -- was trying not to create another thread about it when there seems to be so many -- but I can't figure this out.  Any ideas? Please let me know if I can post anything to help you help me. Thanks for anyone taking interest. 

Below is the output for lshw -C network.

Ken



kenneth@Inspiron530:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82562V-2 10/100 Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 02
       serial: 00:24:e8:17:23:37
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=0.3.3.3-k6 firmware=1.1-2 ip=192.168.2.9 latency=0 module=e1000e multicast=yes
  *-network
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: wlan0
       version: 02
       serial: 00:24:8c:78:8b:0a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.53+ASUS,02/11/2005, 3.100.64.0 latency=64 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 4e:f5:a9:0c:4c:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by rudy.b on 2009-05-21
Try to scan for networks with the following command to see if you get any results:

```
sudo iwlist wlan0 scan
```

---

### Post by nolster12 on 2009-08-17
Not sure if it is the same with you but Jaunty is the first distro to see my wireless on off switch.  It defaults to off on the install.  I have to turn it on before it works.

---

### Post by Jazzkatt on 2009-08-20
I'm new to this also and the same problem. 

   First thing I did was plug hard wired into my network and got all available updates.Through System>Administration>Update Manager.

   Second Clicked System>Administration>Hardware Drivers . It found the card I highlighted it a clicked "Activate" It activated it. Still nothing .Reboot still nothing. 
So I thought when Ubuntu was installed the driver was not active so just maybe the network manager could not see it. 

   Third I clicked Applications > Add / Remove . It said the list was out of date so I clicked refresh . after the refresh I clicked Internet, and in the applications box checked KNetworkManager . In the process of installing KNetMgr it updated all installed programs. While the install was still in process of installing I saw my wireless Switch/Light ,light up . 

After Install was complete I unplugged the cat5 clicked network manager in the title bar there was my router . Selected it put in the key and here I am .

This was on a Compaq Presario 5305wm laptop completely stock.
Semperon 3400+ 80 gig HD 1 gig ram
Broadcom BCM 4318e
Duel booting Ubuntu 9.04 Win7
Ubuntu install and updated 8.20.2009 12.00 pm cst.

Hope this helps 
Jazz

---

### Post by clb62 on 2009-08-22
(k)Ubuntu newbie here,

Dell D610 Bcom4318 (1370), I was having a heck of a time with (k)Jaunty and my wireless.  Tried fwcutter, then ndiswrapper (after much reading over the forums), using 2 different .inf/.sys files from Dell and the Ndis website.  I re-installed Jaunty and this time I donwloaded and used the Windows Device Driver Install (gtk-app) with both .inf/.sys files again.  No luck, then I stumbled on this thread and thought I'll give the fwcutter one more chance.   A 3rd install of Jaunty (and not sure what changed), just made sure I followed Jazzkat's steps below, plus added a system restart after each one, and Ta-Da (well not the Redmond ta-da) I'm sending this note via wireless.  :P

1. Cat5 wired and did all available updates, (restart)
2. System>Administration>Hardware Drivers, clicked "Activate", (restart)
3. Applications > Add / Remove and Refresh(ed), add KNetworkManager, Wireless Light is ON, (restart) 
  4. Clicked Network Mgr from Panel, made sure wireless enabled, found my SSID (WPA-PSK), and logged in

Have a had a couple issues with coming and going, not sure if the WiFi light (wireless enable check box) being on reflects the state of the Fn-F2 state.  Toggling the switch does change the status of the WiFi light.  But for the last 4 days it's been rock solid.

Just thought I'd post another success story with 4318... I'll make sure any other "used" laptops I get are Centrino/Intel Pro in the future !! :idea:

So, thanks everyone.

---

### Post by tired of MS on 2010-02-01
[QUOTE=Jazzkatt;7819050]I'm new to this also and the same problem. 

   First thing I did was plug hard wired into my network and got all available updates.Through System>Administration>Update Manager.

   Second Clicked System>Administration>Hardware Drivers . It found the card I highlighted it a clicked "Activate" It activated it. Still nothing .Reboot still nothing. 
So I thought when Ubuntu was installed the driver was not active so just maybe the network manager could not see it. 

   Third I clicked Applications > Add / Remove . It said the list was out of date so I clicked refresh . after the refresh I clicked Internet, and in the applications box checked KNetworkManager . In the process of installing KNetMgr it updated all installed programs. While the install was still in process of installing I saw my wireless Switch/Light ,light up . 

After Install was complete I unplugged the cat5 clicked network manager in the title bar there was my router . Selected it put in the key and here I am .

Thanks Jazzkatt, finally a simple answer THAT WORKS!!!!  :KS
One other reminder-restart Ubuntu... prior to restart it seemed that everything was fine, but no sites (no connection). Restart-ALL FINE!

---

