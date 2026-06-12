---
title: "no eth connection with W3650(emachines)"
date: 2012-04-11
forum: Networking &amp; Wireless
---

### Post by davesbrain on 2012-04-11
Hello, have an old Emachines W3650 I was trying. 10.04 LTS installed fine, however, it won't connect to net. Mobo does have on-board LAN and it is 'enabled' in Bios. No wired connection.

---

### Post by praseodym on 2012-04-11
Hi,

please show

> lspci -nnk | grep -iA2 net
lsmod
ifconfig -a
cat /etc/network/interfaces
uname -a
How do you want to connect? Router/modem?

---

### Post by davesbrain on 2012-04-12
Hi,  I don't think it's seeing the onboard LAN.  It's just a wired connection to broadband modem.  But, here's the info you requested.

-nnk | grep -iA2 net:
> Did nothing

lsmod:
```
davejr@davejr-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  2 
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  3 i915,drm_kms_helper
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
soundcore               6620  1 snd
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
```

ifconfig -a:
```
davejr@davejr-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)
```

cat /etc/network/interfaces:
```
auto lo
iface lo inet loopback
```

uname -a:
```
Linux davejr-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
```

---

### Post by praseodym on 2012-04-12
This
> lspci -nnk | grep -iA2 net
is one line!

---

### Post by davesbrain on 2012-04-12
sorry about that.  mis-copied in reply.  That entire line didn't do anything.  Here is all of output:

```
davejr@davejr-desktop:~$ lspci -nnk | grep -iA2 net
davejr@davejr-desktop:~$ lspci -nnk | grep -iA2 net
davejr@davejr-desktop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8901  1 
fat                    47767  1 vfat
usb_storage            39425  1 
binfmt_misc             6587  1 
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  2 
drm_kms_helper         29297  1 i915
ppdev                   5259  0 
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   162471  3 i915,drm_kms_helper
psmouse                63245  0 
serio_raw               3978  0 
parport_pc             25962  1 
soundcore               6620  1 snd
intel_agp              24177  2 i915
agpgart                31724  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  3 ppdev,parport_pc,lp
davejr@davejr-desktop:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5600 (5.6 KB)  TX bytes:5600 (5.6 KB)

davejr@davejr-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

davejr@davejr-desktop:~$ uname -a
Linux davejr-desktop 2.6.32-21-generic #32-Ubuntu SMP Fri Apr 16 08:10:02 UTC 2010 i686 GNU/Linux
davejr@davejr-desktop:~$ 

```

---

### Post by praseodym on 2012-04-13
Strange, no card listed. Check the BIOS settings (maybe resetting it) and show

> lsusb
cat /etc/udev/rules.d/70-persistent-net.rules

---

### Post by davesbrain on 2012-04-13
'Onboard' LAN is enabled in Bios.  Could it be a compatibility issue?  I've tried other distro live cd's, same thing, no eth.  Pretty sure it's Realtek RTL8100c.

---

### Post by praseodym on 2012-04-13
Ok, tha complete output of

> lspci
without filter, please.

---

### Post by davesbrain on 2012-04-14
```
davejr@davejr-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation N10/ICH7 Family SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
davejr@davejr-desktop:~$ 

```

---

### Post by praseodym on 2012-04-15
There is no card shown. Sure there is one inside?

---

### Post by davesbrain on 2012-04-15
Yes, of course. It's the onboard LAN.  It is also 'enabled' in Bios.

---

