---
title: "Compaq Presario C500 wifi problem"
date: 2012-01-04
forum: Networking &amp; Wireless
---

### Post by Solthun on 2012-01-04
Hello I have the same problem and dont seem to find the solution. Could  you help if i post responses to commands? I have the compaq presario  c500 with the new ubuntu 11.10 and in system settings->additional  drivers it tells me that it is installed and in use:'Broadcom sta  wireless driver'
```
sudo lshw -C network
*-network UNCLAIMED     
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:40000000-40003fff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 8
       bus info: pci@0000:08:08.0
       logical name: eth0
       version: 10
       serial: 00:1b:38:37:de:2e
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
        configuration: autonegotiation=on broadcast=yes driver=8139too  driverversion=0.9.28 duplex=full ip=10.196.148.169 latency=32 link=yes  maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:2000(size=256) memory:d0100000-d01000ff
```

```
lspci -nn | grep 0280
06:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)

[CODE]lsmod
```
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
snd_hda_codec_conexant    52418  1 
dm_multipath           22771  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
psmouse                73673  0 
binfmt_misc            17292  1 
serio_raw              12990  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  505159  2 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
snd                     55902  13  snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
wl                   2646601  0 
drm_kms_helper         32889  1 i915
drm                   192194  3 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
lib80211               14570  1 wl
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
video                  18908  1 i915
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
8139too                23283  0 
8139cp                 22636  0 
ahci                   21634  2 
libahci                25727  1 ahci
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash[/CODE]

```
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.
```

```
rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Please help, I am a noob at linux. Thank you in advance!

---

### Post by nothingspecial on 2012-01-04
Question moved to it's own thread.

@Solthun

Rather than posting to the end of an old thread, if you have a question that you can not solve, please make a thread of your own.

Also, please put code tags around the entire terminal output.

Thank you.

---

### Post by Solthun on 2012-01-04
Ok thank you and sorry!
I managed to solve the problem at last!
All that i needed was already there because of all the threads i read.
3 important steps were:
removing the additional driver
these 3 lines i found in a thread...dont know which:
```
sudo apt-update
sudo apt-install b43-fwcutter
sudo apt-install b43-fwcutter firmware-b43-installer
```
Restart

---

### Post by carl4926 on 2012-01-04
Congrats
You just installed the b43 firmware

For others that may read this. You might want to check this reference
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by nbnutnu on 2012-01-15
I have the same problem, I inputed 
sudo apt-get install ndisgtk

according to 
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
but it still doesn't work. 

I am also a noob to the linux OS environment. Could you please tell me how to 
get the wifi working and how to remove the thing I installed (ndisgtk)?

---

### Post by carl4926 on 2012-01-15
You need to post the result of

```
lspci -nnk
```

---

