---
title: "Slow/Dropped Wireless Connection Ubuntu 12.04"
date: 2012-07-15
forum: Networking &amp; Wireless
---

### Post by alayahlan on 2012-07-15
I have an Acer Aspire 5733 setup to dual boot Ubuntu 12.04 & Windows 7. My wireless internet connection under Windows 7 is rock solid, but with Ubuntu the connection is painfully slow or non-existent causing pages not to load or say they are unavailable. Refreshing the page will sometimes reconnect in a few seconds. I get constant errors about connecting in Evolution. I seem to loose connection every few minutes.

I upgraded from Ubuntu 11.10 last week. I had a similar (although not as bad) connection problem with 11.10. It seems to have gotten worse since the upgrade.

I'm still fairly new to Ubuntu, so I probably know just enough to get myself into trouble on my own. I know there isn't a problem with the router or wireless card since it works well in Windows, how do I fix the Ubuntu connection?


> ~$ lspci
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe (rev 01)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

> ~$ ifconfig
eth0      Link encap:Ethernet  HWaddr b8:70:f4:e8:74:a4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4621 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:383544 (383.5 KB)  TX bytes:383544 (383.5 KB)

wlan0     Link encap:Ethernet  HWaddr d0:df:9a:8f:c5:c7  
          inet addr:192.168.2.6  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::d2df:9aff:fe8f:c5c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43840 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40140 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:42037070 (42.0 MB)  TX bytes:7015357 (7.0 MB)

> ~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"fuzzypickles"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 08:86:3B:3B:01:28   
          Bit Rate=52 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:34  Invalid misc:1   Missed beacon:0

eth0      no wireless extensions.

---

### Post by steeldriver on 2012-07-15
can you please check the driver with

```
lshw -c network
```

and/or

```
lspci -vnn | grep -i net
```

it should be something like 'ath5k' or 'ath9k'

---

### Post by alayahlan on 2012-07-15
> ~$ sudo lshw -c network
[sudo] password for alayahlan: 
  *-network               
       description: Ethernet interface
       product: NetLink BCM57780 Gigabit Ethernet PCIe
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 01
       serial: b8:70:f4:e8:74:a4
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=half firmware=sb latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:43 memory:d3400000-d340ffff
  *-network
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: d0:df:9a:8f:c5:c7
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-26-generic-pae firmware=N/A ip=192.168.2.6 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2400000-d240ffff

> ~$ lspci -vnn | grep -i net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)

Is this correct?

---

### Post by steeldriver on 2012-07-15
OK I'm not *sure* this fix is still recommended but I believe you can try

```
sudo modprobe -r ath9k

sudo modprobe ath9k nohwcrypt=1
```

if that works we can make it permanent via a conf file

---

### Post by alayahlan on 2012-07-15
Unfortunately, this does not appear to have fixed the problem.
What is my next step to try?

---

