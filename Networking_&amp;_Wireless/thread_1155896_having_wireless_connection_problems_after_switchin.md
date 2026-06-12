---
title: "having wireless connection problems after switching from Xubuntu to Kubuntu"
date: 2009-05-11
forum: Networking &amp; Wireless
---

### Post by mntokman on 2009-05-11
I have a SONY VAIO laptop with Vista on it. I tried Xubuntu and setup the OS from windows platform. I was able to see a ubuntu folder with a 15GB space on it. 

Figured it might be better to format my disk for two different OS and switch to Kubuntu during the process. I knew that KDE platform forces the users write more codes for most things vs Gnome Desktop environment. Now I cannot setup my wireless connection on Kubuntu anymore. 

I have ADSL connection. My router and modem is a single device combined together and provided by my ISP. I was able to use my wireless connection on Xubuntu no problem. 

I attached ifconfig and lshw -C network outputs as well. 

Any help is appreciated.

PS: I am a beginner ubuntu user.

---

### Post by Peter09 on 2009-05-11
Hi,
sorry I cannot read your outputs in the format you posted. You can cut and paste into the QUOTE box.

---

### Post by mntokman on 2009-05-11
mntokman@greenworld:~$ lshw -C network
 WARNING: you should run this program as super-user.
   *-network                                         
        description: Wireless interface
        product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
        vendor: Intel Corporation
        physical id: 0
        bus info: pci@0000:02:00.0
        logical name: wmaster0
        version: 61
        serial: 00:13:e8:da:21:c1
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list logical ethernet physical wireless
        configuration: broadcast=yes driver=iwlagn latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
   *-network
        description: Ethernet interface
        product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
        vendor: Realtek Semiconductor Co., Ltd.
        physical id: 0
        bus info: pci@0000:06:00.0
        logical name: eth0
        version: 01
        serial: 00:1a:80:3e:ca:04
        width: 64 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical
        configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
   *-network DISABLED
        description: Ethernet interface
        physical id: 2
        logical name: pan0
        serial: 22:f9:fb:64:33:60
        capabilities: ethernet physical
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
 

 

  	 	 mntokman@greenworld:~$ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:1a:80:3e:ca:04
           UP BROADCAST MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
           Interrupt:220 Base address:0xe000
 

 lo        Link encap:Local Loopback
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:16436  Metric:1
           RX packets:200 errors:0 dropped:0 overruns:0 frame:0
           TX packets:200 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:0
           RX bytes:13648 (13.6 KB)  TX bytes:13648 (13.6 KB)
 

 wlan0     Link encap:Ethernet  HWaddr 00:13:e8:da:21:c1
           inet6 addr: fe80::213:e8ff:feda:21c1/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:476 errors:0 dropped:0 overruns:0 frame:0
           TX packets:46 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:85449 (85.4 KB)  TX bytes:6983 (6.9 KB)
 

 wmaster0  Link encap:UNSPEC  HWaddr 00-13-E8-DA-21-C1-31-63-00-00-00-00-00-00-00-00
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:0 errors:0 dropped:0 overruns:0 frame:0
           TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by Peter09 on 2009-05-11
Have you a network icon in the top corner - what happens when you click on it?

---

### Post by mntokman on 2009-05-11
i have a black and white earth icon for network connections. Both eth and wlan are disconnected. There is a password for my wireless connection. 

I tried to connect to two other unsecured connections, the strenght is very low but I was able to connect (or maybe not). I say I was able to because I saw the typical signal strength icon after connection is established to other networks.

---

### Post by mntokman on 2009-05-11
As a reminder, I do not have application launcher on top corner. I used to have on my Xubuntu but not on Kubuntu. 

All icons are at the bottom right corner.

---

### Post by Peter09 on 2009-05-11
So your wireless connection is working?

---

### Post by mntokman on 2009-05-11
I do not know what the real problem is. It does not work I think. I had no problem with my connection when I had Xubuntu installed. I installed Kubuntu today. The connection is always disconnected. System keeps disconnecting for some reason.

---

### Post by Peter09 on 2009-05-11
Have you been able to connect to a good strength wireless signal?

---

### Post by Peter09 on 2009-05-11
if its not working properly try-
This assumes you are using Jaunty

