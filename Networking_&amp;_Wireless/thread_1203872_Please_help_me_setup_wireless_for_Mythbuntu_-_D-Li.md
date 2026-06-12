---
title: "Please help me setup wireless for Mythbuntu - D-Link DWA-130"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by the_pod on 2009-07-03
I've spent the better part of 7 hours reading everything written on setting up wireless in Ubuntu, following every tutorial and all to no avail. Even spoke to a lad named "Steve" in India when I called the D-Link toll free support but didn't get much help there either.

At this point, I really don't know what is going wrong.  In essence, I find 2 different paths to take when setting up this wireless adapter.

1)  Via NDIS (example walk-thru here) [http://www.linuxforums.org/forum/ubuntu-help/141152-missing-network-configuration-tool.html](http://www.linuxforums.org/forum/ubuntu-help/141152-missing-network-configuration-tool.html)

and 

2)  Using the linux drivers at the D-Link website (I can't get them to work at all but I've seen where others have)

Would someone care to help me? This is my first time with wireless in Ubuntu and my first Myth box.  I thought getting Myth up and running would be the difficult part but nope - it's the wireless.

For whoever wants to walk this journey with me, let me know what you need from me information wise and I'll move down that path.

TIA.

---

### Post by bkratz on 2009-07-04
I don't know anything about Mythbuntu (although I would like to learn and have downloaded it) but I do use the DWA130 in both 8.10 and 9.04.  First you need to determine if you version a, b or c of the adapter.  If it is an a or b you will have to use the windows drivers (on the website or your installation disk) and ndiskgtk front end. Setup is pretty straightforward after that.

---

### Post by the_pod on 2009-07-04
Ok.  Have had some sleep so I'm thinking a bit more clearly and am trying to provide some further info.  FWIW, trying to install with nsidwrapper support here.

**_System Details:_**

[LIST]
[*]  Mobo:  GIGABYTE GA-MA780G-UD3H AM2+/AM2 AMD 780G HDMI ATX AMD Motherboard
[*]  Processor:  AMD Athlon 64 X2 7750 Kuma 2.7GHz 2 x 512KB L2 Cache 2MB L3 Cache Socket AM2+ 95W Dual-Core Processor
[*] OS:  Mythbuntu 9.04 64
[*] Kernel:  2.6.28-13-Generic
[*] Wireless:  D-Link DWA-130 rev C USB
[/LIST]


*Below applies to attempting to get ndiswrapper working.  *


