---
title: "NewbIie - Download speed very slow"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by Duncspur on 2012-03-12
Hi all,

I've only been using Ubuntu (11.10) for a couple of weeks but already love it.

However, the only issue I have is that my internet wireless connection seems very slow.  I have a 50mb connection and my Windows laptop (and my Mac) get between 30Mb and 50mb, but I am gettting around 1mb with Ubuntu.  I've had a look through a number of forums and tried a couple of things which I thought would work (such as turning off IP6) but to no avail.

I am using a Toshiba Equum 40 L17.

What am I doing wrong?

Any help gratefully received,

Duncan

---

### Post by praseodym on 2012-03-12
Please show the terminal (CTRL+ALT+T) outputs of

> lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list

---

### Post by Duncspur on 2012-03-12
> **praseodym said:**
> Please show the terminal (CTRL+ALT+T) outputs of

Hopefully, I've done this right?


duncan@Toshiba:~$ lspci -nnk | grep -iA2 net
05:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Toshiba America Info Systems Device [1179:ff40]
	Kernel driver in use: 8139too
duncan@Toshiba:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
duncan@Toshiba:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
arc4                   12473  2 
binfmt_misc            17292  1 
snd_hda_codec_realtek   254163  1 
rtl8187                56323  0 
mac80211              393421  1 rtl8187
cfg80211              172427  2 rtl8187,mac80211
eeprom_93cx6           12653  1 rtl8187
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
psmouse                73673  0 
serio_raw              12990  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  509519  3 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
asus_laptop            19050  0 
sparse_keymap          13658  1 asus_laptop
snd                    55902  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  2 
libahci                25727  1 ahci
8139too                23283  0 
8139cp                 22636  0 
duncan@Toshiba:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"Spurs1"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:33:DE:2A:76   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-33 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3217  Invalid misc:21530   Missed beacon:0

duncan@Toshiba:~$ rfkill list

---

### Post by Duncspur on 2012-03-14
Anybody got any idea?

---

### Post by praseodym on 2012-03-14
Looks not bat. Any more infos?

> dmesg | egrep 'rtl|country'
Add the nameservers of your ISP (or those of Google-public 8.8.8.8 and 8.8.4.4, respectively, seperated by comma) in the network-manager-applet.

Right-click->Edit connections->Wireless->IPv4-settings

Change to "Automatic (DHCP), addresses only" and add them in "DNS-servers". Restart the network afterwards.

---

