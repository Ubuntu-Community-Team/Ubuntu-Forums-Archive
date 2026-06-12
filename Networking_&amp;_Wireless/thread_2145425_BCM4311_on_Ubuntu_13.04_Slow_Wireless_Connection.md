---
title: "BCM4311 on Ubuntu 13.04: Slow Wireless Connection"
date: 2013-05-15
forum: Networking &amp; Wireless
---

### Post by Smaril on 2013-05-15
I finally managed to get the wireless working on my Dell Vostro 1000, which is a BCM4311 on Ubuntu 13.0.4. 

The problem I'm having now is the wifi is excruciatingly slow and I'm not even getting one fourth of my wireless speed. 

I've tried everything from here: [http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/) but nothing has worked so far. 

Does anybody have any suggestions?

[B]Update:
[/B]Maybe I need to try using ndiswrapper for the driver instead of whatever I am currently using.

---

### Post by Hadaka on 2013-05-16
Hi, the link you refered to is not for a broadcom card and the
ndiswrapper is a very last resort driver. So please dont load that.
your card uses the linux-firmware-nonfree driver. Please open a terminal
ctrl/alt/t then enter these commands.
```
lsmod
lspci -n
```
copy and paste the results.
thanks.

also you might want to ask a mod to move this to wireless

---

### Post by Smaril on 2013-05-16
lsmod
Module                  Size  Used byparport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
joydev                 17097  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17161  0 
dcdbas                 14021  1 dell_laptop
kvm_amd                50336  0 
kvm                   376505  1 kvm_amd
snd_hda_codec_idt      63896  1 
snd_hda_intel          38307  3 
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
k8temp                 12842  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
psmouse                81038  0 
serio_raw              13031  0 
arc4                   12543  2 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
sp5100_tco             13447  0 
radeon                870822  3 
snd                    56485  15 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_piix4              13066  0 
ttm                    71289  1 radeon
soundcore              12600  1 snd
drm_kms_helper         47545  1 radeon
drm                   228750  5 ttm,drm_kms_helper,radeon
i2c_algo_bit           13197  1 radeon
wmi                    18590  1 dell_wmi
ssb_hcd                12749  0 
shpchp                 32129  0 
ati_agp                13177  0 
b43                   351918  0 
bcma                   39645  1 b43
mac80211              526519  1 b43
video                  18894  0 
cfg80211              436177  2 b43,mac80211
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
pata_acpi              12886  0 
b44                    31137  0 
sdhci_pci              18158  0 
sdhci                  31824  1 sdhci_pci
ssb                    50628  3 b43,b44,ssb_hcd
pata_atiixp            13058  0 
ahci                   25507  2 
libahci                26108  1 ahci

lspci -n
00:00.0 0600: 1002:5950 (rev 10)
00:01.0 0604: 1002:5a3f
00:05.0 0604: 1002:5a37
00:06.0 0604: 1002:5a38
00:12.0 0106: 1002:4380
00:13.0 0c03: 1002:4387
00:13.1 0c03: 1002:4388
00:13.2 0c03: 1002:4389
00:13.3 0c03: 1002:438a
00:13.4 0c03: 1002:438b
00:13.5 0c03: 1002:4386
00:14.0 0c05: 1002:4385 (rev 14)
00:14.1 0101: 1002:438c
00:14.2 0403: 1002:4383
00:14.3 0601: 1002:438d
00:14.4 0604: 1002:4384
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
01:05.0 0300: 1002:5975
05:00.0 0280: 14e4:4312 (rev 01)
08:00.0 0200: 14e4:170c (rev 02)
08:01.0 0805: 1180:0822 (rev 19)
08:01.1 0880: 1180:0843 (rev 01)

---

### Post by Smaril on 2013-05-16
Also I am using the [COLOR=#000000]linux-firmware-nonfree driver it was the only one I found that actually allowed me to even turn on my WiFi, but the internet is still really slow.[/COLOR]

---

### Post by Hadaka on 2013-05-16
ok,looks like you have the b43 driver installed
which should work fine..let's try this..
please COPY  and paste one line at a time into
the terminal..
```
sudo modprobe -rfv dell_wmi 
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe -rfv b43
sudo modprobe b43
```
post back any changes or errors
thanks.

---

### Post by Hadaka on 2013-05-16
ok,looks like you have the b43 driver installed
which should work fine..let's try this..
please COPY  and paste one line at a time into
the terminal..
```
sudo modprobe -rfv dell_wmi 
sudo apt-get install --reinstall linux-firmware-nonfree
sudo modprobe -rfv b43
sudo modprobe b43
```
post back any changes or errors
thanks.

---

### Post by Hadaka on 2013-05-16
You can also change some settings in network mgr. to help
speed it up sometimes as well..

Network Mrg.....Edit Connections...Wireless...Click YOUR ssid...Edit...IPv4  then IPV6

make them look like this...

---

### Post by Smaril on 2013-05-17
For some reason it didn't post the results from the terminal and I'm at work at the moment but I copy and pasted the following commands into the terminal to reinstall the linux-firmware-nonfree driver, and I tried various combinations of editing the network settings per your suggestion but it's still really slow. I'm only getting about 3-5 mbps max on my 30 mbps internet connection. 

I hate how my old crappy laptop is such a pain to get working properly I'm almost considering putting my smaller hard drive back in with 12.0.4 where at least I got decent download speeds :/
[B]
Update:

[/B]I installed firmware-b43-installer and set the ipv settings to what you suggested and for some reason I managed to get at least 7 or 8 mbps. I'm not sure why that had any effect but I guess that's still better than what I was getting earlier although it's still approximately half of what I got on 12.0.4.

---

