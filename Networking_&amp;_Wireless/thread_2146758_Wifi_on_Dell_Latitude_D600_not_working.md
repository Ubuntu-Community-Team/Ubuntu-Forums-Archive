---
title: "Wifi on Dell Latitude D600 not working"
date: 2013-05-19
forum: Networking &amp; Wireless
---

### Post by Hunter2451 on 2013-05-19
Hello, I have an old laptop that used to run windows xp, but the laptop is so old that xp doesn't run well, so I decided to put Ubuntu on it. There is a problem that pretty much everyone has on the Latitude D600 model, including me, where it doesn't find any access points. I followed this guide: http:// ubuntuforums. org/showthread.php?t=1621331 (remove the space in the .org and the http). It all worked well, until I got to the last step:

Type this into the terminal:
> 

sudo chmod o+rx /lib/firmware/b43 /lib/firmware/b43legacy



When I typed in that command, I got no output whatsoever, and the wifi was still not working.
Any help would be greatly appreciated! Thanks!

PS. If you give me a command to type into the  terminal, please explain it to me so that I
learn something!

---

### Post by Hadaka on 2013-05-19
Hi, and welcome !
lets start by looking at what network cards you have.
please COPY and paste,one line at a time into a terminal.

```
lspci -nn | egrep '0200|0280'
rfkill list all
lsmod
```
post back the output.
thanks.

*you may also ask a mod to move this to wireless

---

### Post by wildmanne39 on 2013-05-19
*Thread moved to **Networking & Wireless**.*

---

### Post by Hunter2451 on 2013-05-19
Hi! Thank you for your fast reply! I did as you said and this was the output:

> hunter@Hunter-UB:~$ lspci -nn | egrep '0200|0280'
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5702X Gigabit Ethernet [14e4:16a6] (rev 02)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 02)
hunter@Hunter-UB:~$ rfkill list all
hunter@Hunter-UB:~$ lsmod
Module                  Size  Used by
nls_utf8               12493  1 
isofs                  39553  1 
joydev                 17393  0 
snd_intel8x0           33455  2 
snd_ac97_codec        110213  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80916  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
dcdbas                 14098  0 
wl                   3032542  1 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
radeon                733914  2 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                96718  0 
pcmcia                 39826  0 
serio_raw              13027  0 
cfg80211              178877  1 wl
snd                    62218  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65344  1 radeon
lib80211               14040  1 wl
drm_kms_helper         45466  1 radeon
video                  19115  0 
soundcore              14635  1 snd
drm                   197641  4 radeon,ttm,drm_kms_helper
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
mac_hid                13077  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
bnep                   17830  2 
parport_pc             32114  1 
bluetooth             158479  7 bnep
ppdev                  12849  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
i2c_algo_bit           13199  1 radeon
shpchp                 32265  0 
tg3                   137318  0 



When I copied in rfkill list all, nothing happened.

Sorry for the late reply, I've been away from home and didn't bring the laptop with me.

EDIT: I feel  I should tell you that when I installed Ubuntu, I had to use the mini iso to get the non PAE required version. I'm not sure if this has any corrolation with anything, but now you know ;)

---

### Post by Hadaka on 2013-05-19
hi, please input the following...
COPY and paste one line at a time...

```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43

```
post back how that went.
thanks.

---

### Post by Hunter2451 on 2013-05-20
Ok, it installed the b43-fwcutter drivers but not the firmware-b43-installer. It told me that an unsupported device was found, and to use the legacy drivers. But I don't know what the package name is for the legacy drivers.

EDIT: Fixed! The command was (after typing in all the stuff you told me): > sudo apt-get install firmware-b43legacy-installer

---

### Post by mörgæs on 2013-05-20
Slightly off-topic: For the PAE problem [this]("https://help.ubuntu.com/community/PAE") might be of interest.

---

### Post by Hadaka on 2013-05-20
Great !, glad you got it working
enjoy !

@morgaes: good info on pae...thanks!

---

