---
title: "what happen about my wireless (intel 3945 bg)"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by QQi on 2011-04-01
last update my wireless card not work

~$ dmesg | grep 3945
[   15.066106] iwl3945: Unknown parameter `11n_disable'
[   15.221879] iwl3945: Unknown parameter `11n_disable'


~$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

~$ sudo modprobe iwl3945 
FATAL: Error inserting iwl3945 (/lib/modules/2.6.38-7-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)



[COLOR="Red"]found something.. ?
[/COLOR]
~$ cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf 
options iwl3945 11n_disable=1


[B][COLOR="DarkRed"]------------------ [SOLVED] ------------------
[/COLOR][/B]
disable options my wireless it working again :D

~$ cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf 
# options iwl3945 11n_disable=1

---

### Post by ngsupb on 2011-04-01
> **QQi said:**
> last update my wireless card not work

~$ dmesg | grep 3945
[   15.066106] iwl3945: Unknown parameter `11n_disable'
[   15.221879] iwl3945: Unknown parameter `11n_disable'


~$ lspci | grep Wireless
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

~$ sudo modprobe iwl3945 
FATAL: Error inserting iwl3945 (/lib/modules/2.6.38-7-generic/kernel/drivers/net/wireless/iwlwifi/iwl3945.ko): Unknown symbol in module, or unknown parameter (see dmesg)



[COLOR="Red"]found something.. ?
[/COLOR]
~$ cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf 
options iwl3945 11n_disable=1


[B][COLOR="DarkRed"]------------------ [SOLVED] ------------------
[/COLOR][/B]
disable options my wireless it working again :D

~$ cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf 
# options iwl3945 11n_disable=1

yep. did the same.

Do you know what was that? :S

---

### Post by tjeremiah on 2011-04-01
same thing has happened to me. I tried the solution up above which didnt solve the issue.

---

### Post by ketk on 2011-04-01
> **tjeremiah said:**
> same thing has happened to me. I tried the solution up above which didnt solve the issue.

Same here with:  Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

Can't solve the issue. Also 64bit user.

---

### Post by QQi on 2011-04-01
try >> options iwl3945 disable_hw_scan=1

[http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/](http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/)

---

### Post by tjeremiah on 2011-04-01
> **QQi said:**
> try >> options iwl3945 disable_hw_scan=1

[http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/](http://www.dotkam.com/2008/11/17/configure-iwl3945-driver-on-ubuntu/)

i followed the step and it didnt solve the issue.

---

### Post by tjeremiah on 2011-04-01
I "solved" it by running 'recovery mode' in the grub menu and then running 'fix broken packages.' My wireless is currently back.

---

### Post by safarin on 2011-04-01
I also has this problem.. my problem solved! Thank you

---

### Post by ShatPank on 2011-04-01
I've got this exact same problem.
However being a bit noob, I think I'm missing something whilst trying to fix it as it's still not working for me.
could someone please explain what to do in complete lamens "do this, then type this...etc etc" terms

thanks
Stu


---------EDIT----------

Actually I got it working by substituting "vi" with "gedit" thanks guys :)

---

### Post by Starks on 2011-04-01
Fixed.

[https://launchpad.net/ubuntu/+source/module-init-tools/3.12-1ubuntu5](https://launchpad.net/ubuntu/+source/module-init-tools/3.12-1ubuntu5)

---

### Post by safarin on 2011-04-01
> **ShatPank said:**
> I've got this exact same problem.
However being a bit noob, I think I'm missing something whilst trying to fix it as it's still not working for me.
could someone please explain what to do in complete lamens "do this, then type this...etc etc" terms

thanks
Stu


---------EDIT----------

Actually I got it working by substituting "vi" with "gedit" thanks guys :)

I followed as post #1 by QQi,



> ~$ 
found something.. ?

cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf
options iwl3945 11n_disable=1


------------------ [SOLVED] ------------------

disable options my wireless it working again

~$ cat /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf
# options iwl3945 11n_disable=1

Just disable "options iwl3945 11n_disable=1" by put "#" in front of it.

```

$ gksu gedit /etc/modprobe.d/intel-3945-iwlagn-disable11n.conf

```

Save and restart.

If you use 64bit, maybe you could refer to tjeremiah's post

---

### Post by filiatra on 2011-04-06
Hello, 

