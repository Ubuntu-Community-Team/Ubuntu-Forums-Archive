---
title: "eeepc - ethernet not working"
date: 2010-06-15
forum: Networking &amp; Wireless
---

### Post by Daniel_rz on 2010-06-15
Hi,
I purchased an EeePc 900HD (ASUS).
installed EeeBuntu_3.0
when i run "lshw -c network"
i got a "DISABLE" status for my ethernet connection.

in this forum i read that i need to run
"ifconfig *logical_hardware_name* up"

the "DISABLE" status is gone but still no ethernet connection
in the Gnome-NetworkManager.

any suggestions?

---

### Post by Iowan on 2010-06-15
Check **ifconfig -a** to see if the interface has an IP address. **ifconfig** might start the interface - but NM doesn't know it...

---

### Post by Daniel_rz on 2010-06-15
nope, no ip address
(no inet6 addr like in the wireless one)
and no bus-info from the "lshw" too.

sorry for not coping, my office have only a wired network.

---

### Post by varunendra on 2010-06-15
> **Daniel_rz said:**
> nope, no ip address
(no inet6 addr like in the wireless one)
and no bus-info from the "lshw" too.

sorry for not coping, my office have only a wired network.

See if[ this]("http://ubuntuforums.org/showthread.php?t=1503875") helps. (The problem in the thread is a bit different, but the suggestions in it may help you)

Your network must have a DHCP server. Else you may need to configure the IP settings (IPv4) manually.

---

### Post by Daniel_rz on 2010-06-15
10X but still no result..
made the changes in the interfaces file so the NM will know the ethernet exists.
made the NM manage ifupdown true. (that makes some kind of error when shutting down)

about that last statement i do have a DHCP server.

and i would like to know if i did right on the interfaces file

```

auto lo
iface lo inet loopback

auto pan0
iface pan0 inet loopback

auto wlan0
iface wlan0 inet loopback

```

---

### Post by varunendra on 2010-06-16
> **Daniel_rz said:**
> i do have a DHCP server.

and i would like to know if i did right on the interfaces file

```

auto lo
iface lo inet loopback

auto pan0
iface pan0 inet loopback

auto wlan0
iface wlan0 inet loopback

```
To be honest, I really don't know much about CLI yet. I mostly depend upon GUI for solutions. Here's what I do in such situations:

[LIST=1]
[*]**I read the IP configurations on a working PC. (Most often, using either Ubuntu Live or Slax Live CD makes the current PC network working)**
[*]**Even though DHCP is available, I feed the same configuration data manually through Network Manager (changing only IP address with a free one).**
[*]**So far it always has worked for me. So once it's working, I try to turn it again on auto settings (seeking address from DHCP).**
[*]**Not always, but most often it works. If not, I turn back to manual configuration.**
[/LIST]
If you want CLI options (more capable of-course) you may PM to Dinesh in the thread I gave link of.

I'd be watching this thread.

---

### Post by Daniel_rz on 2010-06-16
> **varunendra said:**
> 
[*]**Even though DHCP is available, I feed the same configuration data manually through Network Manager (changing only IP address with a free one).**


I tried it earlier.. the problem is that the NM dont recognize the ethernet connection. even when I insert it "Hard Coded".

---

### Post by varunendra on 2010-06-16
Have you tried any live CD (Ubuntu or Slax)?
I've found Slax a bit more capable in detecting networks unless there is a hardware problem.
My experience with Slax is now 4-5 months old though.

EDIT: I mean when I last used SLAX. But it never failed me.

---

### Post by Daniel_rz on 2010-06-16
**Again: the problem is that the NM does not recognize the ethernet connection**

If the NM would recognize it, I should be seeing "Wired connection-- No connections"
But even that is missing!

sorry for all the trouble ..

---

### Post by Iowan on 2010-06-16
What are results of (from a terminal) **sudo dhclient eth0**...
Hmmm... brings up a question - is your ethernet connection defined as eth0, or are you trying to get wireless (wlan0) working?

---

### Post by Daniel_rz on 2010-06-17
wireless is working.
ethernet dosent and defined as "pan0" and no as "eth0".

```


 description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5e:af:8d:8b:8d:07
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

how can i get the NM to work with the ethernet connection?

---

### Post by Iowan on 2010-06-18
Could you post results of **sudo lshw -C network**? *Ordinarily*, pan0 is "personal area network" (bluetooth).

---

### Post by Daniel_rz on 2010-06-19
```

*-network               
       description: Wireless interface
       product: RTL8187SE Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 22
       serial: 00:24:23:0b:58:35
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 ip=192.168.2.114 latency=0 module=rtl8187se multicast=yes wireless=802.11b/g linked
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 5a:1b:bc:c9:1d:ce
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes


```

that's after commanding "ifconfig pan0 up". (before it was DISABLED)

but there is no BT interface on my computer's hardware.
and it says "Ethernet interface"..

again, 10X!

---

### Post by Daniel_rz on 2010-06-27
any help?? pls...

---

### Post by varunendra on 2010-06-27
Does your **/etc/network/interfaces** file still looks like how it was in post [#5]("http://ubuntuforums.org/showpost.php?p=9465918&postcount=5") of this thread?
If yes, edit it to comment out each line except the first two. So that it looks like:
```
auto lo
iface lo inet loopback

