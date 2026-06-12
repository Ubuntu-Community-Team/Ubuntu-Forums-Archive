---
title: "help me with ra0 and my wusb54gc"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by AFI420 on 2009-11-22
I followed quite a few procedures to get my adapter working. Today I finally went wired, updated the OS and boom wicd sees my card after reboot and can see the routers in my area but cant connect to mine. so I reinstalled to see if the simple step of blacklisting  rt2800usb would work, it didnt. so now I have wicd installed and no ra0 whcih is what was working before (not connecting tho)


I run a dell 4600

root@ubuntu:~# lsusb
Bus 001 Device 002: ID 1737:0077 Linksys 

root@ubuntu:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

root@ubuntu:~# lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
snd_intel8x0           30168  2 
snd_ac97_codec        101216  1 snd_intel8x0
usblp                  12636  0 
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
iptable_filter          3100  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
ip_tables              11692  1 iptable_filter
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
x_tables               16544  1 ip_tables
snd                    59204  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
psmouse                56180  0 
dell_wmi                2564  0 
shpchp                 32272  0 
ppdev                   6688  0 
lp                      8964  0 
serio_raw               5280  0 
parport_pc             31940  1 
joydev                 10272  0 
parport                35340  3 ppdev,lp,parport_pc
dcdbas                  7292  0 
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
usb_storage            52544  1 
usbhid                 38208  0 
e100                   32452  0 
mii                     5212  1 e100
floppy                 54916  0 
video                  19380  1 i915
output                  2780  1 video
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp

root@ubuntu:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:0c:f1:e5:fe:82
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.104 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:feaff000-feafffff ioport:ddc0(size=64)


root@ubuntu:~# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


root@ubuntu:~# lsb_release -d
Description:    Ubuntu 9.10


root@ubuntu:~# uname -mr
2.6.31-14-generic i686

root@ubuntu:~# sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.
                                                                         [ OK ]

---

### Post by coffeeaddict22 on 2009-11-22
Hi,
On the info you've given, you haven't got a driver for your wireless card installed and/or running- it should be showing up as part of the output of lshw -C network, among other places.

I'm assuming you've just done a new install, although from what you're saying you've replaced network manager with wicd?

Try checking for a driver in System/Administration/Hardware Drivers first.  If there's one there, activate it and see what happens.

Can you post the relevant line from lspci so we can see what card you're running?

---

