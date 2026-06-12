---
title: "Wireless Connection Lost Every Couple Days"
date: 2011-12-06
forum: Networking &amp; Wireless
---

### Post by deepfryerdan on 2011-12-06
I have Ubuntu 11.10 running as the sole OS on a Toshiba Satellite A215. 

The wireless connection (through an Atheros wireless adapter) works great for a few days (a week at most) and then it starts asking for a wireless password. If you type in the password it tries to connect for a minute or so before asking for the password again. This goes on and on to no end. If you click cancel or interrupt the process at all no wireless connections appear in the network drop down. Restarting doesn't change anything. 

If I take the computer and plug it into the router the wireless then turns right back on and reconnects. This lasts for another week before the process repeats. 

I've updated the drivers for the card but I haven't seen a difference. Unfortunately, I'm coming from a PC so I'm still pretty new at this. Any ideas?

---

### Post by wildmanne39 on 2011-12-06
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
Thank you

---

### Post by deepfryerdan on 2011-12-06
**deepfryerdan@emsiks:~$ cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux emsiks 3.0.0-13-generic #22-Ubuntu SMP Wed Nov 2 13:25:36 UTC 2011 i686 athlon i386 GNU/Linux
deepfryerdan@emsiks:~$ lspci -nnk | grep -iA2 net
0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
	Subsystem: Toshiba America Info Systems Device [1179:ff00]
	Kernel driver in use: r8169
--
14:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
	Subsystem: Askey Computer Corp. WLL3141 (Toshiba PA3613U-1MPC) 802.11bg Wireless Adapter [144f:7128]
	Kernel driver in use: ath5k
**deepfryerdan@emsiks:~$ iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"emsiks"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 58:6D:8F:62:A6:81   
          Bit Rate=36 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=32/70  Signal level=-78 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:21  Invalid misc:1127   Missed beacon:0

**deepfryerdan@emsiks:~$ rfkill list all**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
**deepfryerdan@emsiks:~$ lsmod**
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
binfmt_misc            17292  1 
snd_hda_codec_realtek   254125  1 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
pcmcia                 39822  0 
joydev                 17393  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
radeon                925094  4 
arc4                   12473  2 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
tifm_7xx1              12937  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
tifm_core              15040  1 tifm_7xx1
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73673  0 
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
soundcore              12600  1 snd
sp5100_tco             13495  0 
drm                   192226  6 radeon,ttm,drm_kms_helper
k8temp                 12905  0 
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
i2c_piix4              13093  0 
video                  18908  0 
i2c_algo_bit           13199  1 radeon
ath5k                 145100  0 
ath                    19387  1 ath5k
mac80211              393459  1 ath5k
sparse_keymap          13658  0 
shpchp                 32356  0 
cfg80211              172392  3 ath5k,ath,mac80211
ati_agp                13242  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          35854  0 
firewire_core          56937  1 firewire_ohci
sdhci_pci              13658  0 
usbhid                 41905  0 
hid                    77367  1 usbhid
sdhci                  27360  1 sdhci_pci
crc_itu_t              12627  1 firewire_core
pata_atiixp            12967  0 
ahci                   21634  2 
libahci                25727  1 ahci
r8169                  43104  0

---

### Post by wildmanne39 on 2011-12-06
Hi, first your Link Quality=32/70 Signal level=-78 dBm is weak.

Let's try this please:
Copy and paste this into the terminal.
```
gksudo gedit /etc/modprobe.d/ath5k.conf
```
Add a single line:
```
options ath5k nohwcrypt=1
```
Proofread carefully, save and close gedit. Reboot.
Thank you

---

### Post by deepfryerdan on 2011-12-06
alright, i've done all that. I'll give it a couple weeks to make sure it works. thanks for your super fast response and great help!

---

### Post by wildmanne39 on 2011-12-06
Hi, your welcome!!!
Good Luck

---

### Post by deepfryerdan on 2012-03-12
and I'm back. Same problem happening again. I thought it might be firmware-related so I wiped the HD, installed windows 7 and made sure the wifi card's firmware was up to date. I then installed ubuntu (dual boot). from startup I was unable to use the internet. I rebooted back into Windows and I can't get a connection there either. Physically plugging the computer into the router fixes the problem temporarily. I still can't figure out what is causing this.

Any more ideas?

---

### Post by wildmanne39 on 2012-03-13
Hi, I am not on much right now, but have you tried what is in post 4 again? since you reinstalled ubuntu you will need to redo those commands again.
Thanks

---

### Post by deepfryerdan on 2012-03-17
I did what was suggested like before. The connection worked for about 2 system restarts and now I'm back at square one. 

The funny thing is, when I leave it logged into Windows, it will stay connected for as long as I'm there but as soon as I go over to Ubuntu I lose that connection and can't get it back until I connect to the router again.

---

### Post by praseodym on 2012-03-17
Does Windows shut off the card at shutdown? Check your BIOS settings ("on", "last state", whatever) and maybe reset the BIOS to default settings

---

### Post by deepfryerdan on 2012-04-14
After doing some troubleshooting and more tests with my other computer that is the same as this one I think I have figured out what is going wrong with the wireless card.

This computer was rebuilt into a "digital photo frame" style (meaning the motherboard is sitting right behind the screen and they are never apart. I believe the heat from the screen is causing the wireless card to overheat and eventually shut down.

I'm going to rebuild the case with more ventilation and see if that solves the problem. Sorry for the inconvenience but thanks a lot for your help. I'll be sure to post again with progress.

---

