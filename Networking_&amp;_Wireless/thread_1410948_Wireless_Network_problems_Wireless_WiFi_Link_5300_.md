---
title: "Wireless Network problems: Wireless WiFi Link 5300 and *-network UNCLAIMED"
date: 2010-02-19
forum: Networking &amp; Wireless
---

### Post by arianstolwijk on 2010-02-19
Hi all!

I'm using Ubuntu on my laptop for about a half year now, and using it about two years on an other (secundary) desktop, and i'm really enjoying it.

But my wireless network doesn't work. Before it wasn't a real problem, but i really need it now.

I've already done some research and tried to fix it, but i think I made it only worse.

I found some command that may give some more info about the current state:

```
arian@arian-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:25:b3:c0:21:bf
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000e driverversion=1.0.2-k2 firmware=1.8-3 ip=192.168.2.109 latency=0 multicast=yes
       resources: irq:30 memory:db300000-db31ffff memory:db324000-db324fff ioport:80e0(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: memory:db100000-db101fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes
arian@arian-laptop:~$ 
```

After the *-network for the wireless adapter stands something as UNCLAIMED... maybe this has something to do with it.

Another command I've found is iwconfig:

```
arian@arian-laptop:~$  sudo iwconfig
[sudo] password for arian: 
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

vboxnet0  no wireless extensions.

arian@arian-laptop:~$ 

```



Hope you guys could help me further!

Thank :D

---

### Post by arianstolwijk on 2010-02-22
Any ideas, things I could do to get more info?

---

### Post by chili555 on 2010-02-22
Please open a terminal and do:```
rfkill list
sudo modprobe iwlagn
dmesg | grep iwl
```Thanks.

---

### Post by arianstolwijk on 2010-02-23
Can't check if it works, but this is the output

```
arian@arian-laptop:~$ rfkill list
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
arian@arian-laptop:~$ sudo modprobe iwlagn
[sudo] password for arian: 
WARNING: All config files need .conf: /etc/modprobe.d/blacklist, it will be ignored in a future release.
WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
arian@arian-laptop:~$ dmesg | grep iwl
[ 9220.984851] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27k
[ 9220.984859] iwlagn: Copyright(c) 2003-2009 Intel Corporation
[ 9220.984993] iwlagn 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[ 9220.985008] iwlagn 0000:03:00.0: setting latency timer to 64
[ 9220.985059] iwlagn 0000:03:00.0: Detected Intel Wireless WiFi Link 5300AGN REV=0x24
[ 9221.030195] iwlagn 0000:03:00.0: Tunable channels: 13 802.11bg, 24 802.11a channels
[ 9221.030275] iwlagn 0000:03:00.0: irq 31 for MSI/MSI-X
[ 9221.096605] phy0: Selected rate control algorithm 'iwl-agn-rs'
[ 9221.121388] iwlagn 0000:03:00.0: firmware: requesting iwlwifi-5000-2.ucode
[ 9221.181444] iwlagn 0000:03:00.0: loaded firmware version 8.24.2.12
[ 9221.370431] Registered led device: iwl-phy0::radio
[ 9221.370477] Registered led device: iwl-phy0::assoc
[ 9221.370518] Registered led device: iwl-phy0::RX
[ 9221.370557] Registered led device: iwl-phy0::TX
arian@arian-laptop:~$ 

```

---

### Post by chili555 on 2010-02-23
Looks quite good! Now do you have a wireless interface, wlan0 perhaps?```
iwconfig
```Can you click the Network Manager icon and connect?

---

### Post by arianstolwijk on 2010-02-23
```
arian@arian-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

vboxnet0  no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

arian@arian-laptop:~$ 

```

I'll try if it works tonight

---

### Post by arianstolwijk on 2010-02-25
It doesn't work yet... there are no wireless connections in the Network Manager Menu (only the wired one)

---

### Post by chili555 on 2010-02-25
Please detach the wire and try again.

---

### Post by arianstolwijk on 2010-03-01
Actually, it isn't connected... even after a restart.

---

### Post by arianstolwijk on 2010-03-02
I've made a screenshot to show you

---

### Post by chili555 on 2010-03-02
When you run 'sudo lshw -C network' is your Intel still unclaimed? Is the driver module *iwlagn* loading automagically? Find out with:```
lsmod | grep iwl
```I noticed this:> WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignoredIs ndiswrapper loading?```
lsmod | grep ndis
```Is *iwlagn* blacklisted from your unsuccessful ndiswrapper installation?

---

### Post by arianstolwijk on 2010-03-06
lsmod | grep iwl didn't return anything, so I did the following:

```
arian@arian-laptop:~$ lsmod | grep iwl
arian@arian-laptop:~$ lsmod
Module                  Size  Used by
isofs                  31620  1 
udf                    80932  0 
crc_itu_t               1852  1 udf
binfmt_misc             8356  1 
bridge                 47952  0 
stp                     2272  1 bridge
bnep                   12060  2 
vboxnetflt             85288  0 
vboxnetadp             78760  0 
vboxdrv               121608  1 vboxnetflt
pata_pcmcia            11228  1 
snd_hda_codec_analog    59292  1 
pcmcia                 36840  1 pata_pcmcia
iptable_filter          3100  0 
uvcvideo               59112  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
snd_hda_intel          26984  2 
snd_hda_codec          75708  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75520  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
ppdev                   6688  0 
joydev                 10240  0 
btusb                  11856  2 
nvidia               9587272  38 
parport_pc             32228  1 
snd_seq_midi            6432  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
tpm_infineon            8392  0 
tpm                    15680  1 tpm_infineon
tpm_bios                6268  1 tpm
hp_accel               11228  0 
lis3lv02d               7452  1 hp_accel
input_polldev           3716  1 lis3lv02d
sdhci_pci               7132  0 
sdhci                  17632  1 sdhci_pci
led_class               4096  2 hp_accel,sdhci
ricoh_mmc               3676  0 
psmouse                56500  0 
serio_raw               5280  0 
yenta_socket           24392  3 
rsrc_nonstatic         12124  1 yenta_socket
pcmcia_core            36560  3 pcmcia,yenta_socket,rsrc_nonstatic
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9252  2 snd_hda_intel,snd_pcm
ndiswrapper           185692  0 
usbhid                 38304  0 
ohci1394               30220  0 
ieee1394               86628  1 ohci1394
video                  19380  0 
output                  2780  1 video
e1000e                122668  0 
intel_agp              27748  0 
agpgart                35020  2 nvidia,intel_agp

```

As far as I can see, my Intel Wireless card is still unclaimed:

```
arian@arian-laptop:~$ sudo lshw -C network
[sudo] password for arian: 
  *-network               
       description: Ethernet interface
       product: 82567LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 03
       serial: 00:25:b3:c0:21:bf
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k2 duplex=full firmware=1.8-3 ip=192.168.2.111 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:30 memory:db300000-db31ffff memory:db324000-db324fff ioport:80e0(size=32)
  *-network UNCLAIMED
       description: Network controller
       product: Wireless WiFi Link 5300
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:db100000-db101fff
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

I did try something with ndiswrapper, and I can remember I blacklisted something, so it could be it was iwlagn, but I cannot remember that precisely 

Thanks for your help so far and sorry for my slow response!

---

