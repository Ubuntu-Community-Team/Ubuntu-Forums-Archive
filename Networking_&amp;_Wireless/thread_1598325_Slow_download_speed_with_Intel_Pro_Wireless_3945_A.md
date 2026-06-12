---
title: "Slow download speed with Intel Pro Wireless 3945 ABG on Ubuntu 10.10 on HP dv2000"
date: 2010-10-16
forum: Networking &amp; Wireless
---

### Post by Rybo85 on 2010-10-16
I've done a clean install of Ubuntu 10.10 on my HP Pavilion dv2000 laptop. I can connect to my wireless network just fine, but the download speed hasn't been all that it could be.

I've performed a couple download speed tests which are below.

[http://www.speakeasy.net/speedtest/-](http://www.speakeasy.net/speedtest/-) around 1.5 Mbps

[http://www.speedtest.net/-](http://www.speedtest.net/-) around 1 Mbps


When I enabled the wireless on my iMac(Mac OS X 10.6.x) and performed the same tests, I got the following results.

[http://www.speakeasy.net/speedtest/-](http://www.speakeasy.net/speedtest/-) around 20 Mbps

[http://www.speedtest.net/-](http://www.speedtest.net/-) around 13 Mbps


With my wired connection enabled instead on my Ubuntu machine, I was getting download speed test results more like with the wireless on my iMac.


1. Has anyone else run into a situation similar to mine, but was able to increase the download speed performance somehow? If so, how?

2. Should I think about trying the Ndiswrapper solution like in [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper) ? The thing with this though is that URL doesn't mention Ubuntu 10.10 yet.

3. I went to the [http://packages.ubuntu.com/search?keywords=maverick](http://packages.ubuntu.com/search?keywords=maverick)  URL and noticed there was a Package linux-backports-modules-wireless-maverick-generic  entry, which I guess is the newest version of the ubuntu wireless packages described in [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download). Would it be worth it to try and install this package?


```
Machine Brand and Model:
HP Pavilion dv2000
```


```
Wireless Brand/Model:
05:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
        Subsystem: Hewlett-Packard Company Device 135b
        Flags: bus master, fast devsel, latency 0, IRQ 44
        Memory at d4000000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>
        Kernel driver in use: iwl3945
        Kernel modules: iwl3945
```


```
iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"[insert real name here]"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:14:6C:6F:42:08   
          Bit Rate=54 Mb/s   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-38 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



```
Wireless Modules:
lsmod | grep "iwl3945"
iwl3945                85550  0 
iwlcore               127415  1 iwl3945
mac80211              231541  2 iwl3945,iwlcore
cfg80211              144470  3 iwl3945,iwlcore,mac80211
```



```
Potentially Relevant Kernel Boot Messages:
dmesg | grep "iwl3945"
[   11.310787] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   11.310791] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[   11.310880] iwl3945 0000:05:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   11.310895] iwl3945 0000:05:00.0: setting latency timer to 64
[   11.351408] iwl3945 0000:05:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   11.351413] iwl3945 0000:05:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   11.351570] iwl3945 0000:05:00.0: irq 44 for MSI/MSI-X
[   11.848891] iwl3945 0000:05:00.0: loaded firmware version 15.32.2.9
```


```
Network Configuration:
sudo lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 02
       serial: 00:18:de:05:64:d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.35-22-generic firmware=15.32.2.9 ip=192.168.1.5 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:44 memory:d4000000-d4000fff
```



```
Kernel Architecture:
uname -mr
2.6.35-22-generic i686
```

---

### Post by CbrPad on 2010-10-16
Hi, there does seem to be a bug reported about this, see...

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/621265)


I've got the very same laptop and have also just done a clean install however I can't get wireless to work at all.

---

### Post by Rybo85 on 2010-10-16
Thanks for the bug link. I registered at that site and listed myself as one of the affected.

---

### Post by FuturePilot on 2010-10-23
I've got the same problem with Maverick. There was some discussion [here]("http://ubuntuforums.org/showthread.php?t=1520713") about the problem. There more links in the first post of that thread.

---

### Post by snagz on 2010-12-22
I'm experiencing the same issue, I've been testing it by copying files from a server in my house using FTP.  Transfer rates average 200KB/s or so with the Maverick kernels, however if I use the 2.6.32-21 Lucid kernel I get speeds of 3MB/s!

Here's how I installed the Lucid kernel...

Add these lines to /etc/apt/sources.list:
deb http://us.archive.ubuntu.com/ubuntu/ lucid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ lucid main restricted

sudo apt-get update
sudo apt-get install linux-image-2.6.32-21-generic

This installs the image, but since it's an older image, grub doesn't boot to it.  You have a few options here.  You can try to press ESC on boot to get into the grub menu then manually select the 2.6.32-21 image.  I have a hard time with the timing and miss it often.  To increase the timeout edit /etc/default/grub and increase the GRUB_HIDDEN_TIMEOUT to something like 5.  That gives you more time to press escape.  

To make it boot 2.6.32-21 by default, get into the grub menu by pressing ESC right before Ubuntu boots.  Count the grub menu entries to the kernel you want, mine was entry 6.  Edit /etc/default/grub and change GRUB_DEFAULT=0 to that number.  Now your system will boot that kernel automatically.

It works great for me, I know some would rather have a fix for the 2.6.35 kernel, but I don't know of any improvements in 2.6.35 that I need!

Thanks,
Chris

---

### Post by PStedem on 2011-01-08
@snagz

I just wanted to say thanks because I've spent quite a few hours attempting to fix this iwl3945 issue.

I attempted to get ndiswrapper going with ~10 different drivers (a working 64-bit driver is nowhere to be found), played with my router's settings, disabled wireless powersaving and used several other proposed solutions. However, none of them worked until I tried your solution.

This works. I note no ill effects so far. From a download speed of ~0.5Mbit/s to ~10Mbit/s.

Thanks,

Patrick

---

### Post by guntbert on 2011-02-09
> **snagz said:**
> 

Here's how I installed the Lucid kernel...



thx for trying/testing/sharing

that is a useful workaround for me too

guntbert

---

