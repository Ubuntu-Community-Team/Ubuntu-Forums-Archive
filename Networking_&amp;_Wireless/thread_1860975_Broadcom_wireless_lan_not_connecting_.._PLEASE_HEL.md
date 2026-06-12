---
title: "Broadcom wireless lan not connecting .. PLEASE HELP.."
date: 2011-10-15
forum: Networking &amp; Wireless
---

### Post by Frostblade on 2011-10-15
hi..

i have a Samsung n150 plus netbook with Broadcom BCM4313 wireless lan... the same problem that prevented me from using ubuntu 10.10 still there in the new ubuntu 11.10 !

the wireless finds networks.. but does not connect... when i try to connect the icon flashes for seconds then it asks for the network password, i enter the password and after few second re asks for the password and so on without having a successful connection..

i downloaded the STA driver by wired connection and the same problem persist...

any help please, coz really like ubuntu and want to use it in my netbook but without wifi i cant !! :(

* using UBUNTU 11.10 desktop 32 bit
** tried the solutions in the sticked topic but wihtout benefit.
*** tried to change the ip to manual and didnt work
**** my internet modem is airties 206 .

thanx in advance for any suggestion.

---

### Post by praseodym on 2011-10-15
Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

---

### Post by Frostblade on 2011-10-15
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig
```

thanx for the reply ..

_**lspci -nnk | grep -iA2 net**_ :

 [FONT=&quot]05:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
      Subsystem: Wistron NeWeb Corp. Device [185f:051a]
      Kernel driver in use: brcmsmac
--
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354]
      Subsystem: Samsung Electronics Co Ltd Device [144d:c072]
      Kernel driver in use: sky2

[/FONT]
  

_**lsmod**_ :

 [FONT=&quot]Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  8 
parport_pc             32114  0 
ppdev                  12849  0 
binfmt_misc            17292  1 
bcma                   19571  0 
arc4                   12473  2 
snd_hda_codec_realtek   254125  1 
uvcvideo               67271  0 
snd_hda_intel          24262  2 
snd_hda_codec          91754  2 snd_hda_codec_realtek,snd_hda_intel
videodev               85626  1 uvcvideo
joydev                 17393  0 
brcmsmac              591864  0 
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80468  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
brcmutil               16885  1 brcmsmac
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
psmouse                73673  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
i915                  505108  3 
bluetooth             148839  23 bnep,rfcomm,btusb
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              12990  0 
mac80211              272785  1 brcmsmac
drm_kms_helper         32889  1 i915
drm                   192226  4 i915,drm_kms_helper
cfg80211              172392  2 brcmsmac,mac80211
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13199  1 i915
crc_ccitt              12595  1 brcmsmac
soundcore              12600  1 snd
video                  18908  1 i915
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
ahci                   21634  1 
libahci                25727  1 ahci
sky2                   49317  0 

[/FONT]
  

_**rfkill list**_ :

 [FONT=&quot]0: hci0: Bluetooth
      Soft blocked: no
      Hard blocked: no
1: phy0: Wireless LAN
      Soft blocked: no
      Hard blocked: no

[/FONT]
  
_**iwconfig**_ :

 [FONT=&quot]lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

[/FONT]

---

### Post by destructaball on 2011-10-15
Try removing the broadcom driver entering 

echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

into the terminal then re enabling it. I think that might help

Oh and restarting it after disabling it and at the end

---

### Post by Frostblade on 2011-10-15
> **destructaball said:**
> Try removing the broadcom driver entering 

echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf

into the terminal then re enabling it. I think that might help

Oh and restarting it after disabling it and at the end

sorry but am newbie .. if u explain the steps more ..

thanx

---

### Post by Frostblade on 2011-10-15
hi again...

i managed to blacklist bcma .... now in the blacklist.conf file the last line is : blacklist bcma..

restarted the pc ,, but the same problem..

i've installed Wicd network manager ... tried to connect though this manager ,,, it reaches to the "Validating authenticatoin.." and then a message appears , saying " authentication failed : bad password " !!!!!!!!!!

tried to remove the password from the internet modem "no wpa key" but just the same error message ..

what else can i try to make it connecting ... please :(

---

### Post by Frostblade on 2011-10-16
any suggestion , please ..

---

### Post by praseodym on 2011-10-16
Did you activate the STA-driver? Try WPA2-AES encryption if possible.

---

### Post by Frostblade on 2011-10-16
> **praseodym said:**
> Did you activate the STA-driver? Try WPA2-AES encryption if possible.

thanx for ur reply ..

yes i've already activated STA from addition drivers .. and rebooted but without benefit..
i also deactivated security of the internet modem (i.e. removed the password ) and tried to connect from ubuntu but the wireless icon flashed for few seconds then said wireless disconnected !...

what should i do ?! really like to use ubuntu but the wifi issue gonna make me crazy..

---

### Post by Frostblade on 2011-10-17
SOLVED..

thanx for everyone who tried to help..

how it's been solved :
1- installed Wicd (using wired connection )
2- removed network manager :
 sudo apt-get remove network-manager

then :
sudo apt-get purge network-manager network-manager-gnome

3-changed the security type of the internet modem from WPA/WPA2 to WEP-hex (coz the wireless lan never connected to the modem with WPA/WPA2 )..
now every thing working fine with the wireless lan..

thanx again..

---

