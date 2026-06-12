---
title: "Help! Cant install tp-link wn821N on 10.10 even when following guidelines!"
date: 2011-10-23
forum: Networking &amp; Wireless
---

### Post by pellefantus on 2011-10-23
Hello,

I tried to install my tp-link wn821N on my ubuntu before by using a guide on ndiswrapper

from this forum, it didnt work :(

Then I followed this method:
[http://myubuntunotes.wordpress.com/2011/03/03/hello-world/](http://myubuntunotes.wordpress.com/2011/03/03/hello-world/)


and since the links were all down I found another post here:
[http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working-8.html](http://www.backtrack-linux.org/forums/backtrack-howtos/1042-how-get-ar9170-chipset-usb-adapter-working-8.html)

stating that wn821N driver could be found from this site:
installed the htc_9271.fw file from [http://linuxwireless.org/en/users/Drivers/ath9k_htc](http://linuxwireless.org/en/users/Drivers/ath9k_htc)

But my wireless card is not working when I try this. 
This is my /var/log/syslog output:
```
Oct 23 18:43:36 pc kernel: [ 1445.549205] usb 1-1.2: new high speed USB device number 10 using ehci_hcd
Oct 23 18:43:36 pc mtp-probe: checking bus 1, device 10: "/sys/devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.2"
Oct 23 18:43:37 pc kernel: [ 1445.808217] usb 1-1.2: reset high speed USB device number 10 using ehci_hcd
Oct 23 18:43:37 pc kernel: [ 1445.943763] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateReceiveNetBufferLists'
Oct 23 18:43:37 pc kernel: [ 1445.943774] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferList'
Oct 23 18:43:37 pc kernel: [ 1445.943781] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBuffer'
Oct 23 18:43:37 pc kernel: [ 1445.943788] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferList'
Oct 23 18:43:37 pc kernel: [ 1445.943794] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBuffer'
Oct 23 18:43:37 pc kernel: [ 1445.943801] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeMdl'
Oct 23 18:43:37 pc kernel: [ 1445.943814] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisOpenConfigurationEx'
Oct 23 18:43:37 pc kernel: [ 1445.943825] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSendNetBufferListsComplete'
Oct 23 18:43:37 pc kernel: [ 1445.943832] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMOidRequestComplete'
Oct 23 18:43:37 pc kernel: [ 1445.943841] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMIndicateStatusEx'
Oct 23 18:43:37 pc kernel: [ 1445.943852] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMSetMiniportAttributes'
Oct 23 18:43:37 pc kernel: [ 1445.943862] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMDeregisterMiniportDriver'
Oct 23 18:43:37 pc kernel: [ 1445.943869] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMRegisterMiniportDriver'
Oct 23 18:43:37 pc kernel: [ 1445.943892] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferListPool'
Oct 23 18:43:37 pc kernel: [ 1445.943898] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateIoWorkItem'
Oct 23 18:43:37 pc kernel: [ 1445.943910] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateMemoryWithTagPriority'
Oct 23 18:43:37 pc kernel: [ 1445.943917] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisGetSystemUpTimeEx'
Oct 23 18:43:37 pc kernel: [ 1445.943924] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferListPool'
Oct 23 18:43:37 pc kernel: [ 1445.943930] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisQueueIoWorkItem'
Oct 23 18:43:37 pc kernel: [ 1445.943942] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeNetBufferPool'
Oct 23 18:43:37 pc kernel: [ 1445.943948] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisAllocateNetBufferPool'
Oct 23 18:43:37 pc kernel: [ 1445.943955] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisFreeIoWorkItem'
Oct 23 18:43:37 pc kernel: [ 1445.943962] ndiswrapper (import:233): unknown symbol: NDIS.SYS:'NdisMResetComplete'
Oct 23 18:43:37 pc kernel: [ 1445.943967] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionBind'
Oct 23 18:43:37 pc kernel: [ 1445.943972] ndiswrapper (import:233): unknown symbol: WDFLDR.SYS:'WdfVersionUnbind'
Oct 23 18:43:37 pc kernel: [ 1445.943975] ndiswrapper (load_sys_files:206): couldn't prepare driver 'arusb_lh'
Oct 23 18:43:37 pc loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver arusb_lh
Oct 23 18:43:37 pc kernel: [ 1445.944553] ndiswrapper (load_wrap_driver:108): couldn't load driver arusb_lh; check system log for messages from 'loadndisdriver'
Oct 23 18:43:37 pc kernel: [ 1446.021205] usb 1-1.2: reset high speed USB device number 10 using ehci_hcd
Oct 23 18:43:37 pc mtp-probe: bus: 1, device: 10 was not an MTP device
Oct 23 18:43:37 pc kernel: [ 1446.158465] usb 1-1.2: driver   API: 1.9.4 2011-08-15 [1-1]
Oct 23 18:43:37 pc kernel: [ 1446.158470] usb 1-1.2: firmware API: 1.9.2 2010-12-25
Oct 23 18:43:37 pc kernel: [ 1446.158473] usb 1-1.2: failed to find compatible firmware descriptor.
Oct 23 18:43:37 pc kernel: [ 1446.158477] usb 1-1.2: failed to parse firmware (-61).

```[SIZE=4][B]
Is there a conflict between the old ndiswrapper failed drivers and the contents of /lib/firmware that makes me unable to get my card working?[/B][/SIZE]

---

### Post by chili555 on 2011-10-23
> Is there a conflict between the old ndiswrapper failed drivers and the contents of /lib/firmware that makes me unable to get my card working?Roughly, yes. First, let's get rid of ndiswrapper:```
sudo apt-get remove --purge ndiswrapper*
```Now reboot and let us see:```
ls /lib/firmware | grep ar | grep .fw
lspci -nn | grep 0280
```Thanks.

---

### Post by praseodym on 2011-10-23
Hi,

please show

```
lsusb
```
to see which chipset it is.

---

### Post by pellefantus on 2011-10-24
Hello!

These are my results:

/var/log/syslog after I put the device in:
Oct 24 22:29:19 pc kernel: [  128.156751] usb 1-1.1: new high speed USB device number 5 using ehci_hcd
Oct 24 22:29:19 pc mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.1"
Oct 24 22:29:19 pc mtp-probe: bus: 1, device: 5 was not an MTP device

$ls /lib/firmware | grep ar | grep .fw
ar7010_1_1.fw
ar7010.fw
ar9170-1.fw
ar9170-2.fw
ar9170.fw
ar9271.fw
atmsar11.fw
carl9170-1.fw
$ lspci -nn | grep 0280
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:54:6b:8a:25  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:41 
$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 004 Device 002: ID 046d:c30e Logitech, Inc. UltraX Keyboard (Y-BL49)
Bus 001 Device 005: ID 0cf3:1002 Atheros Communications, Inc. TP-Link TL-WN821N v2 [Atheros AR9001U-(2)NG]

---

### Post by pellefantus on 2011-10-24
Hi! sorry I wrote wrong before, I got ubuntu 11.10 !:popcorn:

---

### Post by praseodym on 2011-10-24
Ok, please show

```
lsmod
dmesg | grep 9170
rfkill list
sudo iwlist scan

```
if there are 2 modules loaded, namely **ar9170usb** and **carl9170**. If so, blacklist the wrong one:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv ar9170usb carl9170
sudo modprobe -v carl9170
```an replug the stick.

Uninstall ndiswrapper completely for that:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```

---

### Post by pellefantus on 2011-10-25
> **praseodym said:**
> Ok, please show

```
lsmod
dmesg | grep 9170
rfkill list
sudo iwlist scan

```if there are 2 modules loaded, namely **ar9170usb** and **carl9170**. If so, blacklist the wrong one:

```
echo "blacklist ar9170usb" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv ar9170usb carl9170
sudo modprobe -v carl9170
```an replug the stick.

Uninstall ndiswrapper completely for that:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
sudo depmod -a
sudo update-initramfs -u
```

Hello I got these results after trying all the commands and blacklisting:

$ dmesg | grep 9170
[    0.389170] pnp 00:07: [io  0x0070-0x0071]
[ 1934.348543] usbcore: registered new interface driver carl9170

syslog after putting in the usb stick:
```
ct 25 21:44:07 pc kernel: [ 2108.920371] usb 1-1.2: new high speed USB device number 5 using ehci_hcd
Oct 25 21:44:08 pc mtp-probe: checking bus 1, device 5: "/sys/devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.2"
Oct 25 21:44:08 pc kernel: [ 2109.140370] usb 1-1.2: reset high speed USB device number 5 using ehci_hcd
Oct 25 21:44:08 pc mtp-probe: bus: 1, device: 5 was not an MTP device
Oct 25 21:44:08 pc kernel: [ 2109.286587] usb 1-1.2: driver   API: 1.9.4 2011-08-15 [1-1]
Oct 25 21:44:08 pc kernel: [ 2109.286592] usb 1-1.2: firmware API: 1.9.2 2010-12-25
Oct 25 21:44:08 pc kernel: [ 2109.286594] usb 1-1.2: failed to find compatible firmware descriptor.
Oct 25 21:44:08 pc kernel: [ 2109.286598] usb 1-1.2: failed to parse firmware (-61).
```

lsmod
```
Module                  Size  Used by
carl9170               76064  0 
ath                    19148  1 carl9170
rfcomm                 37292  0 
bnep                   17711  2 
bluetooth             151637  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
kvm_intel              55857  0 
kvm                   336964  1 kvm_intel
snd_hda_codec_hdmi     31426  1 
joydev                 17393  0 
snd_hda_codec_realtek   254125  1 
nvidia              10390874  40 
arc4                   12473  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
binfmt_misc            17292  1 
rt73usb                26616  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19972  1 rt73usb
rt2x00lib              48229  2 rt73usb,rt2x00usb
mac80211              281428  3 carl9170,rt2x00usb,rt2x00lib
cfg80211              173231  4 carl9170,ath,rt2x00lib,mac80211
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
parport_pc             32114  1 
psmouse                63474  0 
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
video                  18908  0 
asus_atk0110           17742  0 
i2c_nforce2            12906  0 
wmi                    18744  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
pata_jmicron           12651  0 
ahci                   21634  2 
libahci                25761  1 ahci
forcedeth              58103  0 

```

$ rfkill list
<nothing>

$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2011-10-25
Is there another stick? If not, blacklist the rt73usb, too, and reload the carl::

```
echo "blacklist rt73usb" | sudo tee /etc/modprobe.d/blacklist-rt73usb.conf
sudo modprobe -rfv rt73usb carl9170
sudo modprobe -v carl9170
```
Is the firmware package "linux-firmware" installed? Install it, reboot, and post the check commands again.

---

### Post by pellefantus on 2011-10-25
> **praseodym said:**
> Is there another stick? If not, blacklist the rt73usb, too, and reload the carl::
There is another Stick but im only using it since this stick doesnt work.

Even when I blacklist rt73usb nothing happends

> **praseodym said:**
> 
```
echo "blacklist rt73usb" | sudo tee /etc/modprobe.d/blacklist-rt73usb.conf
sudo modprobe -rfv rt73usb carl9170
sudo modprobe -v carl9170
```Is the firmware package "linux-firmware" installed? Install it, reboot, and post the check commands again.

$ sudo apt-get install linux-firmware
[sudo] password for anon: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware is already the newest version.

---

### Post by praseodym on 2011-10-25
Recompile the drivers again with

```
./scripts/driver-select atheros
```

instead and reboot.

---

### Post by pellefantus on 2011-10-25
> **praseodym said:**
> Recompile the drivers again with

```
./scripts/driver-select atheros
```instead and reboot.
hello,

where is the script located?

---

### Post by praseodym on 2011-10-25
In the first posting there is a link for the compat-wireless installation you tried before?!

---

### Post by pellefantus on 2011-10-25
> **praseodym said:**
> In the first posting there is a link for the compat-wireless installation you tried before?!

I did 
./scripts/driver-select atheros

make

sudo make install

sudo make wlunload

and now I cant connect at all using my "backup" or TP-link USB!
in my blacklist.conf I now have: ar9170usb and rt73usb.

---

### Post by praseodym on 2011-10-25
Reload the "carl":

```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170
```
You can also load the rt73usb by hand:

```
sudo modprobe -v rt73usb
```
Replug the appropriate stick after these commands.

---

### Post by pellefantus on 2011-10-25
> **praseodym said:**
> Reload the "carl":

```
sudo modprobe -rfv carl9170
sudo modprobe -v carl9170
```
You can also load the rt73usb by hand:

```
sudo modprobe -v rt73usb
```
Replug the appropriate stick after these commands.

Hello,

it doesnt help at all. I cannot connect with neither usb. Was it really correct to build the script with "atheros" ?


```
sudo modprobe -v rt73usb
```
 fails with message:Error insering rt2x00liv (lon path): invalid argument
And there is a FATAL mesage with error inserting rt73usb

---

### Post by praseodym on 2011-10-25
Ok,

undo the installation of compat-wireless:

```
sudo rm -r /lib/modules/$(uname -r)/updates/net/
sudo depmod -a
sudo update-initramfs -u
```
and reboot. Check with the Atheros stick (the other one should now work again):

```
lsmod
iwconfig
dmesg | egrep 'rt7|9170'
sudo iwlist scan
iwlist chan
rfkill list
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by pellefantus on 2011-10-26
Hello!

Thanks for the tip!

I did what you said and I can surf with my old stick again.

This is the output of the commands after putting the wn821n in:
lsmod```
$ lsmod
Module                  Size  Used by
nls_iso8859_1          12617  0 
nls_cp437              12751  0 
vfat                   17308  0 
fat                    55577  1 vfat
twofish_generic        16579  0 
twofish_i586           12503  0 
twofish_common         20823  2 twofish_generic,twofish_i586
xts                    12644  0 
gf128mul               14503  1 xts
dm_crypt               22565  0 
arc4                   12473  0 
rt73usb                27029  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              20092  1 rt73usb
rt2x00lib              48114  2 rt73usb,rt2x00usb
mac80211              272785  2 rt2x00usb,rt2x00lib
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_realtek   254125  1 
kvm_intel              55857  0 
kvm                   336964  1 kvm_intel
nvidia              10390874  40 
joydev                 17393  0 
cfg80211              172392  2 rt2x00lib,mac80211
binfmt_misc            17292  1 
snd_hda_intel          28358  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
ppdev                  12849  0 
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63474  0 
serio_raw              12990  0 
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
shpchp                 32356  0 
video                  18908  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
asus_atk0110           17742  0 
wmi                    18744  0 
parport_pc             32114  1 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
pata_jmicron           12651  0 
forcedeth              58103  0 
ahci                   21634  3 
libahci                25761  1 ahci

``````
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


``````
$ dmesg| egrep 'rt73|9170'
[    0.391701] pnp 00:00: [mem 0xe0000000-0xfbffffff window]
[    0.391703] pnp 00:00: [mem 0xfe000000-0xfebfffff window]
[  159.251676] Registered led device: rt73usb-phy0::radio
[  159.251717] Registered led device: rt73usb-phy0::assoc
[  159.251766] Registered led device: rt73usb-phy0::quality
[  159.252270] usbcore: registered new interface driver rt73usb
[ 1007.486443] Registered led device: rt73usb-phy1::radio
[ 1007.486463] Registered led device: rt73usb-phy1::assoc
[ 1007.486482] Registered led device: rt73usb-phy1::quality

``````
$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

``````
$ iwlist chan
lo        no frequency information.

eth0      no frequency information.


``````
$ rfkill list

<empty>
``````
$ cat /etc/udev/rules.d/70-persistent-net.rules 
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x0ab0 (forcedeth)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:23:54:6b:8a:25", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x0cf3:0x1002 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="94:0c:6d:e2:23:43", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# USB device 0x13b1:0x0020 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:b6:5b:04:3c", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

```

---

### Post by praseodym on 2011-10-26
"carl" is not loaded:

```
sudo modprobe -v carl9170
```
Replug the stick and check:

```
lsmod
dmesg | grep 9170
iwconfig
sudo iwlist scan
```

---

### Post by pellefantus on 2011-10-27
> **praseodym said:**
> "carl" is not loaded:

```
sudo modprobe -v carl9170
```Replug the stick and check:

```
lsmod
dmesg | grep 9170
iwconfig
sudo iwlist scan
```

Hello, 

I get this: 
```

$ sudo modprobe -v carl9170
insmod /lib/modules/3.0.0-12-generic-pae/updates/drivers/net/wireless/ath/ath.ko 
WARNING: Error inserting ath (/lib/modules/3.0.0-12-generic-pae/updates/drivers/net/wireless/ath/ath.ko): Invalid argument
WARNING: Error inserting mac80211 (/lib/modules/3.0.0-12-generic-pae/kernel/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting carl9170 (/lib/modules/3.0.0-12-generic-pae/updates/drivers/net/wireless/ath/carl9170/carl9170.ko): Invalid argument

```

---

### Post by praseodym on 2011-10-27
Error messages?

```
dmesg | egrep 'ath|9170|80211'
```

---

### Post by pellefantus on 2011-11-03
> **praseodym said:**
> Error messages?

```
dmesg | egrep 'ath|9170|80211'
```

```

[   85.853776] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
[   85.853781] ath: Unknown symbol wiphy_apply_custom_regulatory (err -22)
[   85.853794] ath: disagrees about version of symbol freq_reg_info
[   85.853796] ath: Unknown symbol freq_reg_info (err -22)


```

---

### Post by praseodym on 2011-11-06
On page 1:
```
Oct 25 21:44:08 pc kernel: [ 2109.286594] usb 1-1.2: failed to find compatible firmware descriptor.
Oct 25 21:44:08 pc kernel: [ 2109.286598] usb 1-1.2: failed to parse firmware (-61).
```
Install the driver again and/or update the firmware:

 [http://www.linuxwireless.org/en/users/Drivers/carl9170#Firmware-1](http://www.linuxwireless.org/en/users/Drivers/carl9170#Firmware-1)

copy it to /lib/firmware

---

### Post by pellefantus on 2011-11-06
> **praseodym said:**
> On page 1:
```
Oct 25 21:44:08 pc kernel: [ 2109.286594] usb 1-1.2: failed to find compatible firmware descriptor.
Oct 25 21:44:08 pc kernel: [ 2109.286598] usb 1-1.2: failed to parse firmware (-61).
```Install the driver again and/or update the firmware:

 [http://www.linuxwireless.org/en/users/Drivers/carl9170#Firmware-1](http://www.linuxwireless.org/en/users/Drivers/carl9170#Firmware-1)

copy it to /lib/firmware

Hello, I downloaded the one for kernel 3.0+ and put it in the folder, but when I try to load it I get the following error:
```

$ sudo modprobe carl9170
WARNING: Error inserting mac80211 (/lib/modules/3.0.0-12-generic-pae/kernel/net/mac80211/mac80211.ko): Invalid argument
FATAL: Error inserting carl9170 (/lib/modules/3.0.0-12-generic-pae/updates/drivers/net/wireless/ath/carl9170/carl9170.ko): Invalid argument

```

This is what I get in the syslog when inserting my stick:
```

Nov  6 22:35:23 pc kernel: [  848.576613] usb 1-1.1: new high speed USB device number 6 using ehci_hcd
Nov  6 22:35:23 pc mtp-probe: checking bus 1, device 6: "/sys/devices/pci0000:00/0000:00:04.1/usb1/1-1/1-1.1"
Nov  6 22:35:23 pc mtp-probe: bus: 1, device: 6 was not an MTP device
Nov  6 22:35:23 pc kernel: [  848.870125] ath: disagrees about version of symbol wiphy_apply_custom_regulatory
Nov  6 22:35:23 pc kernel: [  848.870129] ath: Unknown symbol wiphy_apply_custom_regulatory (err -22)
Nov  6 22:35:23 pc kernel: [  848.870144] ath: disagrees about version of symbol freq_reg_info
Nov  6 22:35:23 pc kernel: [  848.870146] ath: Unknown symbol freq_reg_info (err -22)

```

---

### Post by praseodym on 2011-11-06
Do you really need the -PAE-kernel? How much RAM do you have? Is it possible to install a 64bit system?

---

### Post by pellefantus on 2011-11-07
> **praseodym said:**
> Do you really need the -PAE-kernel? How much RAM do you have? Is it possible to install a 64bit system?
I chose the 32 bit for greater hardware compatibility *sigh* but If I install a 64bit system I guess I have to reinstall everything, damnt. are you saying its is not solvable otherwise?

---

### Post by praseodym on 2011-11-07
If you have equal to or less than 4 GB of RAM (otherwise it doesnt make sense), just install the regular 32bit kernel:

```
sudo apt-get install --reinstall linux-image-generic linux-headers-generic build-essential dkms startupmanager
```
Choose the tool "startupmanager" to set this kernel as default boot kernel and reboot into it. Try to install the firmware first, then you may try to update the driver in the second term. Try both: Only the Atheros drivers and, if it doesnt work, all of compat-wireless.

---

### Post by pellefantus on 2011-11-07
> **praseodym said:**
> If you have equal to or less than 4 GB of RAM (otherwise it doesnt make sense), just install the regular 32bit kernel:

```
sudo apt-get install --reinstall linux-image-generic linux-headers-generic build-essential dkms startupmanager
```Choose the tool "startupmanager" to set this kernel as default boot kernel and reboot into it. Try to install the firmware first, then you may try to update the driver in the second term. Try both: Only the Atheros drivers and, if it doesnt work, all of compat-wireless.

This sounds like a very radical step. Will I be able to go back if it ***** up my computer? And if it works why did the drivers still work when I had 11.04, it must have been the same kernel back then!

---

### Post by praseodym on 2011-11-07
In 11.04 the **carl9170** is a default kernel module, in 10.10 you have to build it on your own, only ar9170usb is there.

Yes, you can uninstall this kernel via synaptic package manager anytime by booting into the -PAE-kernel.

I recommend to install compat-wireless completely, a newer version of ar9170usb will also be installed and can be tried.

---

