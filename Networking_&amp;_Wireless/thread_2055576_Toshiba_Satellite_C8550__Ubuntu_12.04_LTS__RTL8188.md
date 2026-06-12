---
title: "Toshiba Satellite C8550 / Ubuntu 12.04 LTS / RTL8188CE wirelss card -- Strange issues"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by brutikusarov on 2012-09-09
I will start by saying that Ubuntu 12.04 is installed on my laptop alongside Windows 7.  I have tried plugging my laptop directly into my router and modem, but it will not connect on Ubuntu.  It connects just fine on Windows 7.  I have even tried reverting to Ubuntu 11, but the problem persisted.

Since I cannot copy and paste the results from commands as shown directly on my laptop, I will do my best to type them up char for char.

In case it matters, I'd also like to state that I am new to Linux in general.

lspci results in:

```
Network controller:  Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
```iwconfig:

```
lo
no wireless extensions.

wlan0 IEEE 802.11bgn ESSID off/any
Mode:Managed Acces Point: Not-associated Tx=Power=20 dBm
Retry long limit: 7  RTS thr=2347 B  Fragment thr:off
Power Management:off
```
So, I cannot connect to a wireless or wired network at all from Ubtuntu on my laptop, but I can on Windows 7.  However, Ubuntu DOES recognize my network, and nearby networks.

My PC is currently connected to a router via a Netgear USB wireless adapter.  Every time I attempt to connect to my wireless on Ubuntu, my PC loses its connection.  I have tested this multiple times, and the connections always drops when I attempt to connect on Ubuntu.

---

### Post by brutikusarov on 2012-09-10
Turns out the wireless card works fine when I am on my college campus.  Still not working from home, though.

---

### Post by brutikusarov on 2012-10-02
Now that I am connected on campus, I can paste all the correct information straight from the terminal

lspci:
```
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8162 Fast Ethernet (rev 10)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)

```

lsusb:
```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 0bda:0129 Realtek Semiconductor Corp.
Bus 001 Device 004: ID 10f1:1a3d Importek 
```

ifconfig wlan0:
```
wlan0     Link encap:Ethernet  HWaddr 44:6d:57:42:b2:9f 
          inet addr:144.174.250.10  Bcast:144.174.251.255  Mask:255.255.252.0
          inet6 addr: fe80::466d:57ff:fe42:b29f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:38980 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20361 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:46393745 (46.3 MB)  TX bytes:2009667 (2.0 MB)

```

iwconfig:
```
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"FSUWIN" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:24:6C:CF:61:00  
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=56/70  Signal level=-54 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:173   Missed beaco
```


lsmod dealing with rtl:
```
rtl8192ce              75491  0
rtl8192c_common        69519  1 rtl8192ce
rtlwifi                95804  1 rtl8192ce
mac80211              436455  3 rtl8192ce,rtl8192c_common,rtlwifi
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178679  2 rtlwifi,mac80211

```

lshw -C network:

```
PCI (sysfs) 

  *-network UNCLAIMED    
       description: Ethernet controller
       product: AR8162 Fast Ethernet
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi msix bus_master cap_list
       configuration: latency=0
       resources: memory:b8500000-b853ffff ioport:3000(size=128)
  *-network
       description: Wireless interface
       product: RTL8188CE 802.11b/g/n WiFi Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 44:6d:57:42:b2:9f
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8192ce driverversion=3.2.0-29-generic-pae firmware=N/A ip=144.174.250.10 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:b8400000-b8403fff

```

uname -mr:

```
3.2.0-29-generic-pae i686

```

Can't connect from home still.

---

### Post by mikewhatever on 2012-10-03
Can you try the swenc=1 option, in other words:

sudo rmmod rtl8192ce

sudo modprobe rtl8192ce swenc=1

---

### Post by brutikusarov on 2012-10-08
> **mikewhatever said:**
> Can you try the swenc=1 option, in other words:

sudo rmmod rtl8192ce

sudo modprobe rtl8192ce swenc=1

I did not get any results with this.

Also, I've found that my "working" connection on campus is hardly a connection.  I cannot even install an IDE from the software center, and the connection drops within a few minutes

---

### Post by varunendra on 2012-10-11
> **brutikusarov said:**
> I did not get any results with this.
You won't get any 'results' with that command, it'll silently reload the driver with 'swenc=1' parameter. What is expected to change is the connection behaviour.

So, did the connection get any better after trying what *mike* suggested? Because that's all that is sometimes needed to be done.