#auto pan0
#iface pan0 inet loopback

#auto wlan0
#iface wlan0 inet loopback
```

Reboot. Then, try what is suggested [here]("http://forum.eeeuser.com/viewtopic.php?id=15665").

If it doesn't help, post here the outputs of```
ifconfig -a
``````
cat /etc/NetworkManager/nm-system-settings.conf
```(mind the case of letters in the command), and,```
cat /etc/network/interfaces
```

---

### Post by zugvogel on 2010-06-27
I'm having the same problem, albeit with "ubuntu netbook" - it's basically the same system though. I tried the battery trick but it didn't work.

This is the output from my networking files:

```

james@turkey:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:23:54:79:83:ce  
          inet6 addr: fe80::223:54ff:fe79:83ce/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:3204 (3.2 KB)
          Interrupt:28 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:43:56:0e:b1  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

james@turkey:~$ cat /etc/NetworkManager/nm-system-settings.conf 
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

james@turkey:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback



```

Your help is very much appreciated!
Thanks!

---

### Post by Daniel_rz on 2010-06-27
no luck with the battery trick..

here are the outputs you asked for:
```

daniel@DanielsNetbook:~$ sudo ifconfig -a
[sudo] password for daniel: 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

pan0      Link encap:Ethernet  HWaddr 1e:d2:75:14:78:35  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:23:0b:58:35  
          inet addr:192.168.1.133  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:23ff:fe0b:5835/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1433 errors:0 dropped:1402 overruns:0 frame:0
          TX packets:1415 errors:27 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1284438 (1.2 MB)  TX bytes:139103 (139.1 KB)
          Interrupt:18 Memory:f81d8000-f81d8100 

daniel@DanielsNetbook:~$ cat /etc/NetworkManager/nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

daniel@DanielsNetbook:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


```

---

### Post by varunendra on 2010-06-27
@zugvogel,
Have you tried manually assigning a valid IP to eth0?```
sudo ifconfig eth0 xxx.xxx.xxx.xxx
(where xxx would be replaced by a valid IP on your network, for example: 192.168.1.10)
```
What is the output of ```
sudo dhclient eth0
```



@Daniel,
I'm absolutely out of wits for your problem. eth0 not showing at all & pan0 being displayed as 'ethernet' is really confusing. Besides, I'm not familiar with Eeepc (I only recently realized it does not has an optical drive).

As a crosscheck measurement, I can only suggest a few things right now:

[LIST=1]
[*]If it is actually your ethernet that is displayed as pan0, it is currently not **'UP'**. Try```
sudo ifconfig pan0 up
```
[*]check your BIOS if it has ethernet enabled.
[*]check if the BIOS has any option to manually or automatically switch between ethernet & wifi. If it does, try disabling wifi from there & see if eth0comes up.
[*]If BIOS does not have any such switching option, try```
sudo ifconfig wlan0 down
```
[/LIST]

Besides these, I'd suggest you both to-

[LIST]
[*]Try creating & booting off Live USB thumb drive (system>administration>startup disk creator) & see if there is any positive difference. If there is, post the output of same commands in that mode.
[*]If you have a separate desktop pc with cd drive available, boot it with latest Slax LiveCD in Live PXE Server mode. Then, connecting it to your netbook over LAN, try booting the netbook from network. (If it is connected correctly, BIOS has the option to boot from network, & ethernet interface does not have 'physical' or BIOS issues, it should boot immediately into Slax). If it boots into Slax successfully, run the same commands & post the outputs.
[/LIST]

---

### Post by zugvogel on 2010-06-30
varunendra, thanks for your suggestion.

The IP address is DHCP assigned (something like 211.168.250.45) and so setting it manually probably won't work. The ethernet does work on my macbook, but when I unplug the cable from my macbook and plug it into my eee pc, I get the problem.

The output of "sudo dhclient eth0" is as follows:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For infor, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:23:54:79:83:ce
Sending on   LPF/eth0/00:23:54:79:83:ce
Sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
james@turkey:~$
```

So I suppose it's not picking up an address via DHCP. Any idea why this might be?

Thanks again for your help. I hope we can get this working.

---

### Post by varunendra on 2010-06-30
I'm not sure, but it seems to me that you probably don't have a dhcp server enabled on your network.
When your Macbook is connected successfully, see its IP configuration (IP address, Gateway, DNS addresses). Try manually setting the same configuration on your EeePC (except changing the last digit of the IP address.) For this you can use either Network Manager or commandline through terminal. Using Network Manager is convenient & better.
Say, the IP of your macbook is 192.168.1.10, then try assigning IP=192.168.1.12 to your EeePC eth0.
```
sudo ifconfig eth0 192.168.1.12
```
(remember, 192.168.1.12 is only for example. You may need to change it to mach your network's pattern.)

---

