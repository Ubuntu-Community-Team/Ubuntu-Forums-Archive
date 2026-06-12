---
title: "ACPI=off Intel Pro Wireless 3945 problem"
date: 2009-11-05
forum: Networking &amp; Wireless
---

### Post by Zionteam on 2009-11-05
Hello dear friends:

I am having this problem using Karmic Koala...
I'm trying to install it "inside windows"...

After the computer starts i have to select the "ACPI workarounds" option in the install boot options, if i want anything to happen...

When it's finally installed, it recognizes the wireless card, but it says that it's disabled, and I can't enable it.

can anyone help me??

pleasE!

---

### Post by fomaa on 2009-11-05
I have the same problem.

---

### Post by Zionteam on 2009-11-07
anyone??

PLEASE HELP! :D

---

### Post by fomaa on 2009-11-07
**lspci | grep Wireless**
```
01:04.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection (rev 05)
```

**ifconfig**
```
eth0      Link encap:Ethernet  HWaddr 00:11:d8:eb:5b:fe  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:feeb:5bfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9250 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11903 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6955725 (6.9 MB)  TX bytes:2979891 (2.9 MB)
          Interrupt:5 Base address:0xc800 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:16:a3:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:5 Base address:0xc000 Memory:fe8fe000-fe8fefff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:8174 (8.1 KB)  TX bytes:8174 (8.1 KB)
```

**iwconfig eth1**
```

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

**lsmod**
```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
pcmcia                 36808  0 
ipw2200               140292  0 
libipw                 43148  1 ipw2200
yenta_socket           24200  2 
rsrc_nonstatic         11644  1 yenta_socket
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
lib80211                6432  2 ipw2200,libipw
iptable_filter          3100  0 
joydev                 10272  0 
snd_intel8x0           30168  0 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
ip_tables              11692  1 iptable_filter
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
lp                      8964  0 
snd_seq_midi            6432  0 
shpchp                 32272  0 
snd_rawmidi            22208  1 snd_seq_midi
parport                35340  2 ppdev,lp
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm
x_tables               16544  1 ip_tables
psmouse                56180  0 
serio_raw               5280  0 
dm_raid45              84228  0 
xor                    15620  1 dm_raid45
usbhid                 38208  0 
ohci1394               29900  0 
ieee1394               86596  1 ohci1394
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
output                  2780  0 
intel_agp              27484  1 
agpgart                34988  2 intel_agp
```

**sudo lshw -C network**
```
  *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:11:d8:eb:5b:fe
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.2 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100MB/s
       resources: irq:5 ioport:c800(size=256) memory:fe8ff400-fe8ff4ff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:01:04.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:16:a3:4a
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) latency=64 link=no maxlatency=24 mingnt=3 multicast=yes wireless=radio off
       resources: irq:5 memory:fe8fe000-fe8fefff
```

**iwlist scan**
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      No scan results
```

**lsb_release -d**
```
Description:	Ubuntu 9.10
```

**uname -mr**
```
2.6.31-14-generic i686
```

Can be solved?

---

### Post by tehardis on 2009-11-08
I am fairly new here, but according to the instructions from intel on installing ipw2200, the radio needs to be turned 'on'. Its looks like under iwconfig it is turned off. I may be missing something. Like I say. I'm quite green.

---

### Post by fomaa on 2009-11-08
acpi=off is not writing computer freezes. But the wireless light is lit.
[[IMG]http://img689.imageshack.us/img689/3331/62369266.th.png[/IMG]](http://img689.imageshack.us/i/62369266.png/)


acpi=off writing the computer does not freeze. But wireless light is not lit. Fn + F2 (wireless open the hotkeys) not working.
[[IMG]http://img266.imageshack.us/img266/2859/offs.th.png[/IMG]](http://img266.imageshack.us/i/offs.png/)

---

### Post by Zionteam on 2009-11-09
I have the same problem...
when i boot with acpi=off my wireless card doesn't work...

---

### Post by fomaa on 2009-11-09
kernel 2.6.28.16 installed. Problem is solved :D
I installed the following packages.

[http://packages.ubuntu.com/jaunty/linux-image-2.6.28-16-generic](http://packages.ubuntu.com/jaunty/linux-image-2.6.28-16-generic)
[http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16)
[http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16-generic](http://packages.ubuntu.com/jaunty/linux-headers-2.6.28-16-generic)

Restarted the computer. Open the computer with 2.6.28-16 kernel release. Do not write acpi=off.

---

### Post by Zionteam on 2009-11-11
you are right fomaa, it does start, but i have no audio nor 3d acceleration with this kernel....

I think I'll stick with jaunty...

---

