---
title: "X10 RF Remote Control (USB)- do not work"
date: 2008-09-13
forum: Mythbuntu
---

### Post by ds2k5 on 2008-09-13
RF Remote Control
P/N 20017670
FCC ID: B4S20016398

USB RF Reciver
P/N 20017629

hello,
i have installed mythbuntu 8.10 aplha 4 (64bit)
with updates up to 13 sep 2008
backend & frontend on the same machine

Kernel: 2.6.27-3-generic


i have configured in mybuntu control center 

Module: lirc_atiusb
Konfiuration: /usr/share/lirc/remotes/atiusb/lircd.conf.atiusd

or

ATI/NVIDA X10 RF (KERNEL)

or

ATI/NVIDA X10 RF (userspace)

restartet the backend & frontend

nothing happend in frontend.


root      8205  0.0  0.0  18144   784 ?        Ss   06:19   0:00 /usr/sbin/lircd --device=/dev/lirc0



The Remote Controll is OK
i can do a sudo irrecord -d /dev/lirc0 X10.conf for example


begin remote

  name  X10.conf
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   8
  pre_data       0x14
  post_data_bits  16
  post_data      0x0
  gap          227989
  toggle_bit_mask 0x0

      begin codes
          DOWN                     0xF722
          UP                       0xEF1A
          LEFT                     0xF21D
          RIGHT                    0xF41F
          OK                       0xF31E
          CH+                      0xE00B
          CH-                      0xE10C
          VOL+                     0xDE09
          VOL-                     0xDD08
          TV                       0x012C
          VCR                      0x022D
          DVD                      0xD904
          MUSIC                    0xDB06
          RADIO                    0x032E
          PHOTO                    0xDA05
          RECORD                   0xFC27
          STOP                     0xFD28
          PLAY                     0xFA25
          <<                       0xF924
          >>                       0xFB26
          ||                       0xFE29
          |<<                      0xF621
          >>|                      0xF823
          POWER                    0xD702
          SETUP                    0xF01B
          CHLIST                   0x0530
          1                        0xE20D
          2                        0xE30E
          3                        0xE40F
          4                        0xE510
          5                        0xE611
          6                        0xE712
          7                        0xE813
          8                        0xE914
          9                        0xEA15
          0                        0xEC17
          DELETE                   0xF520
      end codes

end remote


What dit i wrong ?




# lsusb
Bus 001 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless 
Transceiver (ACPI-compliant)

# lsmod

Module                  Size  Used by
af_packet              29568  2 
lirc_atiusb            26160  0 
lirc_dev               22216  1 lirc_atiusb
ipv6                  314312  23 
sbs                    22288  0 
video                  28948  0 
output                 11776  1 video
container              12288  0 
sbshc                  14592  1 sbs
pci_slot               13704  0 
wmi                    15808  0 
battery                21128  0 
iptable_filter         11520  0 
ip_tables              28176  1 iptable_filter
x_tables               31752  1 ip_tables
xfs                   575760  1 
ac                     13448  0 
lp                     19588  0 
snd_hda_intel         489264  1 
snd_pcm_oss            52608  0 
snd_mixer_oss          25088  1 snd_pcm_oss
snd_pcm                99208  2 snd_hda_intel,snd_pcm_oss
snd_seq_dummy          11524  0 
snd_seq_oss            42368  0 
snd_seq_midi           15872  0 
snd_rawmidi            34176  1 snd_seq_midi
snd_seq_midi_event     16768  2 snd_seq_oss,snd_seq_midi
stv0299                19848  1 
snd_seq                67168  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34320  2 snd_pcm,snd_seq
snd_seq_device         16404  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    79304  11 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                51612  0 
budget_ci              27780  24 
budget_core            20740  1 budget_ci
dvb_core               99756  3 stv0299,budget_ci,budget_core
saa7146                27400  2 budget_ci,budget_core
ttpci_eeprom           10752  1 budget_core
serio_raw              14596  0 
ir_common              51716  1 budget_ci
soundcore              16800  1 snd
i2c_nforce2            15752  0 
k8temp                 13568  0 
snd_page_alloc         17680  2 snd_hda_intel,snd_pcm
nvidia               7779928  26 
i2c_core               36128  6 stv0299,budget_ci,budget_core,ttpci_eeprom,i2c_nforce2,nvidia
shpchp                 42140  0 
pci_hotplug            39472  1 shpchp
parport_pc             44200  1 
parport                50096  2 lp,parport_pc
button                 15904  0 
evdev                  20512  8 
ext3                  150544  1 
jbd                    66472  1 ext3
mbcache                17924  1 ext3
sg                     45408  0 
sr_mod                 24772  0 
cdrom                  47784  1 sr_mod
sd_mod                 45864  4 
crc_t10dif             10240  1 sd_mod
pata_acpi              13568  0 
pata_amd               22020  3 
ata_generic            14212  0 
libata                200160  3 pata_acpi,pata_amd,ata_generic
forcedeth              67984  0 
ehci_hcd               48780  0 
ohci_hcd               34972  0 
scsi_mod              183160  4 sg,sr_mod,sd_mod,libata
dock                   18464  1 libata
usbcore               175248  4 lirc_atiusb,ehci_hcd,ohci_hcd
thermal                27424  0 
processor              49208  1 thermal
fan                    13576  0 
fbcon                  51200  0 
tileblit               11264  1 fbcon
font                   17152  1 fbcon
bitblit                14592  1 fbcon
softcursor             10496  1 bitblit
uvesafb                38056  0 
cn                     17068  1 uvesafb
fuse                   68288  1 


