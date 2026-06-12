---
title: "No wirless after ndiswrapper"
date: 2010-12-31
forum: Networking &amp; Wireless
---

### Post by forza.stiinta on 2010-12-31
Hello!

I have lenovo thinkpad, T61 with Intel 4965AGN wireless card. 
It is a N card, it works under N mode in windwos, but not in Ubuntu (10.10).

I installed ndiswrapper and got the windows xp drivers for this card. the issue is that i got an error when installing the drivers and since then I cannot use wireless.

The error i got is:```
Module could not be loaded. Error was:

FATAL: Could not read '/lib/modules/2.6.35-24-generic/kernel/ubuntu/ndiswrapper/ndiswrapper.ko': No such file or director
```

I unistalled the driver, but now under network connections no wireless connections appear, nothing. I cannot use wirless anymore.

Any solutions? At leas now I would like to turn wireless on and use it as it is, N mode can wait. :-)

---

### Post by bkratz on 2010-12-31
You probably did not need ndiswrapper at all and should probably remove it, anyway your original question should be answered in the third post here.

[http://kubuntuforums.net/forums/index.php?topic=3114240.0](http://kubuntuforums.net/forums/index.php?topic=3114240.0)

---

### Post by forza.stiinta on 2010-12-31
Thanks for the quick reply.

I needed (or thought i did) ndiswrapper because it does not work in N mode.

I followed the advice in your link, but it is not working. The wireless device does not appear if i run ifconfig, nor I can see anything related to wireless in network manager.

I uninstalled ndiswrapper, still nothing.

---

### Post by bkratz on 2010-12-31
Can you post the output of 

sudo lshw -C network

and 

rfkill list

if no output to the second command

sudo apt-get install rfkill

then try again.


also here is a very similar posting, look at number two

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664414](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/664414)

---

### Post by forza.stiinta on 2011-01-01
First of all, Happy New Year to you all!

Here's the output for the lshw command - it appears that the wireless is "unclaimed"

```
 *-network               
       description: Ethernet interface
       product: 82566MM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:1e:37:18:6f:ed
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 duplex=full firmware=0.3-0 ip=192.168.1.102 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:46 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:df2fe000-df2fffff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
```

Second command output is:

```
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

---

### Post by PatchesTheCaveman on 2011-01-01
Hi forza.stiinta!  Happy new year to you too!

Try running these commands to disable ndiswrapper and reactivate the native Linux driver for your device:
```
sudo modprobe -r ndiswrapper
sudo bash -c "echo blacklist ndiswrapper >> /etc/modprobe.d/blacklist.conf"
sudo modprobe iwl3945
```

After that, run ```
sudo iwconfig
``` to see if your wireless card reappears.  If it does, try reconnecting to the wireless.

If it doesn't run this command:
```
dmesg | grep -i iwl3945
```
and copy/paste it here so we can try and figure out what's going on.

---

### Post by forza.stiinta on 2011-01-01
I ran the 3 commands - none produced any output.

Running iwl3945 shows no wireless adapter, but the "dmesg | grep -i iwl3945" command outputs:

```
[  659.166553] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  659.166557] iwl3945: Copyright(c) 2003-2010 Intel Corporation

```

My adapter is Intel 4965 AGN

---

### Post by forza.stiinta on 2011-01-01
I forgot to mention that I uninstalled ndiswrapper  when I noticed that wireless is not working anymore.

---

### Post by bkratz on 2011-01-01
> **forza.stiinta said:**
> I ran the 3 commands - none produced any output.

Running iwl3945 shows no wireless adapter, but the "dmesg | grep -i iwl3945" command outputs:

```
[  659.166553] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  659.166557] iwl3945: Copyright(c) 2003-2010 Intel Corporation

```

My adapter is Intel 4965 AGN



The first three commands would not normally produce any output. You simply removed then blacklisted ndiswrapper then told it to load another module. You might want to copy/paste the output of 

lsmod

(LSMOD in lowercase) back here so we can see what modules are actually loaded.

---

### Post by forza.stiinta on 2011-01-02
Ok, a step forward. the wireless network looks to be working - i.e. i can see my wireless network but I cannot connect to it. It tries to connect but fails. there is no security enabled on the router, it should connect with no wpa/wep.

Here's the output of iwconfig:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"ChipROUTER"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
vboxnet0  no wireless extensions.


```

Currently I am using the same computer on the same network, but in windows, the router is working fine.

---

### Post by forza.stiinta on 2011-01-02
Update:

I forced the router to run in G mode, and now I can connect to the wireless.

Normally it is set to use mixed N+G, but using that config I cannot connect. Now the issue is making it to work in N mode, or at leas make it connect even if the router is N+G mode (like it was before).

I set options iwlagn 11n_disable=0 , nothing happens

---