```
sudo apt-get install linux-backports-modules-jaunty-generic
```

---

### Post by mntokman on 2009-05-11
I get an error:

Reading package list: done
Building dependency tree
Reading state information...Done
E: Could not find package linux-backports-modules-jaunty-generic

---

### Post by Peter09 on 2009-05-11
Not sure if this package will help, it will not harm

```
sudo apt-get install linux-backports-modules-jaunty 
```

---

### Post by mntokman on 2009-05-11
still same error...:(

should I switch to Xubuntu again? Not sure if KDE is good for me yet.

---

### Post by Peter09 on 2009-05-11
edit removed

---

### Post by Peter09 on 2009-05-11
We need to update your wireless drivers, I'm just try to find where they are.

---

### Post by Peter09 on 2009-05-11
Try

```
sudo apt-get install jaunty-backports
```

---

### Post by Peter09 on 2009-05-11
This should work

```
sudo apt-get install linux-backports-modules-jaunty-generic
```

I can do this on my machine, you need to confirm your network connection.

---

### Post by Peter09 on 2009-05-11
Check in your Software Sources application that under Updates the jaunty-backports box is  ticked.

---

### Post by mntokman on 2009-05-11
> **Peter09 said:**
> Check in your Software Sources application that under Updates the jaunty-backports box is  ticked.

Hmm how do I do that? I know how to do it on Xubuntu but not on Kubuntu. 

I did try that code but it still does not work.

---

### Post by Peter09 on 2009-05-11
Sorry, I don't know how either, somewhere you need to enable backports....:(

---

### Post by mntokman on 2009-05-11
I made some progress. I tried to connect to internet with Ethernet cable it is working just fine. 

I also found how to upgrade and install softwares and packages. Still no wireless connection though

---

### Post by Peter09 on 2009-05-11
did you install the backports package?

---

### Post by mntokman on 2009-05-11
Hi Peter, I upgraded to KDE 4.2 and Ubuntu 9.04 during the whole process. For a moment my keyboard was not functioning and I was very frustrated but now I got it all up and running except wireless still. I will work on backport packages next and will update you soon. 

MNT

---

### Post by mntokman on 2009-05-13
> **Peter09 said:**
> Check in your Software Sources application that under Updates the jaunty-backports box is  ticked.

I did check but I do not see such an option.

---

### Post by Peter09 on 2009-05-13
In gnome its under Synaptic ->Software Sources->Updates

---

### Post by mntokman on 2009-05-13
Since I upgraded to Jaunty recently I added the repositories in the below and it started to download now. 
 
[http://azerdark.wordpress.com/2009/04/08/ubuntu-910-repository-list-indonesia/](http://azerdark.wordpress.com/2009/04/08/ubuntu-910-repository-list-indonesia/) 

How do you like Gnome? I think if would download Xubuntu, none of these would happen...:( 

Gnome takes care of stuff like this

---

### Post by mntokman on 2009-05-13
ok I finised installing the backport packages but still no wireless connection...:(

It keeps disconnecting automatically, does not even try to connect...I can see my router listed though.

---

### Post by Peter09 on 2009-05-13
Here is the bug - cannot see a fix here

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/277634)

---

### Post by mntokman on 2009-05-13
it was working when I setup xubuntu on windows for some reason, is it because I was using an earlier ubuntu version maybe? before 8.10

---

### Post by Peter09 on 2009-05-13
Noticed this in the bug report

> If the dropouts are only happening on 11n networks, maybe it's worth disabling 11n in iwlagn and seeing if this stops the dropouts:
 sudo modprobe -r iwlagn && sudo modprobe iwlagn 11n_disable=1
 or add 'options iwlagn 11n_disable=1' to /etc/modprobe.d/options to make it permanent.so try

```
sudo modprobe -r iwlagn && sudo modprobe iwlagn 11n_disable=1
```to test
and if it works do
>  add 'options iwlagn 11n_disable=1' to /etc/modprobe.d/options to make it permanent.


---

### Post by mntokman on 2009-05-14
it does not seem like working for me still...I wish they would post which ubuntu versions do not have this bug. I am downloading ubuntu right now again 8.04...and I will use gnome

---