Below is **lsusb** -- so you can see that the card is recognized ("D-Link Corp. [hex]" with ID of 2001-3301.
```

$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 2001:3301 D-Link Corp. [hex] 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 004: ID 046d:c501 Logitech, Inc. Cordless Mouse Receiver
Bus 003 Device 003: ID 147a:e017 Formosa Industrial Computing, Inc. 
Bus 003 Device 002: ID 046d:c315 Logitech, Inc. Classic New Touch Keyboard
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

**ifconfig** below.  No idea what this tells me but I suppose I should be able to see a wireless network? No dice. 
```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:24:1d:2e:32:3e  
          inet addr:192.168.222.106  Bcast:192.168.222.255  Mask:255.255.255.0
          inet6 addr: fe80::224:1dff:fe2e:323e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4221 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2715 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2390635 (2.3 MB)  TX bytes:656287 (656.2 KB)
          Interrupt:253 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:151 errors:0 dropped:0 overruns:0 frame:0
          TX packets:151 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10901 (10.9 KB)  TX bytes:10901 (10.9 KB)

```

**iwconfig** below.  
```

$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

```

**lsmod** below.  Not sure what we're looking for here so I dumped the entire output.
```

$ lsmod
Module                  Size  Used by
radeon                357792  2 
drm                   123232  3 radeon
bridge                 63904  0 
stp                    11140  1 bridge
bnep                   22912  2 
input_polldev          12688  0 
video                  29204  0 
output                 11648  1 video
nfsd                  285344  13 
auth_rpcgss            52512  1 nfsd
exportfs               13440  1 nfsd
nfs                   304464  0 
lockd                  83796  2 nfsd,nfs
nfs_acl                11776  2 nfsd,nfs
sunrpc                227304  15 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
xfs                   568464  1 
lp                     19588  0 
mxl5005s               50436  1 
s5h1409                18564  1 
tuner_simple           24084  1 
tuner_types            26240  1 tuner_simple
cs5345                 11868  0 
tuner                  36036  0 
cx18                  129984  1 
dvb_core              106924  1 cx18
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
compat_ioctl32         18304  1 cx18
snd_hda_intel         557492  0 
snd_seq_midi           15744  0 
videodev               45184  3 tuner,cx18,compat_ioctl32
v4l1_compat            23940  1 videodev
snd_rawmidi            33920  1 snd_seq_midi
i2c_algo_bit           15364  1 cx18
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
snd_seq_midi_event     16512  2 snd_seq_oss,snd_seq_midi
cx2341x                22148  1 cx18
snd_pcm                99336  2 snd_hda_intel,snd_pcm_oss
snd_seq                66272  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
v4l2_common            23296  4 cs5345,tuner,cx18,cx2341x
ppdev                  16904  0 
snd_timer              34064  2 snd_pcm,snd_seq
tveeprom               23428  1 cx18
usbhid                 47040  0 
parport_pc             45096  1 
parport                49584  3 lp,ppdev,parport_pc
i2c_piix4              20112  0 
pcspkr                 11136  0 
snd_seq_device         16276  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 44572  0 
lirc_mceusb2           21636  0 
snd                    78792  9 snd_seq_oss,snd_hda_intel,snd_rawmidi,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device
lirc_dev               22088  1 lirc_mceusb2
soundcore              16800  1 snd
snd_page_alloc         18704  2 snd_hda_intel,snd_pcm
ndiswrapper           250624  0 
ohci1394               42036  0 
ieee1394              108288  1 ohci1394
r8169                  46596  0 
mii                    14464  1 r8169
floppy                 75816  0 
fbcon                  49792  0 
tileblit               11264  1 fbcon
font                   17024  1 fbcon
bitblit                14464  1 fbcon
softcursor             10368  1 bitblit

```

Select part of **dmesg** below.  While it looks like I have a driver associated with the stick it's not a 64b driver so it doesn't seem to work.  I've tried installing the 64b drivers (both the Win2kXP version and the Vista version but both completely kill the system (will not full reboot until hardware unplugged from system completely).
```

$ dmesg
...
[    6.039322] ndiswrapper (check_nt_hdr:150): kernel is 64-bit, but Windows driver is not 64-bit;bad magic: 010B
[    6.039326] ndiswrapper (load_sys_files:206): couldn't prepare driver 'net8192u'
[    6.050427] ndiswrapper (load_wrap_driver:108): couldn't load driver net8192u; check system log for messages from 'loadndisdriver'
...
```

So here's what I came up with from the "messages" file in /var/log/:
```

Jul  3 22:02:11 purdie-mythtv loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver net8192u 
Jul  3 22:02:11 purdie-mythtv kernel: [ 3384.551059] usbcore: registered new interface driver ndiswrapper
Jul  3 22:03:41 purdie-mythtv kernel: [ 3474.556898] [drm] Resetting GPU
Jul  3 22:03:41 purdie-mythtv kernel: [ 3474.623740] mtrr: MTRR 4 not used
Jul  3 22:03:53 purdie-mythtv kernel: [ 3486.455479] nfsd: last server has exited, flushing export cache
Jul  3 22:03:54 purdie-mythtv exiting on signal 15
Jul  3 22:04:36 purdie-mythtv syslogd 1.5.0#5ubuntu3: restart.
Jul  3 22:04:37 purdie-mythtv kernel: Inspecting /boot/System.map-2.6.28-13-generic
Jul  3 22:04:37 purdie-mythtv kernel: Cannot find map file.
Jul  3 22:04:37 purdie-mythtv kernel: Loaded 64186 symbols from 63 modules.

```

And **lshw**...  I have no idea if it should say "DISABLED" down there or not.
```

$ sudo lshw -C network
[sudo] password for purdie: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:24:1d:2e:32:3e
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.222.106 latency=0 link=yes module=r8169 multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: ca:22:5b:1a:24:fe
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
```

for **iwlist**:
```

$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

```

...and...```

$ iwlist scan wlan0
iwlist: unknown command `wlan0' (check 'iwlist --help').

```

Ubuntu version (note that I'm installed from a Mythbuntu 9.04 64b):
```

$ lsb_release -d
Description:	Ubuntu 9.04

```

kernel:
```

$ uname -mr
2.6.28-13-generic x86_64

```

And finally restarting the network:
```

$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          WARNING: ifup -a is disabled in favour of NetworkManager.
  Set ifupdown:managed=false in /etc/NetworkManager/nm-system-settings.conf.

```
I have no idea how to access NetworkManager and have actually  installed Wicd thinking this might help somewhere but it didn't.

Hope that's enough to get started. I'm guessing the issue is related to the 64b architecture and a 32b driver.  I'd prefer to stick w/ 64b if possible but I'm not above installing a 32b system if that means I get a week of my life back. :)

Thanks.

---

### Post by the_pod on 2009-07-04
> **bkratz said:**
> I don't know anything about Mythbuntu (although I would like to learn and have downloaded it) but I do use the DWA130 in both 8.10 and 9.04.  First you need to determine if you version a, b or c of the adapter.  If it is an a or b you will have to use the windows drivers (on the website or your installation disk) and ndiskgtk front end. Setup is pretty straightforward after that.

Thanks for the reply.  Just spent an hour putting together a list of all types of info from the system and my issue seems to be related (I'm guessing here) to trying to runa 32b driver on a 64b system.

Fwiw, my USB stick is vC (box says "Ver. C1", so I'm assuming that's what it means).

-S

---

### Post by bkratz on 2009-07-04
Try looking at this link, the gentlemen figured out how to do what you are trying to do with the same version device.




[http://ubuntuforums.org/showthread.php?t=1162462&highlight=dwa-130](http://ubuntuforums.org/showthread.php?t=1162462&highlight=dwa-130)

Good luck!

---

### Post by the_pod on 2009-07-04
> **bkratz said:**
> Try looking at this link, the gentlemen figured out how to do what you are trying to do with the same version device.




[http://ubuntuforums.org/showthread.php?t=1162462&highlight=dwa-130](http://ubuntuforums.org/showthread.php?t=1162462&highlight=dwa-130)

Good luck!

Thanks for looking. I did try that yesterday late but may have better luck today with (a) less beer in me and (b) a better working brain (not so tired).

As an update, I still can't figure out the driver for 64b.

HOWEVER I have successfully installed the 32b version of mythbuntu and can now connect to the LAN wirelessly using the wrapper w/ the Windows driver.  I did have to install WICD because (guess here) either NetworkManager blows or it is really stripped down in the Mythbuntu distro... not sure what the deal is there.

Still, I'm "in" and can now officially move my Mythbox where it needs to be.  I'll play around w/ the wireless piece from my normal computer which runs an Ubuntu 9.04 64b as well. If I can get it installed there then I can start over on the mythbox, but right now it's just way too cluttered w/ computers sitting about in partial states of disarray.

---

