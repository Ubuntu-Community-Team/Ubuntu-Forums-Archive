---
title: "[DRIVER INSTALL?] ATI Radeon Xpress 200M"
date: 2010-12-28
forum: Multimedia Software
---

### Post by WarrenSH on 2010-12-28
I am using Ubuntu 10.10 32bit OS with a AMD Sempron & ATI Radeon™ Xpress 200M GFX card. 

How can I get the ATI Radeon™ Xpress 200M driver installed & running on my laptop? 

I went to System > Administration > Additional Drivers 

To find that nothing is listed for ATI :o

Enjoy this screen shoot of it it.

[CENTER][IMG]http://img195.imageshack.us/img195/8029/screenshotwi.png[/IMG][/CENTER]


Please help me get this driver installed & working tso I can play games & etc better on this laptop <3 you all :KS

---

### Post by amsterdamharu on 2010-12-28
Just to make sure how Ubuntu detects your card could you post the output of the following command?

```
sudo lshw -C video
```

And see what is loaded for drivers so far:

```
lsmod
```

To execute the commands you can press alt + F1, type gnome-terminal and click run. Then copy one command and paste it in the terminal (black screen that showed up after you clicked run). Use the mouse to paste commands in the terminal.
Then you can select all the text in the terminal, right click and select copy. When pasting it here please wrap it in &#91;code] &#91;/code] tags.

---

### Post by amsterdamharu on 2010-12-28
If it is the card you say it is you should be in luck. According to Ubuntu community help the card is supported and has 3D support.
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

