---
title: "Internet works on Windows, but not Ubuntu..."
date: 2009-04-06
forum: Networking &amp; Wireless
---

### Post by tdashroy on 2009-04-06
Okay so internet is working on Windows, but not Ubuntu, on the same machine. Windows is version XP and Ubuntu is version 8.10.

So this is basically what happened: I used my computer on Friday, before I left to go home, internet was working fine on both ubuntu and windows. Went home. Then came back today, turned on my computer, and the internet wasn't working on ubuntu, but was on windows. Restarted my computer about a million times, trying different cables and whatnot, nothing worked. Umm...I don't really know what kind of output is needed so please tell me if anything is needed. By the way this is only wired internet, I don't know about wireless as there is none to be obtained and it would be hard to move my desktop to somewhere where there is some. Thanks, and like I said, tell me if there is anything I need to give to make it easier!


okay so I read somewhere that this might be useful output

lspci:
```
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub
00:01.0 PCI bridge: Intel Corporation 82945G/GZ/P/PL PCI Express Root Port
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.4 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 5 (rev 01)
00:1c.5 PCI bridge: Intel Corporation 82801GR/GH/GHM (ICH7 Family) PCI Express Port 6 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GH (ICH7DH) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GR/GH (ICH7 Family) SATA AHCI Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV41.1 [GeForce 6800] (rev a2)
04:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller (rev 01)
```

lsmod:
```
Module                  Size  Used by
nls_iso8859_1          12032  1 
nls_cp437              13696  1 
vfat                   18816  1 
fat                    57376  1 vfat
af_packet              25728  2 
binfmt_misc            16904  1 
sco                    18308  2 
rfcomm                 44432  0 
bridge                 56980  0 
stp                    10628  1 bridge
bnep                   20480  2 
l2cap                  30464  6 rfcomm,bnep
bluetooth              61924  6 sco,rfcomm,bnep,l2cap
ppdev                  15620  0 
ipv6                  263972  16 
cpufreq_conservative    14600  0 
cpufreq_ondemand       14988  0 
cpufreq_powersave       9856  0 
cpufreq_userspace      11396  0 
cpufreq_stats          13188  0 
freq_table             12672  2 cpufreq_ondemand,cpufreq_stats
wmi                    14504  0 
pci_slot               12680  0 
container              11520  0 
sbs                    19464  0 
sbshc                  13440  1 sbs
video                  25232  0 
output                 11008  1 video
battery                18436  0 
iptable_filter         10752  0 
ip_tables              19600  1 iptable_filter
x_tables               22916  1 ip_tables
ac                     12292  0 
parport_pc             39204  0 
lp                     17156  0 
parport                42604  3 ppdev,parport_pc,lp
dcdbas                 15008  0 
snd_hda_intel         384176  3 
psmouse                45200  0 
serio_raw              13444  0 
evdev                  17696  6 
snd_pcm_oss            46848  0 
snd_mixer_oss          22784  1 snd_pcm_oss
snd_pcm                83204  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          10884  0 
pcspkr                 10624  0 
snd_seq_oss            38528  0 
snd_seq_midi           14336  0 
nvidia               6909268  36 
snd_rawmidi            29824  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
i2c_core               31892  1 nvidia
snd_seq                57776  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29960  2 snd_pcm,snd_seq
snd_seq_device         15116  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
button                 14224  0 
intel_agp              33724  0 
agpgart                42184  2 nvidia,intel_agp
snd                    63268  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15328  1 snd
shpchp                 38036  0 
pci_hotplug            34976  1 shpchp
snd_page_alloc         16136  2 snd_hda_intel,snd_pcm
ext3                  133256  1 
jbd                    55828  1 ext3
mbcache                16004  1 ext3
sr_mod                 22212  0 
cdrom                  43168  1 sr_mod
sd_mod                 42392  5 
crc_t10dif              9984  1 sd_mod
ata_piix               24580  0 
ata_generic            12932  0 
usbhid                 35840  0 
hid                    50560  1 usbhid
sg                     39732  0 
usb_storage            82752  1 
libusual               30356  1 usb_storage
pata_acpi              12160  0 
ahci                   37132  2 
libata                178208  4 ata_piix,ata_generic,pata_acpi,ahci
scsi_mod              155212  5 sr_mod,sd_mod,sg,usb_storage,libata
dock                   16656  1 libata
ehci_hcd               43788  0 
e1000e                112808  0 
uhci_hcd               30736  0 
usbcore               149360  6 usbhid,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                23708  0 
processor              42156  1 thermal
fan                    12548  0 
fbcon                  47648  0 
tileblit               10880  1 fbcon
font                   16512  1 fbcon
bitblit                13824  1 fbcon
softcursor              9984  1 bitblit
fuse                   60828  3 

```

---

### Post by superprash2003 on 2009-04-06
post output of **ifconfig** from the terminal

---

### Post by tdashroy on 2009-04-06
Thanks for the response! Here is the ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:7b:25:59  
          inet addr:129.116.15.161  Bcast:129.116.15.255  Mask:255.255.255.128
          inet6 addr: fe80::212:3fff:fe7b:2559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:194857 (194.8 KB)  TX bytes:4734 (4.7 KB)
          Memory:ecee0000-ecf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)


