---
title: "Wireless issues Novatech 1411 / Ubuntu 12.10/Kernel 3.5.0-17/Intel Wireless-N 2230"
date: 2012-11-01
forum: Networking &amp; Wireless
---

### Post by slipp3ryWhippit on 2012-11-01
Relative Linux newb, some past usage but by no means an expert.

Got a new ultrabook and ditched Windows completely.

Am having problems with signal strength over distance with the wireless connection. 

Router and card are both N grade. Currently using the default driver.

Other laptops are getting very good range but this one the signal strength is dropping drastically proportionally with distance from router for example an older laptop running G wireless on XP gets 54Mbps at the same place the Novatech is picking up >1Mbps.

Perfect connection when stood near router, completely unusable at very short distances away.

Any help massively appreciated.





***_lspci:_***

Network controller: Intel Corporation Centrino Wireless-N 2230 (rev c4)

***_ifconfig:_***

eth0      Link encap:Ethernet  HWaddr 4c:72:b9:e3:62:95  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:878 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83569 (83.5 KB)  TX bytes:83569 (83.5 KB)

wlan0     Link encap:Ethernet  HWaddr 84:a6:c8:0a:5b:95  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::86a6:c8ff:fe0a:5b95/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8414 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8410 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5031950 (5.0 MB)  TX bytes:1527279 (1.5 MB)


***_iwconfig wlan0:_***

wlan0     IEEE 802.11bgn  ESSID:"cookiemonster"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:8E:F2:A5:92:E4   
          Bit Rate=1 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=30/70  Signal level=-80 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:7  Invalid misc:26   Missed beacon:0



***_ sudo lshw -C network:_***

  *-network               
       description: Wireless interface
       product: Centrino Wireless-N 2230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: c4
       serial: 84:a6:c8:0a:5b:95
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-17-generic firmware=18.168.6.1 ip=192.168.0.15 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:45 memory:f7c00000-f7c01fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 07
       serial: 4c:72:b9:e3:62:95
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:42 ioport:e000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff

---

### Post by chili555 on 2012-11-01
> Router and card are both N grade. Currently using the default driver.I'm surprised it connects at all. Please try a temporary driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Is there any improvement?

---

### Post by slipp3ryWhippit on 2012-11-01
> **chili555 said:**
> I'm surprised it connects at all. Please try a temporary driver parameter:```
sudo modprobe -r iwlwifi
sudo modprobe iwlwifi 11n_disable=1
```Is there any improvement?

Hi Chili555, thanks for the reply.

I tried that, unfortunately no effect.

As part of of my investigations I have noticed that although distance makes the problem more frequent and longer lasting the speed will still drop to <~ 1Mb/s even when very close to the router.

And on that point to clarify observed behaviour, sometimes it will be running at normalish speeds then all of a sudden drop to <~ 1Mb/s

---

### Post by robbiemacg on 2012-11-03
I've just noticed that **/etc/modprobe.d/iwlwifi.conf** has changed since the update to 12.10. Take a look at your file and see if it now looks like this:

```

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```

---

### Post by chili555 on 2012-11-03
Whoa!!! I learn something new, often astounding, every day. I do have that file! However, and I'd appreciate your checking this, I do not have either iwldvm or iwlmvm loaded:> chili@LAPTOP410:~$ lsmod | grep iwl
iwlwifi               348544  0 
mac80211              461161  1 iwlwifi
cfg80211              175375  2 iwlwifi,mac80211I also see no reference to either in syslog. It actually looks like the intent is to remove first mac80211 and then iwlwifi.

Hmmmmm.

---

### Post by slipp3ryWhippit on 2012-11-03
Hi robbiemacg, thanks for looking at my question, this is what I've got in mine, 

# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

although I have no idea if that is a good thing or a bad thing?

---

### Post by chili555 on 2012-11-03
A very interesting read. It appears that the purpose of the conf file is to remove modules in the correct order transparent to we ordinary users: [http://comments.gmane.org/gmane.linux.kernel.wireless.general/89422](http://comments.gmane.org/gmane.linux.kernel.wireless.general/89422)

However, as robbiemacg quite correctly implies, if we want to add a driver parameter, 11n_disable=1, for instance, it must be added to the end of the conf file and *_not_* replace or remove it.

I was fascinated by this:> Do users need to remove modules at all? I doubt it. And if they do, they will use rmmod, because it is faster to type :).I guess the devs at kernel.org never frequent the forums. We modprobe -r <some_module> every day and for good reason.

---

### Post by robbiemacg on 2012-11-04
I think [chili555]("http://ubuntuforums.org/member.php?u=35909") has a good sense of where my line of investigation seemed to lead. That said, due credit for digging in, taking things further and finding a reliable source of information!

Back to the problem at hand. Can we aid [slipp3ryWhippit]("http://ubuntuforums.org/member.php?u=1750593") by suggesting the addition of a line like this to the conf itself?:
```

