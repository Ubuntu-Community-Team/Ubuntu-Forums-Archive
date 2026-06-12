---
title: "Acer Extensa 5420 wireless problems with 11.04"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by Longhorn134158 on 2011-06-08
[LEFT]Someone please help me... I have a fresh install of Ubuntu 11.04, Wireless doesn't work I don't even see a wireless option in the Internet connection drop-down menu, Ethernet is working however first try It said connected eth0, but now it doesn't show it's connected but it is, the wifi card is BCM4311 the common one, it has a signal up turn on switch on the front but it doesn't turn it on... Please help me!! :'([/LEFT]

---

### Post by Barton Bloke on 2011-07-15
I've just this day encountered the same problem. Did you ever find out how to turn the wireless adapter on and get it working?

---

### Post by realgary2 on 2011-10-19
I am having the same problem. I am a newbie to ubuntu but not to computers. The wifi adapter doesn't even show up. I tried the broadcom STA driver, as was suggested elsewhere, to no avail. Someone please help, I am very impressed so far with Ubuntu, except I need the wifi. Thanks in advance.

---

### Post by storyloops on 2011-11-16
Anyone - Is there a known solution to this?  I have the same problem with the latest Ubuntu.  *Bad karma for anyone who says to read the *@&@( manual.*

---

### Post by eyeaguda on 2012-01-02
Id also appreciate help regarding this problem! Damn, just noticed im on 10,10 not 10,04! Ah well hopefully i can get some help anyways!

---

### Post by wildmanne39 on 2012-01-02
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by eyeaguda on 2012-01-03
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

jonas@Jonas:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Jonas 3.0.0-14-generic-pae #23-Ubuntu SMP Mon Nov 21 22:07:10 UTC 2011 i686 athlon i386 GNU/Linux
jonas@Jonas:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 15)
    Subsystem: Acer Incorporated [ALI] Device [1025:0124]
    Kernel driver in use: sky2
--
05:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
    Subsystem: AMBIT Microsystem Corp. Device [1468:0422]
    Kernel modules: wl, ssb
jonas@Jonas:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

jonas@Jonas:~$ rfkill list all
0: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
jonas@Jonas:~$ lsmod
Module                  Size  Used by
usbhid                 41905  0 
hid                    77367  1 usbhid
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
acer_wmi               23302  0 
sparse_keymap          13658  1 acer_wmi
snd_hda_codec_realtek   254125  1 
binfmt_misc            17292  1 
pcmcia                 39822  0 
snd_hda_intel          28358  4 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
wl                   2646601  0 
snd_seq_midi_event     14475  1 snd_seq_midi
yenta_socket           27465  0 
pcmcia_rsrc            18367  1 yenta_socket
psmouse                63474  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
k8temp                 12905  0 
serio_raw              12990  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13495  0 
i2c_piix4              13093  0 
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
radeon                961834  2 
lib80211               14570  1 wl
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   196290  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
wmi                    18744  1 acer_wmi
ati_agp                13242  0 
nsc_ircc               23240  0 
irda                  185428  1 nsc_ircc
crc_ccitt              12595  1 irda
video                  18908  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35846  0 
sdhci_pci              13658  0 
firewire_core          56937  1 firewire_ohci
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
ahci                   21634  2 
libahci                25761  1 ahci
pata_atiixp            12967  0 
sky2                   49304  0 
jonas@Jonas:~$ 

```

There you go, thanks alot for helping!

---

### Post by wildmanne39 on 2012-01-03
Hi we need to change drivers.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
```
sudo modprobe b43
```
Thanks

---

### Post by eyeaguda on 2012-01-03
> **wildmanne39 said:**
> Hi we need to change drivers.
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
``````
sudo modprobe b43
```Thanks



Thanks alot! Solved my problems! Now i got all i need for the moment:) So awesome!

---

### Post by wildmanne39 on 2012-01-03
HI, your welcome! would you please go to the top of the page and mark this thread solved by clicking on thread tools. 
Thank you

---