thanks for help

dennis

---

### Post by tobiz on 2009-03-12
I've having exactly the same problems as you wrt an X10 RF remote. Mine says it's a UR86E on the back. If found some material on this via google but still no success.  Did you ever get your to work?

---

### Post by xidahs on 2009-04-11
I'm having similar problems getting this remote to work. Ineed it to work with xbmc but i am given hope by the fact that is does partially work with xbmc live. I would like to figure out which file causes a few buttons on the remote to work in the hope that I can modify it to make the remaining buttons work. If anyone has any ideas it would be much appreciated as i'm getting pretty sick of googling the same keywords lirc xbmc rf remote and linux over and over again

---

### Post by xidahs on 2009-04-12
ok gonna update this so if future if I looses it again then maybe I can find it again here. 
Messed around with this remote with my ubuntu laptop and after running sudo dpkg-reconfigure lirc and choosing medion MD1 MDC i finally get an output from irw (not all keys but a lot more than I had  before) now to reconfigure lirc for xbmc fingers crossed.

---

### Post by xidahs on 2009-04-13
Ok just to update still havn't got it to work with xbmc sure I could get it to work if I installed ubuntu then installled xbmc on top of it but I really can't be bothered. Anyway I've changed the lircd.conf in both /etc and /etc/lirc to match the one in /usr/share/lircd/remotes/medion and I've changed my hardware.conf to read as it does on my stock ubuntu machine. However I still notice when I insert the usb receiver the lirc_atiusb module is loaded on the xbmc machine allowing up down left right and snapshot button to work but no others. I also noticed this does not happen on the stock ubuntu machine and when i remove the module using 
```
 modprobe -r lirc_atiusb 
```
the remote will stop working until I either insert the module or unplug and reinsert the usb  receiver
If anyone has any ideas where there are more lirc configuration files I would be willing to give them a try and report the results
Again to confirm ```
irw
``` does nothing on the xbmc machine and
 ```
sudo dpkg-reconfigure lirc 
```
fails every time

---

### Post by Infoteksec on 2009-09-21
Hi.

Did you get anywhere with this?

lsusb reports my device as:
```
Bus 004 Device 002: ID 0bc7:0006 X10 Wireless Technology, Inc. Wireless Transceiver (ACPI-compliant)
```

Thanks

---

### Post by williammanda on 2009-09-21
> **xidahs said:**
> I'm having similar problems getting this remote to work. Ineed it to work with xbmc but i am given hope by the fact that is does partially work with xbmc live. I would like to figure out which file causes a few buttons on the remote to work in the hope that I can modify it to make the remaining buttons work. If anyone has any ideas it would be much appreciated as i'm getting pretty sick of googling the same keywords lirc xbmc rf remote and linux over and over again

Your remote is probably being configured by HAL. Look at your Xorg.0.log and see if your remote has been setup. It probably will be setup as a keyboard. I'm not sure how to edit the HAL info, someone else will have to chime in.

---

