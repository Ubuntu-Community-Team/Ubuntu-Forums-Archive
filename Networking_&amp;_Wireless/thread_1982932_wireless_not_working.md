---
title: "wireless not working"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by gvrichie on 2012-05-19
Have inspiron 1720 with BCM 4311 802.11. Installed additional drivers. says it supports.
But wireless does not work ubutu 12.04

---

### Post by wildmanne39 on 2012-05-19
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod

```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by gvrichie on 2012-05-19
Thank you for responding.
I copied and pasted each line seperatley into a termina then shut down, unpluged ethernet, rebooted. Still not able to get wireless to work.
When I click on the icon on the top bar, I get no options for wireless.

---

### Post by wildmanne39 on 2012-05-19
Hi, read my post again, you are suppose to paste the information here.
Thanks

---

### Post by gvrichie on 2012-05-19
Are you saying I should paste the terminal results in a reply?

---

### Post by wildmanne39 on 2012-05-19
Hi, yes and follow the directions I gave in my first post to do so.
Thanks

---

### Post by gvrichie on 2012-05-19
rich@rich-Inspiron-1720:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

rich@rich-Inspiron-1720:~$ rfkill list all
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
rich@rich-Inspiron-1720:~$ lsmod
Module                  Size  Used by
rfcomm                 38139  0 
vesafb                 13516  1 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60251  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
nvidia              10962290  44 
dell_wmi               12601  0 
snd_seq_midi           13132  0 
sparse_keymap          13658  1 dell_wmi
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
dell_laptop            13671  0 
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  1 dell_laptop
b44                    31364  0 
ssb                    50691  1 b44
psmouse                72919  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
r852                   17901  0 
sm_common              16737  1 r852
serio_raw              13027  0 
nand                   49667  2 r852,sm_common
r592                   17808  0 
nand_ids                8547  1 nand
wl                   2646601  0 
mtd                    35584  2 sm_common,nand
nand_bch               13003  1 nand
bch                    21757  1 nand_bch
joydev                 17393  0 
memstick               15857  1 r592
nand_ecc               13070  1 nand
snd                    62064  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
wmi                    18744  1 dell_wmi
video                  19068  0 
ipw2200               146207  0 
libipw                 46701  1 ipw2200
cfg80211              178679  2 ipw2200,libipw
lib80211               14040  3 wl,ipw2200,libipw
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
usbhid                 41906  0 
hid                    77367  1 usbhid
rich@rich-Inspiron-1720:~$

---

### Post by wildmanne39 on 2012-05-19
Hi, you missed a few commands but from what you have given me it looks like you need to do:
```
sudo apt-get purge bcmwl-kernel-source broadcom-sta-common broadcom-sta-source
```
Then:
```
sudo apt-get install b43-fwcutter firmware-b43-installer
```
watch for errors, then reboot.

I have to leave for a little while.
Thanks

---

### Post by gvrichie on 2012-05-19
:p:p:p

Hey, Thanks loads Wildmanne.
That did it!
I have been trying to figure this out for over a week.

---

### Post by wildmanne39 on 2012-05-19
Hi, your welcome! please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by gvrichie on 2012-05-20
I'll be glad to do that, but I'm not sure how.
When I clicked on thread tools, it only gave me the option of "printable version"

---

### Post by gvrichie on 2012-05-20
My reply didn't seem to go through so I'll try again.
When I click on it it only gives me the option for printable version.
Don't quite know how to post that problem was solved.

---

### Post by wildmanne39 on 2012-05-20
Hi, I see you was able to mark it solved.
Thanks

---