### Post by alayahlan on 2012-07-17
I came across this link and decided to give it a try:
[http://tech.chandrahasa.com/2012/05/31/fixing-wifi-regulatory-rule-in-unix/](http://tech.chandrahasa.com/2012/05/31/fixing-wifi-regulatory-rule-in-unix/)

Although my country code was set to TW instead of US for some reason, changing this did not appear to change anything.

I also tried the advice in this thread, again to no avail:
[http://ubuntuforums.org/showpost.php?p=12088241&postcount=31](http://ubuntuforums.org/showpost.php?p=12088241&postcount=31)

Every other minute or so, pages fail to load saying DNS lookup failed and Evolution email gives an error claiming it did not have a connection.

---

### Post by Finnicella on 2012-07-17
You can try with this command:
```
sudo rfkill unblock all
```
Bye

---

### Post by alayahlan on 2012-07-19
That didn't work Finnicella.

Problem is still persisting.

---

### Post by alayahlan on 2012-07-19
I had a USB wireless adapter lying around, so I attempted using it to see if the connection was more stable. I was able to connect using it, but the connection was no better.

---

### Post by Finnicella on 2012-07-20
I found this on the web, I hope will be helpful:

```
It's the old hwcrypt problem. In case you upgrade the kernel,
and have no access to the web, don't blame network manager
or wpasupplicant, create a file named (with sudo gedit)

/etc/modprobe.d/ath9k.conf 

with the contents

options ath9k nohwcrypt=1

and reboot
```

Bye

---

### Post by alayahlan on 2012-07-22
That is the same command steeldriver had me try earlier. Unfortunately, it had no effect.

---

### Post by alayahlan on 2012-07-23
The exact error I get when pages stop loading is as follows if this helps.

> This webpage is not available
The server at whatever_webpage_I_was_trying_to_go_to.com can't be found, because the DNS lookup failed. DNS is the network service that translates a website's name to its Internet address. This error is most often caused by having no connection to the Internet or a misconfigured network. It can also be caused by an unresponsive DNS server or a firewall preventing Chromium from accessing the network.
Here are some suggestions:
Reload this webpage later.
Check your Internet connection. Restart any router, modem, or other network devices you may be using.
Check your DNS settings. Contact your network administrator if you're not sure what this means.
Try disabling network prediction by following these steps: Go to the wrench menu > Settings > Under the Hood and deselect "Predict network actions to improve page load performance." If this does not resolve the issue, we recommend selecting this option again for improved performance.
Add Chromium as a permitted program in your firewall's or antivirus software's settings. If it is already a permitted program, try deleting it from the list of permitted programs and adding it again.
If you use a proxy server, check your proxy settings or contact your network administrator to make sure the proxy server is working. If you don't believe you should be using a proxy server, adjust your proxy settings: Go to the wrench menu > Settings > Under the Hood > Change Proxy Settings... and make sure your configuration is set to "no proxy" or "direct."
Error 105 (net::ERR_NAME_NOT_RESOLVED): Unable to resolve the server's DNS address.

---

### Post by alayahlan on 2012-07-25
Still having the same issue. The DNS errors are happening at the most inopportune time, like when I'm attempting to pay a bill online and the page craps out before I get a confirmation, leaving me to wonder if the transaction actually went through.

Any help would be appreciated.

---

### Post by alayahlan on 2012-07-30
Update: The problem seems to be worse the longer the computer is on. I have fewer problems when I first load Ubuntu than after I've been using it for a few hours.

---

### Post by alayahlan on 2012-08-29
Still having a lot of connection problems. I seem to be disconnected more than connected anymore. I sometimes have to reload the same page 4 or 5 times before it loads. If I am connected via ethernet cable, I have no issues at all, so it is strictly a wireless problem. The same computer booted up under windows has no connection problems wirelessly, so I know it is not a hardware or router issue.

Any help at all would be much appreciated.

---

### Post by dnukumamras on 2012-12-21
Open a terminal window (alt+ctrl+t)
and type

 sudo rmmod -f iwlwifi

then
 sudo modprobe iwlwifi 11n_disable=1

now check if the speeds have improved. if yes lets make it permanent

type
gksudo gedit /etc/modprobe.d/iwlwifi_disable11n.conf

add the line

options iwlwifi 11n_disable=1

to the end of the file.save and quit!!!


Replace iwlwifi with iwlagn in the above commands in-case you get an error like

ERROR: Removing 'iwlwifi': No such file or directory.:D

---

### Post by chofo1979 on 2013-01-13
I had the same problem when I upgraded my kernel to fix some power management issues. 

This solved my wifi problems:

Go to [http://wireless.kernel.org/en/users/Download/stable/]("http://wireless.kernel.org/en/users/Download/stable/") and download the appropiate driver for your kernel.

Unpack the file you just downloaded in a new folder into your downloads folder. (it should be something like Downloads/compat-wireless-3.5.4-1-snp) (beware: your filename might be different)

You will probably need the build tools; open a terminal and type:

```
sudo apt-get install build-essential linux-headers-generic
```

Then after you have installed build-essential and headers, please do:

```

cd Downloads/compat-wireless-3.5.4-1-snp
sudo su
make
make install
modprobe -r ath9k
modprobe ath9k
exit
```

My computer crashed shortly after the 2nd modprobe, but when I restarted everything ran lightspeed!!!:popcorn:

Hope this helps you!

Credits to chili555 for his post here: [http://ubuntuforums.org/showthread.php?t=2035156]("http://ubuntuforums.org/showthread.php?t=2035156")

---