```

---

### Post by Iowan on 2009-04-06
Is that a static or DHCP address? (Does machine have same address under Windows?)

---

### Post by tdashroy on 2009-04-06
umm...I'm not really sure.  Here is ipconfig from windows:

```
Microsoft Windows XP [Version 5.1.2600]
(C) Copyright 1985-2001 Microsoft Corp.

C:\Documents and Settings\Troy>ipconfig

Windows IP Configuration


Ethernet adapter Local Area Connection:

        Connection-specific DNS Suffix  . : dorm.utexas.edu
        IP Address. . . . . . . . . . . . : 129.116.15.51
        Subnet Mask . . . . . . . . . . . : 255.255.255.128
        Default Gateway . . . . . . . . . : 129.116.15.1

C:\Documents and Settings\Troy>
```

The IP Address looks different to me.

---

### Post by Iowan on 2009-04-07
IP address looks different to me, too... meaning it's *probably* DHCP.  Might be helpful to check routing table (route?) to see if Ubuntu gets the right gateway.

---

### Post by superprash2003 on 2009-04-07
also post output of **ping 208.67.222.222**

---

### Post by tdashroy on 2009-04-07
EDIT: It is now not working...see post below

Okay so...I logged onto ubuntu to get the output asked for, and the internet was working all of a sudden...

But, I would like to try and pinpoint what happened if possible, because this is not the first time this has happened.

Here is the requested output

route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.116.15.0    *               255.255.255.128 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         resnet-15-1.dor 0.0.0.0         UG    0      0        0 eth0

```

ping 208.67.222.222
```
ping 208.67.222.222
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.
^C
--- 208.67.222.222 ping statistics ---
146 packets transmitted, 0 received, 100% packet loss, time 145069ms

```

ping [www.google.com](www.google.com)
```
ping www.google.com
PING www.l.google.com (74.125.93.147) 56(84) bytes of data.
^C
--- www.l.google.com ping statistics ---
46 packets transmitted, 0 received, 100% packet loss, time 45045ms

```

Why is it that I can go to website but I cannot ping them??

---

### Post by tdashroy on 2009-04-07
Okay! So all of a sudden it is not working again...

Here is the output when it is not working:

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:7b:25:59  
          inet addr:129.116.15.25  Bcast:129.116.15.127  Mask:255.255.255.128
          inet6 addr: fec0::9:212:3fff:fe7b:2559/64 Scope:Site
          inet6 addr: 2002:8174:e37:9:212:3fff:fe7b:2559/64 Scope:Global
          inet6 addr: fe80::212:3fff:fe7b:2559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2194260 (2.1 MB)  TX bytes:27736 (27.7 KB)
          Memory:ecee0000-ecf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)
```


route:
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
129.116.15.0    *               255.255.255.128 U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         129.116.15.1    0.0.0.0         UG    0      0        0 eth0
```


ping:
```
PING 208.67.222.222 (208.67.222.222) 56(84) bytes of data.

--- 208.67.222.222 ping statistics ---
15 packets transmitted, 0 received, 100% packet loss, time 14036ms
```

---

### Post by superprash2003 on 2009-04-08
do you have firestarter or anything similar running?? post output of **sudo iptables -L**

---

### Post by tdashroy on 2009-04-08
I don't even know what firestarter is, so my guess is it's not running.

sudo iptables -L
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```

---

### Post by superprash2003 on 2009-04-09
well.. your firewall isnt blocking anything.. try disabling ipv6 [http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html](http://www.prash-babu.com/2009/01/how-to-disable-ipv6-in-linux-ubuntu-to.html) .. also restart networking by typing sudo /etc/init.d/networking restart..

---

### Post by tdashroy on 2009-04-09
Well it randomly started to work again...but I will definately try these things if it stops again. Thanks a bunch!

---

### Post by tdashroy on 2009-04-10
Okay so it stopped working again...and I tried those commands and they did not work.

When I did:

```
sudo /etc/init.d/networking restart
```

It gave me the following error message:

```
Ignoring uknown interface eth0=eth0
```

Any other ideas?

---

### Post by pbpersson on 2009-04-10
how does your ifconfig appear now?

---

### Post by Kulgan on 2009-04-10
Just butting in here with my 0.5¢. 

Had some problems like this before, though I only think what I did works with a generic driver - if you had to do any magic to get networking working in the first place, it will probably do less good than evil. Also probably will be bad in a non-dhcp context.

Back up /etc/network/interfaces:
```

cp /etc/network/interfaces /etc/network/interfaces_bk

```

Now remove from interfaces all lines but the two referring to the loopback interface. Then reboot. 

There seems to be some conflict between this file and nm-applet. Perhaps this has an impact on it. Who knows? >_>

---

### Post by tdashroy on 2009-04-10
pbpersson: Wouldn't you know it, the internet, again, started to work. I'll post the ifconfig anyway.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:12:3f:7b:25:59  
          inet addr:129.116.15.51  Bcast:129.116.15.127  Mask:255.255.255.128
          inet6 addr: fe80::212:3fff:fe7b:2559/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2729801 (2.7 MB)  TX bytes:501804 (501.8 KB)
          Memory:ecee0000-ecf00000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

```

Kulgan: if it happens again, which I'm assuming it will, I will try this.

Thank you both for the response!

---