But if it still doesn't work, you may try a few other parameters, individually or simultaneously (although I've never seen anyone using them, but they don't seem to hurt) :
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```This will also disable some power saving features of the module which (I assume) may impact connection stability.

**Important:** Do not restart after reloading the driver with any parameters. These changes are temporary and will be lost on reboot. So try connecting immediately after trying above commands.


**PS:**
Why are you using a [COLOR=Red]pae kernel[/COLOR]? Its often reported to be way too buggy. Your CPU is 64bit capable, so use a 64bit version of Ubuntu instead.

---

### Post by brutikusarov on 2012-10-25
> **varunendra said:**
> You won't get any 'results' with that command, it'll silently reload the driver with 'swenc=1' parameter. What is expected to change is the connection behaviour.

So, did the connection get any better after trying what *mike* suggested? Because that's all that is sometimes needed to be done.

On campus, it seems that the connection is more stable.  I have also fixed my ethernet connection, and connect at home or on campus via ethernet.  At home, however, I still cannot connect wirelessly.  When I try, it is in a perpetual state of "connecting" and my PC's wireless connection drops (it is connected via USB).   This leads me to believe that the two are interfering, though I had no luck connecting even after unplugging the USB.  The optimal case would be for me to be able to connect wirelessly from both machines simultaneously.

> 
But if it still doesn't work, you may try a few other parameters, individually or simultaneously (although I've never seen anyone using them, but they don't seem to hurt) :
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```This will also disable some power saving features of the module which (I assume) may impact connection stability.

**Important:** Do not restart after reloading the driver with any parameters. These changes are temporary and will be lost on reboot. So try connecting immediately after trying above commands.


I am going to try this now.

> 
**PS:**
Why are you using a [COLOR=Red]pae kernel[/COLOR]? Its often reported to be way too buggy. Your CPU is 64bit capable, so use a 64bit version of Ubuntu instead.

I don't know.  I will upgrade.

---

### Post by ahallubuntu on 2012-10-25
Did you try building your own driver from Realtek?

Check out this thread:

[http://ubuntuforums.org/showthread.php?t=2075870](http://ubuntuforums.org/showthread.php?t=2075870)

---

### Post by brutikusarov on 2012-11-05
> **varunendra said:**
> 
```
sudo modprobe -rfv rtl8192ce
sudo modprobe -v rtl8192ce swenc=1 ips=0 fwlps=0
```This will also disable some power saving features of the module which (I assume) may impact connection stability.

**Important:** Do not restart after reloading the driver with any parameters. These changes are temporary and will be lost on reboot. So try connecting immediately after trying above commands.

**PS:**
Why are you using a [COLOR=Red]pae kernel[/COLOR]? Its often reported to be way too buggy. Your CPU is 64bit capable, so use a 64bit version of Ubuntu instead.

I have done a clean install of ubuntu 12.04 LTS.  The connection issues persisted.  This code worked, and my connection at school seems more stable.  Also, my ethernet connection hasn't been recognized since the clean install.

Re:  your PS:
This new version is 64 bit.  I don't know what the difference is between a "pae kernel" and any other kernel is.  What should I do about it?

---

### Post by varunendra on 2012-11-05
> **brutikusarov said:**
> I have done a clean install of ubuntu 12.04 LTS.  The connection issues persisted.  This code worked, and my connection at school seems more stable.Can we call it a "Good news" then?

If you have tested it long enough and for a sufficient number of times to ensure it works everytime, we can make it permanent by writing a ".conf" file for this driver :
```
echo "options rtl8192ce swenc=1 ips=0 fwlps=0" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
However, I believe you shouldn't need all those three parameters. So try one at a time (starting with "swenc=1") and see if it works alone. If yes, use only that parameter in the '.conf' file. For example -
```
echo "options rtl8192ce swenc=1" | sudo tee /etc/modprobe.d/rtl8192ce.conf
```
We can test this stepwise if you wish.

> **brutikusarov said:**
> Also, my ethernet connection hasn't been recognized since the clean install.You should start a new thread for that to get best support. Post the details of your problem and the results of the following in your new thread :
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
```
Then post a link to that thread here so we can follow.


> **brutikusarov said:**
> This new version is 64 bit.  I don't know what the difference is between a "pae kernel" and any other kernel is.  What should I do about it?Since the new version is 64bit, you don't have a pae kernel anymore. PAE (Physical Address Extension) is an extension to 32 bit kernels to make them capable of handling more than 4GB of RAM (upto 64GB). A 64 bit kernel is already capable to do that (and much more).

---