options iwlwifi 11n_disable=1

```

I've not thought this all the way through, but I suspect the solution will be something along those lines.

---

### Post by chili555 on 2012-11-04
We could, except he says:> I tried that, unfortunately no effect.
I'm not sure I have any better ideas.

---

### Post by robbiemacg on 2012-11-04
After reading the conf, checking out that dev thread, I'm still not 100% clear on  how modules are loaded and at what point in the process we can modify them.
My question is, could it be too late to effectively modify the module using the standard CLI method once the conf has already done its work? Might we need to include an **options** line in the conf, rather than trying to reload **iwlwifi** with a modification after the conf has already done it's work of loading/removing/etc.? 
IDK. This is a genuine question for me. I might just spin up the laptop and do some experimenting after work&#8230; see if I can learn something new.

---

### Post by chili555 on 2012-11-04
If you wish to try a driver parameter temporarily:```
sudo modprobe -r <module>
sudo modprobe <module> <parameter>
```The conf file is used to invoke the parameter automagically persistently on boot:```
options <module> <parameter>
```Learn what parameters are available with *modinfo*. For example:> chili@LAPTOP410:~$ modinfo iwlwifi
filename:       /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
alias:          iwlagn
license:        GPL
author:         Copyright(c) 2003-2012 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
<snip>
vermagic:       3.5.0-17-generic SMP mod_unload modversions 686 
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: agg TX, 4: agg RX (uint)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart:restart firmware in case of error (int)
parm:           antenna_coupling:specify antenna coupling in dB (defualt: 0 dB) (int)
parm:           bt_ch_inhibition:Enable BT channel inhibition (default: enable) (bool)
parm:           plcp_check:Check plcp health (default: 1 [enabled]) (bool)
parm:           wd_disable:Disable stuck queue watchdog timer 0=system default, 1=disable, 2=enable (default: 0) (int)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           auto_agg:enable agg w/o check traffic load (default: enable) (bool)
parm:           5ghz_disable:disable 5GHz band (default: 0 [enabled]) (bool)Note some parameters are invoked with an integer (int) and some boolean (bool). In most cases, boolean means Y or N.

Finally, see what state parameters are set to with:```
cat /sys/module/<module>/parameters/<parameter> 
```For example:> chili@LAPTOP410:~$ cat /sys/module/iwlwifi/parameters/11n_disable
[COLOR="Red"]0[/COLOR]
There ya go! That's all I know about parameters; however, the day is early!

---

### Post by slipp3ryWhippit on 2012-11-08
Would it help to download the drivers directly? 

Is there a way to tell what version the kernel is currently using?

---

### Post by chili555 on 2012-11-08
If you haven't downloaded and compiled compat-wireless, I'm sure you have the stock in-tree version. Before we try compat-wireless, please do:```
sudo gedit /etc/modprobe.d/iwlwifi.conf
```As has been pointed out above, it ought to contain text already:```
# /etc/modprobe.d/iwlwifi.conf
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the
# microcode file installed on the system.  When removing iwlwifi, first
# remove the iwl?vm module and then iwlwifi.
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

```At the end, add one new line:```
options iwlwifi 11n_disable=1 bt_coex_active=N
```Proofread, save and close gedit. Reboot and let us have a report.

---

### Post by slipp3ryWhippit on 2012-11-10
Hi Chili,

Just to let you know I have done this.

I'm trialling it for a bit. The network speed is dropping down every now and again but seems (at the moment) to have much better speed at distance and when it does drop down recovers fast.

Thanks,
Slip

---

### Post by chili555 on 2012-11-10
We look forward to your report.

---

### Post by slipp3ryWhippit on 2012-11-15
I've been trying it out for a few days now, it's quite subjective but I think it's better in some areas. 

In other areas though it's still unusable at relatively short distances ~20 feet

---

### Post by slipp3ryWhippit on 2012-12-04
Any other ideas in the offing?

---

### Post by chili555 on 2012-12-04
> **slipp3ryWhippit said:**
> Any other ideas in the offing?Sorry, my best shot is above. If that doesn't do it, I'm afraid I have nothing further.

---

