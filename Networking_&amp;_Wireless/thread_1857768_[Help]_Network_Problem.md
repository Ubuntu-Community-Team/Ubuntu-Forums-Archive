---
title: "[Help] Network Problem"
date: 2011-10-10
forum: Networking &amp; Wireless
---

### Post by carlosbgois on 2011-10-10
I know it's a recurrent topic in here, but I'm pretty new to linux and couldn't get any help reading the old ones.

My case is that i've installed ubuntu 11.04 but can't make wired network work. This same PC had an older version, maybe 10.04, in which networking was fine.

What may have happened? Wrong installation? Maybe the driver is not present in the newer version os ubuntu? Should I consider reinstalling it, since it doesn't take long and I have no files on my HD?

Thanks

---

### Post by papibe on 2011-10-11
Hi carlosbgois. Welcome to the forums! 

Could you post the result of these commands?
```
$ sudo lshw -C network

$ lspci -nn | grep -i eth

$ lsmod

$ ifconfig

$ route -n

$ nslookup ubuntu.com

$ dig ubuntu.com
```
Please paste your result using the # tagss (available when replying).

Regards.

---

### Post by carlosbgois on 2011-10-11
Thanks for your help, here's what you asked:

**sudo lshw -C network:**
```

  *-network               
       description: Ethernet interface
       product: 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:06:08.0
       logical name: eth0
       version: 01
       serial: 00:13:20:20:d1:e0
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A latency=32 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:20 memory:f9b00000-f9b00fff ioport:b400(size=64)
```


**lspci -nn | grep -i eth:**
```
06:08.0 Ethernet controller [0200]: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller [8086:1064] (rev 01)
```


**lsmod:**
```
Module                  Size  Used by
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
nouveau               621970  2 
binfmt_misc            13213  1 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   180037  4 nouveau,ttm,drm_kms_helper
joydev                 17322  0 
psmouse                73312  0 
serio_raw              12990  0 
snd                    55295  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
parport_pc             32111  1 
i2c_algo_bit           13184  1 nouveau
video                  18951  1 nouveau
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
e100                   40108  0 
floppy                 60032  0 
```


**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:13:20:20:d1:e0  
          inet6 addr: fe80::213:20ff:fe20:d1e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1440 (1.4 KB)  TX bytes:6236 (6.2 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16908 (16.9 KB)  TX bytes:16908 (16.9 KB)
```


**route -n**
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
```


**nslookup ubuntu.com:**
```
;; connection timed out; no servers could be reached
```


**dig ubuntu.com:**
```
; <<>> DiG 9.7.3 <<>> ubuntu.com
;; global options: +cmd
;; connection timed out; no servers could be reached
```

---

### Post by newbie-user on 2011-10-11
From the results of ifconfig, it looks like your network card isn't picking up an IP address.  Check to see if the network cable is seated in the socket correctly.

Also, check the contents of /etc/network/interfaces.  Check if the following lines are uncommented:

   auto eth0
   iface eth0 inet dhcp

---

### Post by dineshs on 2011-10-11
Please post the result of```
sudo dhclient eth0
``` then again```
ifconfig
```

---

### Post by papibe on 2011-10-11
> Hey newbie-user & dineshs,

I think that is because he doesn't have a router, but just a modem. He's using a ppp conection to the internet. Check the details of the ppp0 connection on ifconfig.

I believe his connection has to be configured more like the guidelines found [here]("https://help.ubuntu.com/community/ADSLPPPoE"), than a regular DHCP connection (behind a router).

Regards.
Please ignore this.

---

### Post by carlosbgois on 2011-10-11
**newbie-user**, in my interfaces file there only
```
auto lo
iface lo inet loopback
```
seems there's something wrong in there... Thanks for your help.

**dineshs**, the result of the new ifconfig was:
```
eth0      Link encap:Ethernet  HWaddr 00:13:20:20:d1:e0  
          inet6 addr: fe80::213:20ff:fe20:d1e0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7686 (7.6 KB)  TX bytes:20422 (20.4 KB)

eth0:avahi Link encap: Ethernet HWaddr 00:13:20:20:d1:e0
          inet addr:169.254.9.88 Bcast:169.254.255.255 Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9360 (9.3 KB)  TX bytes:9360 (9.3 KB)
```

Thanks

---

### Post by newbie-user on 2011-10-11
> **papibe said:**
> Hey newbie-user & dineshs,

I think that is because he doesn't have a router, but just a modem. He's using a ppp conection to the internet. Check the details of the ppp0 connection on ifconfig.

I believe his connection has to be configured more like the guidelines found [here]("https://help.ubuntu.com/community/ADSLPPPoE"), than a regular DHCP connection (behind a router).

Regards.

Papibe, I didn't see any ppp0 connection listed anywhere.  Maybe I missed it?

---

### Post by papibe on 2011-10-11
> **papibe said:**
> Hey newbie-user & dineshs,

I think that is because he doesn't have a router, but just a modem. He's using a ppp conection to the internet. Check the details of the ppp0 connection on ifconfig.

I believe his connection has to be configured more like the guidelines found [here]("https://help.ubuntu.com/community/ADSLPPPoE"), than a regular DHCP connection (behind a router).

Regards.

My mistake... too many threads open. :confused:

---

### Post by newbie-user on 2011-10-11
carlosbgois, try adding the following lines to /etc/networking/interfaces:

auto eth0
iface eth0 inet dhcp

then restart the computer.

---

### Post by carlosbgois on 2011-10-12
Didn't work either... Maybe my LAN card isn't working?

---

### Post by newbie-user on 2011-10-12
Well, it might not be working.  Do you have another one to swap into your system?

---

