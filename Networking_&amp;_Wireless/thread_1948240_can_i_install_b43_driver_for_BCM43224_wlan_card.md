---
title: "can i install b43 driver for BCM43224 wlan card?"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by milkyky on 2012-03-27
Hi,

I'm trying to install b43 driver for my BCM43224 wlan card. As what i can see from here [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) my wlan card with PCI:ID [14e4:4353] is supported. 

Then after i google a  little bit i found these steps to install the b43 driver.
1. ~$ sudo apt-get install b43-fwcutter
2. ~$ sudo apt-get install b43-fwcutter firmware-b43-installer

And it comes out an error showing [14e4:4353] not supported. And i'm curious why i get this message since my wlan card is supported for b43 driver?

Before that i do install the Broadcom STA driver through the driver manager. So do i need to uninstall it first before install the b43 driver?

Hope someone can help me on this.Thank you.

---

### Post by wildmanne39 on 2012-03-28
Hi, that driver is supported in kernel version 3.1 and higher so you would have to have upgraded your kernel for that driver to work.

What version of ubuntu are you using?

Did you upgrade your kerenl?

Your card is support by the sta driver, and yes you can only have one installed at a time.

If you need more help post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.

We should be able to get your wireless working using the sta driver easier then upgrading the kernel.
Thank you

---

### Post by milkyky on 2012-03-28
Hi wildmanne39,
thanks for the fast reply. All right i'll get all the info once i'm in front of my laptop later. FYI, i'm trying aircrack-ng in my ubuntu. That's the reason why i want to install b43 driver for my bcm43224 wlan than install the STA driver.Because from what i google, i must install the b43 driver so that the injection will work. Is it correct?

thank you.

---

### Post by milkyky on 2012-03-28
below are the outputs:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux shane-pc 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011 i686 i686 i386 GNU/Linux

00:0a.0 Ethernet controller [0200]: nVidia Corporation MCP79 Ethernet [10de:0ab0] (rev b1)
	Subsystem: Dell Device [1028:0271]
	Kernel driver in use: forcedeth
--
06:00.0 Network controller [0280]: Broadcom Corporation BCM43224 802.11a/b/g/n [14e4:4353] (rev 01)
	Subsystem: Dell Device [1028:000e]
	Kernel driver in use: brcmsmac

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
mon0      IEEE 802.11abgn  Mode:Monitor  Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


Module                  Size  Used by
b43                   318816  0 
ssb                    50682  1 b43
btusb                  18160  0 
vesafb                 13489  1 
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     31426  1 
snd_hda_codec_idt      60049  1 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  11 btusb,bnep,rfcomm
binfmt_misc            17292  1 
joydev                 17393  0 
nvidia              10390874  60 
usbhid                 41905  0 
hid                    77367  1 usbhid
uvcvideo               67271  0 
videodev               85626  1 uvcvideo
wl                   2646601  0 
lib80211               14570  1 wl
bcma                   19571  0 
arc4                   12473  2 
dell_wmi               12601  0 
mxm_wmi                12859  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          24262  2 
snd_hda_codec          91754  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
dell_laptop            13519  0 
dcdbas                 14098  1 dell_laptop
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
psmouse                73673  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              591864  0 
serio_raw              12990  0 
brcmutil               16885  1 brcmsmac
mac80211              272785  2 b43,brcmsmac
snd                    55902  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              172392  3 b43,brcmsmac,mac80211
crc_ccitt              12595  1 brcmsmac
r852                   17901  0 
sm_common              16737  1 r852
nand                   49707  2 r852,sm_common
nand_ids                8547  1 nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
nand_ecc               13070  1 nand
mtd                    35852  2 sm_common,nand
shpchp                 32356  0 
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_nforce2            12906  0 
video                  18908  0 
ir_lirc_codec          12770  0 
lirc_dev               18700  1 ir_lirc_codec
wmi                    18744  2 dell_wmi,mxm_wmi
ir_sony_decoder        12493  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
ir_rc5_decoder         12490  0 
rc_rc6_mce             12454  0 
ir_nec_decoder         12490  0 
ite_cir                24743  0 
rc_core                25797  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,ite_cir
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usb_storage            44173  4 
uas                    17699  0 
xhci_hcd               72915  0 
firewire_ohci          35854  0 
sdhci_pci              13658  0 
sdhci                  27360  1 sdhci_pci
firewire_core          56937  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ahci                   21634  0 
libahci                25727  1 ahci
forcedeth              58103  0 
```

---

### Post by chili555 on 2012-03-28
> I'm trying to install b43 driver for my BCM43224 wlan card. As what i can see from here [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) my wlan card with PCI:ID [14e4:4353] is supported.For kernels 3.1 and above. However, in Ubuntu, it is not:```
ubuntu@ubuntu:~$ modinfo brcmsmac | grep 4353
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
ubuntu@ubuntu:~$ modinfo b43 | grep 4353
ubuntu@ubuntu:~$ uname -r
3.2.0-20-generic
```I am running, temporarily, 12.04 beta and b43 does not support your device. The driver in use, brcmsmac, does.

I can't speak to air-crack, et al.

---

### Post by wildmanne39 on 2012-03-28
Thanks chili555 before we went down that road and found out it did not work.

---

### Post by praseodym on 2012-03-28
Hi,

as chili555 mentioned above, the driver bcma/brcmsmac can work in 11.10 (it may work [better] from 12.04). In your case, blacklist the following modules:

```
sudo apt-get remove --purge b43-fwcutter firmware-b43-installer
echo -e "blacklist bcma\nblacklist brcm80211\nblacklist brcmsmac" | sudo tee /etc/modprobe.d/blacklist-bcm.conf 
```
Reboot, and check:
```

iwconfig
lsmod
sudo iwlist scan
route -n
```

---

### Post by CharlesA on 2012-03-28
FYI: aircrack isn't supported here.

---

