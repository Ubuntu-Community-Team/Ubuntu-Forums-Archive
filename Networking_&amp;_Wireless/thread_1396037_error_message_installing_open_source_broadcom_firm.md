---
title: "error message installing open source broadcom firmware?"
date: 2010-02-01
forum: Networking &amp; Wireless
---

### Post by Wintermut3 on 2010-02-01
Hi,

I'm trying to get my BCM4306 wireless card working, as detailed on [this thread]("http://ubuntuforums.org/showthread.php?t=1393739"). I've tried most other things and am now attempting to use the open source firmware, as described in the guide at:
[http://linuxfans.keryxproject.org/?page_id=54](http://linuxfans.keryxproject.org/?page_id=54)

I've got to the section on actually building the firmware, and after doing
> wget [http://www.ing.unibs.it/openfwwf/firmware/openfwwf-5.2.tar.gz](http://www.ing.unibs.it/openfwwf/firmware/openfwwf-5.2.tar.gz)
tar -xvf openfwwf-5.2.tar.gz
cd openfwwf-5.2
makeI get an error on 'make':
> b43-asm ucode5.asm ucode5.fw --cpp-args -DDEBUG=1 -- --ivalext .fw --psize
gcc: error trying to exec 'cc1plus': execvp: No such file or directory
Assembler ERROR:
  No %arch defined
make: *** [ucode5.fw] Error 1
which may as well be in Greek to me. Anyone care to explain what it means or what I can do to make it go away? :)

---

### Post by chaanakya_chiraag on 2010-02-01
I'm guessing you don't have the necessary utilities to build the stuff.  Try this:
```
sudo aptitude install build-essential
```
and then rerun make.

---

### Post by Wintermut3 on 2010-02-01
Thanks :)

That fixed the error, and I was able to complete the installation.... but still no wireless :(

Some random debug output I've picked up on the way (apologies if this is irrelevant, I'm very new to all this and picking it up as I go along)

iwconfig
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0dmesg | grep -e b43
> 
[    2.446397] b43-pci-bridge 0000:02:02.0: PCI INT A -> Link[LNK3] -> GSI 17 (level, low) -> IRQ 17
[   25.707186] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
lshw -C network
> 
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:72:0a:39
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.1.66 latency=64 maxlatency=64 mingnt=32 multicast=yes
       resources: irq:18 ioport:7000(size=256) memory:e0108800-e01088ff
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:17 memory:e0104000-e0105fff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:ec:69:4e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
None of it means a thing to me but hopefully someone will be able to work out from it if I even managed to install the thing correctly. :confused:

---

### Post by chaanakya_chiraag on 2010-02-01
Is Network Manager not showing any of the networks?  Try installing wicd and seeing if that works out better.  Also, look up the man pages for ifup and ifdown to see if they will get you connected.

---

### Post by Wintermut3 on 2010-02-04
Thanks - I don't really know how I'm supposed to use that, though?

All I've got listed in /etc/network/interfaces is:
auto lo
iface lo inet loopback

I tried running
ifup -a

and got this error:
ifup: failed to open statefile /var/run/network/ifstate: Permission denied

:confused:

Also - I've got Wicd installed and all it every says is "no wireless networks found".

---

### Post by chaanakya_chiraag on 2010-02-04
You need to use ifup and ifdown with root permissions.  Therefore, the complete command would be
```
sudo ifup
```

---

