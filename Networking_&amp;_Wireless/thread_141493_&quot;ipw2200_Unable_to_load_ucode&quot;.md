---
title: "&quot;ipw2200: Unable to load ucode&quot; ???"
date: 2006-03-08
forum: Networking &amp; Wireless
---

### Post by Commuto on 2006-03-08
I've a totally fresh, 2 days old install of Ubuntu 5.10
Now I'm trying to set up the Wireless Network and step upon a hurdle. The firmware of my Intel 2200 BG won't load :-k 
```
me@Host:/var/log$ dmesg | grep ipw2200
[4297637.249000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.0.6
[4297637.250000] ipw2200: Copyright(c) 2003-2004 Intel Corporation
[4297637.253000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[b][4297637.488000] ipw2200: Unable to load ucode
[4297637.488000] ipw2200: Unable to load firmware: 0xFFFFFFEA[/b]
[4297637.488000] ipw2200: failed to register network device
[4297637.493000] ipw2200: probe of 0000:02:0a.0 failed with error -5
me@Host:/var/log$

```

I don't know where to dig further... and Google is of any help :???: 

Maybe I am confronted with a dev problem and should address the dev team ?
Don't know what to do :oops:

---

### Post by mdmarmer on 2006-03-08
This will occur if ndiswrapper is loaded before ipw2200

Is the simplest way to fix to add ndiswrapper to /etc/blacklist?

Or maybe just sudo apt-get remove ndiswrapper --purge  ?


Mike

---

### Post by Commuto on 2006-03-08
Indeed i found some similar input describing a 'conflict' with ndiswrapper.
Therefore I tried to "disable" it in a hard way : I removed (actually, changed the name of) the file /lib/modules/2.6.12-10-686/kernel/drivers/net/ndiswrapper/ndiswrapper.ko , and rebooted.

I guess this prevent the system to load the module... (?)
Unfortunately it didn't change the behaviour :oops: .

I have no /etc/blacklist file... as it is a fresh install I guess I'd have to create it. Moreover correct me if I'm wrong but I doubt it would have any impact considering my previous attempt.

Also I tried to sudo apt-get remove ndiswrapper --purge but apparently there is no such package on my system (and not even in Synaptic :confused:). Weird :-k

---

### Post by dbunder on 2006-03-14
I read somewhere in that monster wpa+2200 howto thread that there're two (or more) versions of the Intel PRO/Wireless 2200 card, some work in linux, some don't.  Your dmesg looks exactly like mine (minus the errors) as far as driver, card, etc.  Assuming this is a Dell laptop?  If so, what model?  May help narrow things down.  Are you sure you copied *all* the firmware files to the proper location as described in the howto thread?  Most recent ipw and ieee drivers?  I know these're all questions covered in the howto, but it doesn't help to double check.  When I first started configuring my WPA+2200 I accidentally downloaded an earlier version of the iwp drivers and it made everything bomb.

Also, in synaptic, I'm finding ndiswrapper-utils.  If you're seeing conflicts with that, may want to uninstall it.  Mine's not installed by default, so unless you installed it somehow, yours should be as well.

---

### Post by Commuto on 2006-03-14
Thank you for your several ideas dbunder :o.
This laptop never hold a linux. It is a Toshiba 5105-S501, sold withOUT WiFi. I bought the Intel PRO/Wireless 2200 separately.
Did you hear about any physical difference between the "good for linux" and "not good for linux" card...:confused:.

Regarding the installation of the ipw2200 :
Well i did *nothing* at the moment :mrgreen:. I mean, I installed Ubuntu 5.10 one week ago. As far as I know support for ipw2200 is provided. The firmware files appear to be well at their location:
```
me@myhost:/lib/hotplug/firmware$ ls *2.3*
ipw-2.3-boot.fw-2.6.12-10-686       ipw-2.3-ibss.fw-2.6.12-9-686
ipw-2.3-boot.fw-2.6.12-9-686        ipw-2.3-ibss_ucode.fw-2.6.12-10-686
ipw-2.3-bss.fw-2.6.12-10-686        ipw-2.3-ibss_ucode.fw-2.6.12-9-686
ipw-2.3-bss.fw-2.6.12-9-686         ipw-2.3-sniffer.fw-2.6.12-10-686
ipw-2.3-bss_ucode.fw-2.6.12-10-686  ipw-2.3-sniffer.fw-2.6.12-9-686
ipw-2.3-bss_ucode.fw-2.6.12-9-686   ipw-2.3-sniffer_ucode.fw-2.6.12-10-686
ipw-2.3-ibss.fw-2.6.12-10-686       ipw-2.3-sniffer_ucode.fw-2.6.12-9-686
me@myhost:/lib/hotplug/firmware$
```
I did not follow any howto to install the sourceforge driver cuz I wanted to keep in pace with Ubuntu, rather than diverging from the main tree. This is the precise reason I gave a chance to Ubuntu, or I'd better stick to my  ~almost faithfull Debian :neutral:.

So if you invite me to install the driver thanks to the traditionnal method, compiling and the like, I'll eventually give it a try. I'm at the point I desesperately need WiFi. But I sadly consider it as a point against Ubuntu :(.

(I double-checked ndiswrapper-utils in Synaptic and it is not currently installed (it never was, indeed)).

---

