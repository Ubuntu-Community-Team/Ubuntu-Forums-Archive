---
title: "MSI Wind L2100 RaLink Wireless a/b/g/n &quot;unclaimed&quot;"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by anthonydv07 on 2010-01-24
I've searched on-line and through these forums and I am still not able to find a solution to my problem. To start off, I do not know if my wireless card is turned on or off. I press Fn+f8 key and the LED turns on but Ubuntu does not detect the wireless networks. I am able to connect using the Ethernet port. I am a new user, please help.

ps: I have already updated the Ubuntu software using the commands:

>  sudo apt-get update and sudo apt-get upgradeMy Product:
> 
 RaLink RT3090 Wireless 802.11n 1T/1R PCIe
Ra-link makes a Linux driver for this card but from what I understand I should not install the driver unless I absolutely have to (do to the fact that it does not automatically update through the operating system)

here is the link to the driver (btw, I do not know how to install driver on Ubuntu, please help if do need too)
> 
[http://www.ralinktech.com/support.php?s=2](http://www.ralinktech.com/support.php?s=2)
List of commands that should make some sense to experts:

> anthony@ubuntu:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:feaf0000-feafffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 03
       serial: 00:24:21:6c:03:51
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.108 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:e800(size=256) memory:fdfff000-fdffffff(prefetchable) memory:fdff8000-fdffbfff(prefetchable) memory:febe0000-febfffff(prefetchable)
anthony@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

anthony@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

anthony@ubuntu:~$ 
> anthony@ubuntu:~$ sudo /etc/init.d/networking restart
[sudo] password for anthony: 
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface eth0=eth0.
                                                                                                                                                                 [ OK ]
anthony@ubuntu:~$ 
> 
anthony@ubuntu:~$ uname -mr
2.6.31-17-generic i686

> 
anthony@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
joydev                 10240  0 
snd_hda_codec_atihdmi     3356  1 
snd_hda_codec_realtek   203328  1 
snd_seq_dummy           2656  0 
iptable_filter          3100  0 
snd_seq_oss            28576  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
psmouse                56500  0 
serio_raw               5280  0 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
k8temp                  4188  0 
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
i2c_piix4               9932  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_realtek,snd_seq_oss,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
shpchp                 32272  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
r8169                  32064  0 
mii                     5212  1 r8169
radeon                636000  3 
ttm                    36212  1 radeon
drm                   159584  5 radeon,ttm
i2c_algo_bit            5760  1 radeon
video                  19380  0 
output                  2780  1 video
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
anthony@ubuntu:~$ 


---

### Post by anthonydv07 on 2010-01-25
[http://ubuntuforums.org/showthread.php?t=1274886&page=6](http://ubuntuforums.org/showthread.php?t=1274886&page=6)

Follow the instructions provided. I now have a working wireless card on Ubuntu Netbook Remix.

skip step 2. by manually adding the website to your system's Software Sources. Continue on to step 3. and restart!

:popcorn:

---

