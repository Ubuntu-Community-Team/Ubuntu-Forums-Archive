---
title: "Slow web page loading in 12.04 (slow in all browsers, fast in Windows)"
date: 2012-06-23
forum: Networking &amp; Wireless
---

### Post by mawxcarroll on 2012-06-23
Hi,
  I just upgraded to Ubuntu 12.04 and now page loading in both Firefox and Chrome is very slow.  Page loading under Windows and on my iPad on the same network continues to be quite fast.  A page that loads under Windows near instantaneously takes about 10-15 seconds to load in Ubuntu.

However, Ubuntu reports the same network speeds.  Speedtest.net provides the perfect test:

under Windows, the website loads quickly, quickly determines which server to use, and then reports about 25 ms ping, 20 mbps download, and 4 mbps upload

under Ubuntu, the website takes a long time to load, takes a long time to determine the server to use, and then reports the exact same statistics

Feels like a DNS issue, but I can't see how Windows would be faster since they're connecting to the same router.

I have tried disabling ipv6 in the browsers and in sysctl.conf with the lines:

```
# IPv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1
```

Any help would be greatly appreciated!

Thanks!
tom

Specs and outputs:

Dell Latitude e6410
4 GB RAM
Intel Core i5, 2.67GHz x 4
Kernel 3.2.0-25-generic
12.04, 64-bit


```
lspci | grep Network
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 05)
03:00.0 Network controller: Broadcom Corporation BCM43224 802.11a/b/g/n (rev 01)

```

```
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:4  Signal level:197  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

```

```
lsmod
Module                  Size  Used by
michael_mic            12612  8 
arc4                   12529  4 
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  4 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
bnep                   18281  2 
joydev                 17693  0 
binfmt_misc            17540  1 
btusb                  18288  0 
bluetooth             180104  11 rfcomm,bnep,btusb
snd_hda_codec_idt      70795  1 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
ppdev                  17113  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
psmouse                87692  0 
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32866  0 
nvidia              12319264  47 
wmi                    19256  1 dell_wmi
snd_timer              29990  2 snd_pcm,snd_seq
lib80211_crypt_tkip    17390  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  19596  0 
intel_ips              18089  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2568210  0 
mac_hid                13253  0 
lib80211               14381  2 lib80211_crypt_tkip,wl
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_ohci          41000  0 
firewire_core          63558  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                156693  0 

```

```
dmesg | grep eth1
[   26.290452] eth1: Broadcom BCM4353 802.11 Hybrid Wireless Controller 5.100.82.38
[   68.835645] eth1: no IPv6 routers present
[ 2937.625361] eth1: no IPv6 routers present

```

```
sudo lshw -C network
[sudo] password for tcarroll: 
  *-network               
       description: Ethernet interface
       product: 82577LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 05
       serial: 5c:26:0a:30:88:15
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e latency=0 multicast=yes
       resources: irq:20 memory:e9600000-e961ffff memory:e9680000-e9680fff ioport:8040(size=32)
  *-network
       description: Wireless interface
       product: BCM43224 802.11a/b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: c0:cb:38:20:7f:63
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.38 ip=192.168.1.125 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:17 memory:e6e00000-e6e03fff

```

---

### Post by mawxcarroll on 2012-07-01
Solved!  This did turn out to be a DNS issue.

Not sure why this is the case, but I tracked the problem down to the new resolvconf system in Ubuntu.  I was getting the following error when I tried to run resolvconf

```
resolvconf: Error: /etc/resolv.conf must be a symlink
```

I fixed this error using dpkg-reconfigure

```
sudo dpkg-reconfigure resolvconf
```

Just agree/ok everything and then restart your networking (or just restart your computer).  You might also need to clear out your browser caches.

Cheers,
tom

---

### Post by matrixzz on 2012-10-01
Thanks for sharing the info... I also had a similar problem where my firefox and chrome fail to load pages (pages continuously tries to load but nothing appeared). Sometime I had to click on the address bar and enter manually again.

The solution above did help improved the situation. Thank you. :)

---

### Post by popper668 on 2012-12-20
after hitting enter / ok just reboot or do I have to wait until some type of prompt?

---

### Post by jdthood on 2013-01-04
> **mawxcarroll said:**
> I fixed this error using dpkg-reconfigure

See the following bug report (especially comment #82) for info about why you might have had to do this.

[https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244](https://bugs.launchpad.net/ubuntu/+source/resolvconf/+bug/1000244)

---