You can either choose to install the fglrx (if it's not already), or the open source driver.

---

### Post by WarrenSH on 2010-12-28
> **amsterdamharu said:**
> Just to make sure how Ubuntu detects your card could you post the output of the following command?

```
sudo lshw -C video
```

sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Radeon XPRESS 200M 5955 (PCIE)
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=66 mingnt=8
       resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff


```
lsmod
```

Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
radeon                828445  3 
snd_atiixp_modem        9147  5 
snd_atiixp             12426  3 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
b43                   168681  0 
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
mac80211              231541  1 b43
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                  5223  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
cfg80211              144470  2 b43,mac80211
video                  18712  0 
ati_agp                 5202  0 
i2c_algo_bit            5168  1 radeon
snd                    49038  21 snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
psmouse                59033  0 
shpchp                 29886  0 
i2c_piix4               8635  0 
serio_raw               4022  0 
led_class               2633  1 b43
agpgart                32011  3 ttm,drm,ati_agp
k8temp                  3228  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
ssb                    39288  1 b43
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2

---

### Post by amsterdamharu on 2010-12-28
It looks like it's installed: ati_agp is loaded, this is the open source driver and should support 3D support.

Can you press alt + F2, then type gnome-control-center and click run.

There should be compizconfig under Look and feel. Try to activate wobbly windows under effects and move the window around.

---

### Post by amsterdamharu on 2010-12-28
PS: I meant formatting the output with code tags so it reads easier:
```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
radeon                828445  3 
snd_atiixp_modem        9147  5 
snd_atiixp             12426  3 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
b43                   168681  0 
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
mac80211              231541  1 b43
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                  5223  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
cfg80211              144470  2 b43,mac80211
video                  18712  0 
ati_agp                 5202  0 
i2c_algo_bit            5168  1 radeon
snd                    49038  21  snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm ,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
psmouse                59033  0 
shpchp                 29886  0 
i2c_piix4               8635  0 
serio_raw               4022  0 
led_class               2633  1 b43
agpgart                32011  3 ttm,drm,ati_agp
k8temp                  3228  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
ssb                    39288  1 b43
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2
```

---

### Post by WarrenSH on 2010-12-28
> **amsterdamharu said:**
> PS: I meant formatting the output with code tags so it reads easier:
```
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
binfmt_misc             6599  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8767  0 
radeon                828445  3 
snd_atiixp_modem        9147  5 
snd_atiixp             12426  3 
snd_ac97_codec         99227  2 snd_atiixp,snd_atiixp_modem
arc4                    1165  2 
ac97_bus                1014  1 snd_ac97_codec
snd_pcm                71475  6 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
b43                   168681  0 
ttm                    56633  1 radeon
snd_seq_midi_event      6047  1 snd_seq_midi
drm_kms_helper         30200  1 radeon
mac80211              231541  1 b43
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
hp_wmi                  5223  0 
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
drm                   168092  5 radeon,ttm,drm_kms_helper
cfg80211              144470  2 b43,mac80211
video                  18712  0 
ati_agp                 5202  0 
i2c_algo_bit            5168  1 radeon
snd                    49038  21  snd_atiixp,snd_atiixp_modem,snd_ac97_codec,snd_pcm ,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
output                  1883  1 video
psmouse                59033  0 
shpchp                 29886  0 
i2c_piix4               8635  0 
serio_raw               4022  0 
led_class               2633  1 b43
agpgart                32011  3 ttm,drm,ati_agp
k8temp                  3228  0 
soundcore                880  1 snd
snd_page_alloc          7120  3 snd_atiixp,snd_atiixp_modem,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
8139too                19581  0 
8139cp                 16934  0 
ssb                    39288  1 b43
mii                     4425  2 8139too,8139cp
pata_atiixp             3288  2
```


I guess my main reason for posting this was I d/l the game called Mad Skills Motocross [http://www.madskillsmotocross.com/](http://www.madskillsmotocross.com/)

I d/l the Linux version and when I go play it my screen flashes black & shows the game its kinda like a strobe effect. I posted on the games facebook.com & they asked me to make sure that my gfx card was installed on Ubuntu. 

Any ideas on whats going on with this game or why it would do the flashing thing with my gfx card being installed?

---

### Post by amsterdamharu on 2010-12-28
> You can either choose to install the fglrx (if it's not already), or the open source driver.

Ok, so you'd like to replace the opensource driver with the fglrx driver.
Do you have wired Internet? I am thinking of removing the open source and installing the fglrx driver but have to shut down gnome and that usually means not wireless.

Anyway, assuming you have cable connected Internet you could try:
Log out
press control + alt + F1
log in (text only) and type the following commands:
```
sudo service gdm stop
sudo apt-get purge xserver-xorg-video-ati
sudo apt-get install xorg-driver-fglrx
sudo service gdm start
```

I am having some trouble getting on google here because the great and wise government of China has resided to be a pain and block google and yahoo for me, will be stuck with connection reset for the next hour or so whenever I try to get on there.

There is a help page with a lot more complicated way of doing it (if the above fails) you can find it by googling:
```
site:help.ubuntu.com ATI fglrx
```
If I have the package names wrong for maverick you can search for the right name by googling:
```
site:packages.ubuntu.com ATI x200 driver
```

---

### Post by WarrenSH on 2010-12-28
> **amsterdamharu said:**
> Ok, so you'd like to replace the opensource driver with the fglrx driver.
Do you have wired Internet? I am thinking of removing the open source and installing the fglrx driver but have to shut down gnome and that usually means not wireless.

Anyway, assuming you have cable connected Internet you could try:
Log out
press control + alt + F1
log in (text only) and type the following commands:
```
sudo service gdm stop
sudo apt-get purge xserver-xorg-video-ati
sudo apt-get install xorg-driver-fglrx
sudo service gdm start
```

I am having some trouble getting on google here because the great and wise government of China has resided to be a pain and block google and yahoo for me, will be stuck with connection reset for the next hour or so whenever I try to get on there.

There is a help page with a lot more complicated way of doing it (if the above fails) you can find it by googling:
```
site:help.ubuntu.com ATI fglrx
```
If I have the package names wrong for maverick you can search for the right name by googling:
```
site:packages.ubuntu.com ATI x200 driver
```


Will I be able to use my wireless after doing the above process? What can go wrong with doing this? Is there a safe way to get the ATI drivers to install?

---

### Post by amsterdamharu on 2010-12-28
Your wireless should be fine. It's uninstalling the opensource driver and installing the fglrx as you want.

There is no guaranty that your game will work better because different drivers have different results with different cards.

---

