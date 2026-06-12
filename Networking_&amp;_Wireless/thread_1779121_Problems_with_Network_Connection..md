---
title: "Problems with Network Connection."
date: 2011-06-10
forum: Networking &amp; Wireless
---

### Post by OldBoy44 on 2011-06-10
Hi all,

I have had problems connecting to the internet via Firefox which with tweaking now appear to be resolved. However I believe I still may have a network problem - when I enter the command sudo ifdown eth0 the result is "interface not configured". I have done a little searching and came across the following thread which may be helpful. [http://ubuntuforums.org/showthread.php?t=1778594](http://ubuntuforums.org/showthread.php?t=1778594)

The following are my results -
```

ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:6f:65:d6:d1:a4  
          inet addr:10.1.1.2  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1e6f:65ff:fed6:d1a4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8774 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7623 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9872836 (9.8 MB)  TX bytes:1057354 (1.0 MB)
          Interrupt:41 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1920 (1.9 KB)  TX bytes:1920 (1.9 KB)

``````

lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 06
       serial: 1c:6f:65:d6:d1:a4
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=10.1.1.2 latency=0 multicast=yes port=MII speed=100Mbit/s
       resources: irq:41 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.

``````

lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 7 (rev b5)
00:1c.7 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 8 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation H67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: ATI Technologies Inc Juniper [Radeon HD 5700 Series]
01:00.1 Audio device: ATI Technologies Inc Juniper HDMI Audio [Radeon HD 5700 Series]
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)

``````

lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_hdmi     28103  1 
snd_hda_codec_realtek   336693  1 
usblp                  18233  0 
snd_hda_intel          33211  2 
snd_hda_codec         103804  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
radeon                982197  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
serio_raw              13166  0 
joydev                 17606  0 
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    76664  1 radeon
snd                    67382  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         42136  1 radeon
xhci_hcd               77643  0 
drm                   227495  4 radeon,ttm,drm_kms_helper
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13400  1 radeon
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
usbhid                 46956  0 
hid                    91020  1 usbhid
ahci                   25951  4 
libahci                26642  1 ahci
r8169                  48022  0 

```Is this information helpful in establishing if I have a problem?

Thank you -

---

### Post by dandnsmith on 2011-06-10
have a look at the man page for ifdown, and then look at the content of /etc/network/interfaces.
If your setup is like mine, there won't be an entry for eth0 - which would account for that error message.

---

### Post by OldBoy44 on 2011-06-10
Hi and thanks Derek,

I am a complete newbie - what did you mean by "man page for ifdown"? 

Cheers, :)

---

### Post by OldBoy44 on 2011-06-10
I am looking at the manual page now - I hope I can get it sorted out,

---

### Post by OldBoy44 on 2011-06-10
sudo ifup eth0 returns message - interface already configured.

I assume then that all is well - any comments would be appreciated -

Although I have been accessing the internet, I became very confused when I pinged certain sites suggested by Ubuntu documentation and obtained apparently very poor results.

Thanks again Derek. :)

---

### Post by dandnsmith on 2011-06-10
> **aussiebean said:**
> sudo ifup eth0 returns message - interface already configured.

I assume then that all is well - any comments would be appreciated -

Although I have been accessing the internet, I became very confused when I pinged certain sites suggested by Ubuntu documentation and obtained apparently very poor results.

Thanks again Derek. :)

It looks as though all is well - I'd never use ifup and ifdown for wired connections, only wireless, myself.

Not sure when you talk about 'pinging' sites - do you mean literally, the results from using the ping command, or are you talking about trying to access them via browser? Sometimes the documentation gets out of date.

---

