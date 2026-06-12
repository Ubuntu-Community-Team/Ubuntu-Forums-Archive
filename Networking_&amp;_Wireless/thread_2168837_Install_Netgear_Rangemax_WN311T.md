---
title: "Install Netgear Rangemax WN311T"
date: 2013-08-19
forum: Networking &amp; Wireless
---

### Post by Mahmoud shedid on 2013-08-19
Hi everyone,I have A Netgear Rangemax WN311T adapter, And I tired to install this:

[http://lkml.indiana.edu/hypermail/linux/kernel/1204.3/01981.html](http://lkml.indiana.edu/hypermail/linux/kernel/1204.3/01981.html)

But I could not applied patch ](*,).
Can anyone help me to install this adaptor?? :(

```

$ uname -a
Output: 
Linux dragon 3.8.0-27-generic #40-Ubuntu SMP Tue Jul 9 00:17:05 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

```

$ sudo lspci -nn | grep Marvell
Output: 
07:05.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88W8361 [TopDog] 802.11n Wireless [11ab:2a02] (rev 03)

```

Thanks,,

---

### Post by praseodym on 2013-08-19
For this device you need Ndiswrapper:
```

sudo apt-get install --reinstall linux-headers-generic linux-headers-$(uname -r) build-essential dkms ndisgtk ndiswrapper-dkms
```
Driver here:
[http://media.cdn.ubuntu-de.org/forum/attachments/13/28/2732001-WN311T_32_64bitXP.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/13/28/2732001-WN311T_32_64bitXP.tar.gz)

---

### Post by Mahmoud shedid on 2013-08-19
Thanks praseodym for replying,
but this adapter still not working

```

$ ndiswrapper -l
Output:
netmw14x : driver installed
    device (11AB:2A02) present

```

```

$ iwconfig
Output:
eth0      no wireless extensions.


lo        no wireless extensions.



```

---

### Post by praseodym on 2013-08-20
Check:```


lsmod
dmesg | grep ndis
cat /etc/modprobe.d/ndiswrapper.conf
sudo iwlist scan
rfkill list
```

---

### Post by Mahmoud shedid on 2013-08-20
```

$ lsmod
Output:
Module                  Size  Used by
nls_iso8859_1          12713  0 
usb_storage            57204  0 
nls_utf8               12557  1 
isofs                  39815  1 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228667  10 bnep,rfcomm
dm_crypt               22820  0 
binfmt_misc            17500  1 
snd_hda_codec_analog    93738  1 
gpio_ich               13476  0 
coretemp               13355  0 
kvm                   443165  0 
snd_hda_intel          39619  2 
snd_hda_codec         136453  2 snd_hda_intel,snd_hda_codec_analog
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
ppdev                  17073  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
parport_pc             28152  1 
lpc_ich                17061  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
mac_hid                13205  0 
snd_timer              29425  2 snd_pcm,snd_seq
snd                    68876  13 snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_hda_codec_analog
dcdbas                 14397  0 
ndiswrapper           283323  0 
soundcore              12680  1 snd
i5400_edac             17266  0 
shpchp                 37032  0 
edac_core              62003  2 i5400_edac
lp                     17759  0 
i5k_amb                13189  0 
parport                46345  3 lp,ppdev,parport_pc
psmouse                95870  0 
microcode              22881  0 
serio_raw              13215  0 
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
nouveau               943184  3 
mxm_wmi                13021  1 nouveau
tg3                   158031  0 
wmi                    19070  2 mxm_wmi,nouveau
mptsas                 62336  4 
video                  19390  1 nouveau
mptscsih               40289  1 mptsas
ptp                    18621  1 tg3
mptbase               101888  2 mptsas,mptscsih
scsi_transport_sas     40901  1 mptsas
i2c_algo_bit           13413  1 nouveau
pps_core               14080  1 ptp
ttm                    83187  1 nouveau
drm_kms_helper         49394  1 nouveau
drm                   286028  5 ttm,drm_kms_helper,nouveau

```
```

$ dmesg | grep ndis
Output:
[   24.192302] ndiswrapper version 1.58 loaded (smp=yes, preempt=no)
[   24.393003] ndiswrapper: driver netmw14x (NETGEAR,05/29/2006, 2.1.0.15) loaded
[   24.395184] ndiswrapper: using IRQ 26
[   25.229058] ndiswrapper (mp_init:211): couldn't initialize device: C0000001
[   25.229068] ndiswrapper (pnp_start_device:395): Windows driver couldn't initialize the device (C0000001)
[   25.229075] ndiswrapper (mp_halt:254): device ffff880110e19800 is not initialized - not halting
[   25.229077] ndiswrapper: device eth%d removed
[   25.229206] ndiswrapper: probe of 0000:07:05.0 failed with error -22
[   25.230368] usbcore: registered new interface driver ndiswrapper

```
```

$ cat /etc/modprobe.d/ndiswrapper.conf
Output:
alias wlan0 ndiswrapper

```
```

$ sudo iwlist scan
Output:
eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.



```

---

### Post by Mahmoud shedid on 2013-08-25
Dear praseodym 

Can you help me??

---

### Post by praseodym on 2013-08-25
Try to install the driver via terminal:
```

sudo ndiswrapper -i /path/to/driver/file.inf
```

---

### Post by Mahmoud shedid on 2013-08-25
```

$ sudo ndiswrapper -i NetMW14x.inf
Output:
driver netmw14x is already installed

```

:(

---

### Post by praseodym on 2013-08-25
Check:
```

sudo ndiswrapper -ma
```
Do you really want to use that device? Maybe its not working anymore with new kernels...

---

### Post by Mahmoud shedid on 2013-08-25
```

$ sudo ndiswrapper -ma
Output:
module configuration information is stored in /etc/modprobe.d/ndiswrapper.conf

```

Problem is that I have purchased ;)

---

### Post by praseodym on 2013-08-26
It is really "old". You may get a new stick for 10-15 $ with Atheros, Ralink or Realtek chipset which works ootb.

---

### Post by Mahmoud shedid on 2013-08-26
Dear praseodym

Thanks for your helping ;),,
And I will take your advice.

Thanks,,

---

### Post by praseodym on 2013-08-26
For example, I am using a TP-Link TL-WN821-N v3 with Atheros Chipset. Works ootb

---