After upgrade from 10.10 to 11.04 my wireless is dead. I tried many things out of forums (wicd, settings files, even installation of new drivers from compat-wireless) but no luck. Everytime the problem is the same:

Network-manager reports "wireless disabled by hardware switch"



I have blacklisted the module acer_wmi, since I don't have an acer card, and it is loaded.

Thank you for your help.

```

localhost ~$ lsmod | grep iwl
iwlagn                284569  0 
iwlcore               148965  1 iwlagn
mac80211              257001  2 iwlagn,iwlcore
cfg80211              156212  3 iwlagn,iwlcore,mac80211

localhost ~$ lspci | grep Wireless
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

localhost ~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

localhost ~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.

localhost ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:d3:b5:af:8b  
          inet addr:192.168.1.80  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d3ff:feb5:af8b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:433 errors:0 dropped:0 overruns:0 frame:0
          TX packets:500 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:346585 (346.5 KB)  TX bytes:62788 (62.7 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5240 (5.2 KB)  TX bytes:5240 (5.2 KB)

localhost ~$ dmesg | grep Intel
[    0.000000] ACPI: TCPA 9f6dfda2 00032 (v01 Intel   CRESTLN 06040000      00005A52)
[    0.062988] CPU0: Intel(R) Core(TM)2 Duo CPU     T7300  @ 2.00GHz stepping 0a
[    0.064003] Performance Events: PEBS fmt0+, Core2 events, Intel PMU driver.
[    2.392589] agpgart-intel 0000:00:00.0: Intel 965GM Chipset
[   23.635404] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   23.635407] iwlagn: Copyright(c) 2003-2010 Intel Corporation
[   23.635524] iwlagn 0000:06:00.0: Detected Intel(R) Wireless WiFi Link 4965AGN, REV=0x4
[   24.344680] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   24.344753] HDA Intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   24.344790] HDA Intel 0000:00:1b.0: setting latency timer to 64

localhost ~$ uname -a
Linux localhost 2.6.38-8-generic #41-Ubuntu SMP Tue Apr 5 19:29:52 UTC 2011 i686 i686 i386 GNU/Linux


```

---

### Post by safarin on 2011-04-06
what is the output using this command

```
sudo lshw -C network
```

---

### Post by filiatra on 2011-04-06
Here it is:
```
localhost ~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: NetLink BCM5906M Fast Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:16:d3:b5:af:8b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=sb v3.04 ip=192.168.1.80 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:47 memory:f4200000-f420ffff
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 61
       serial: 00:13:e8:16:6d:33
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-8-generic firmware=228.61.2.24 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn
       resources: irq:45 memory:f4300000-f4301fff

```

---

### Post by cariboo on 2011-04-06
@filiatra, could you also post the output of:

```
rfkill list
```

---

### Post by filiatra on 2011-04-06
@cariboo907: it is in my first post. Trying to unblock does not work!

---

### Post by cariboo on 2011-04-06
Oops, I didn't see it. This is a dumb question, but did you try the physical switch?

---

### Post by filiatra on 2011-04-06
> **cariboo907 said:**
> Oops, I didn't see it. This is a dumb question, but did you try the physical switch?

There is a common switch for both wireless and bluetooth. When I turn it off, the bluetooth icon disappears (bluetooth works normally) and I get: 
```

localhost ~$ rfkill list
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```


In fact, rfkill event is as follows:
```

localhost ~$ rfkill event
1302112328.994421: idx 1 type 1 op 0 soft 0 hard 1
1302112336.104434: idx 2 type 2 op 0 soft 0 hard 0
1302112336.105084: idx 2 type 2 op 2 soft 0 hard 0
1302112339.564661: idx 2 type 2 op 1 soft 0 hard 0

```
Physical switch off: first line
Physical switch on: first 3 lines
Physical switch off again:  all four lines

---

### Post by filiatra on 2011-04-06
Grrr!! I just tried Fn + F5 (keyboeard switch) and it worked!
Sorry for the trouble, but I was sure I had tried that before..
Thank you cariboo907 and everybody!

---

### Post by cariboo on 2011-04-06
I've noticed that quite a few laptops have both a function key and a physical switch, I guess that have both, as sometime the physical switch is located in a place that isn't very obvious. :)

---

