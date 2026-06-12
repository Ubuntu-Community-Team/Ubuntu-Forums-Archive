---
title: "Wireless problem Gateway LT4008U BCM4313"
date: 2013-04-01
forum: Networking &amp; Wireless
---

### Post by drfox on 2013-04-01
One of my staff bought a Gateway LT4008U, manufactured 5/2012. Its HD died a couple months ago and Gateway says it's out of warranty. I gave her a new HD, but Gateway wants $50 to send her a copy of Windows 7 Starter edition. Nice, huh?

I've installed Xubuntu (13.04) on her netbook, and everything is working EXCEPT her wireless card, a Broadcom BCM4313.

Can someone please help me get it working?  The wireless light stays orange, but it can detect the local wifi APs, just cannot connect to them. I have installed build-essentials, Broadcom STA drivers and common and dkms. Here's the output of some commands I've seen others ask :

jon@NikiBook:~$```
 lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:0624]
	Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e042]
	Kernel driver in use: wl

jon@NikiBook:~$ lsusb
Bus 001 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

jon@NikiBook:~$ lsusb
Bus 001 Device 002: ID 04f2:b209 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
jon@NikiBook:~$ lsmod
Module                  Size  Used by
parport_pc             31968  0 
ppdev                  12817  0 
bnep                   17669  2 
rfcomm                 37420  4 
bluetooth             202069  10 bnep,rfcomm
snd_hda_codec_realtek    63791  1 
snd_hda_codec_hdmi     36052  1 
snd_hda_intel          38307  3 
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
snd_hda_codec         117303  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
lib80211_crypt_tkip    17160  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
snd_hwdep              13272  1 snd_hda_codec
videobuf2_core         39161  1 uvcvideo
joydev                 17097  0 
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
wl                   2902185  0 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
videodev               95806  2 uvcvideo,videobuf2_core
snd_seq_midi_event     14475  1 snd_seq_midi
coretemp               13131  0 
snd_rawmidi            25114  1 snd_seq_midi
acer_wmi               27592  0 
gma500_gfx            167754  2 
sparse_keymap          13658  1 acer_wmi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
drm_kms_helper         47545  1 gma500_gfx
snd_timer              24411  2 snd_pcm,snd_seq
drm                   228750  3 drm_kms_helper,gma500_gfx
snd                    56485  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
lib80211               14040  2 wl,lib80211_crypt_tkip
microcode              18286  0 
i2c_algo_bit           13197  1 gma500_gfx
cfg80211              436177  1 wl
lpc_ich                16925  0 
psmouse                81038  0 
soundcore              12600  1 snd
serio_raw              13031  0 
rtsx_pci_ms            12875  0 
wmi                    18590  1 acer_wmi
memstick               15842  1 rtsx_pci_ms
mac_hid                13037  0 
lp                     13299  0 
video                  18894  2 acer_wmi,gma500_gfx
parport                40753  3 lp,ppdev,parport_pc
rtsx_pci_sdmmc         17238  0 
r8169                  61531  0 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci                   25507  4 
libahci                26108  1 ahci
jon@NikiBook:~$ 

jon@NikiBook:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

jon@NikiBook:~$ rfkill list
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jon@NikiBook:~$ 
```

Thanks, Larry

---

### Post by praseodym on 2013-04-01
Hi,

uninstall the Broadcom driver, connect via cable and install the missing firmware:
```

sudo apt-get remove --purge bcmwl-kernel-source
wget  http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```
You may need to clean up the old config:```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

---

### Post by wildmanne39 on 2013-04-01
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by drfox on 2013-04-06
> **praseodym said:**
> Hi,

uninstall the Broadcom driver, connect via cable and install the missing firmware:
```

sudo apt-get remove --purge bcmwl-kernel-source
wget  http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_fae7121.tar.gz -C /lib/firmware 
```
You may need to clean up the old config:```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf 
```
Reboot.

Worked like a charm! Thank you very much!

---

### Post by Israphel on 2013-04-07
Hello! I own a Thinkpad E430 with this wireless card. I installed Ubuntu 13.04 Beta2 and wifi works out of the box, but the signal is very poor. I can reach my AP because it's closer but with poor signal and of course I can't see any other AP.

After installing bcmwl-kernel-source the signal icreased to the top! and I can see every AP in the block. The speed was awesome. But it only works for a while then, even with full signal, internet and ping doesn't work, even after rebooting.

If I purge and re-install that package, I recover internet and lose it again after a while. And the story goes on....

I did that "firmware stuff" but it doesn't make any difference to me.

Any clue?

---

### Post by praseodym on 2013-04-08
I recommend using pure WPA2-AES encryption. Please check:
```

iwconfig
ifconfig -a
lsmod
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by Israphel on 2013-04-12
Yes, it's WPA2-AES

I'm now using STA driver 5 (from ubuntu Quantal) but on ubuntu Raring. I also locked the version.

It's working awesome. Someone had the same problem: [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1160471](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1160471)

Recently there were firmware updates on ubuntu raring and some files appeared on the brcm folder. Maybe the "open" driver is working again?

---

### Post by batman800 on 2013-05-09
> 
wget  [http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/39/45/5007272-Broadcom_Firmware_fae7121.tar.gz)
> **drfox said:**
> Worked like a charm! Thank you very much!

I can't access that link! = 404 - Not Found
For different driver it works!
Can you help me?

---

### Post by praseodym on 2013-05-09
The filename was updated:```


wget media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz
sudo tar xvf 5007272-Broadcom_Firmware_070513.tar.gz -C /lib/firmware 
```

---

### Post by Nobby on 2013-05-10
Hi, just wanted to say thanks for your posts praseodym.  Fixed the same issue I was having on my old Dell inspiron m101z with same Broadcom bcm4313 chip.  Cheers!

---

### Post by batman800 on 2013-05-13
Many thanks!!!
I'll try it asap!!

---

