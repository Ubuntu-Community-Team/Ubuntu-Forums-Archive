---
title: "No sound from analog jacks using Intel HDA sound - on G45 (dg45fc) MB"
date: 2008-12-30
forum: Multimedia Software
---

### Post by adix81 on 2008-12-30
Hi,

I've been messing around with this for ages now. Just got new DG45FC mb. I install ubuntu 8.10 and analog sound worked using the rear panel jacks however optical didn't. After reading many howto's and troubleshooting I upgraded ALSA to 1.0.18a. ooh looked like success - optical output worked :). then tested analog jacks, couldn't get sound from any of them.


i've tried various things since - 
I've tried adding "options snd-hda-intel model=basic" (plus lots of other variations from ALSA-Configuration.txt, e.g. model=5stack-digout) to /etc/modprobe.d/alsa-base - nothing has worked.

basically if i go for clean 8.10 install i get analog no optical, if i upgrade the driver i get optical no ananlog.

Has anyone had any experience with DG45FC or DG45ID or have any clue how to get this working.

Thanks in advance

---

### Post by adix81 on 2009-01-01
so no one has any ideas on this

---

### Post by tereyo on 2009-01-03
Hi

I have the MB Intel DG45ID and I'm using Intrepid 8.10...at first I couldn't make sound work at all..I don't remember what I installed but In System -> Preferences -> Sound -> Devices appeared a device just called "alsa"...I selected it everywhere,rebooted and analog sound worked great...Now I have reinstalled 8.10 and I don't remember how to get sound back. =(

Please help
Thanks

---

### Post by adix81 on 2009-01-06
Please Please i need help!!!!!!!1 - this is now doing my head in.

I still cannot get sound working properly on this board. I have followed so many guides, reinstalled ubuntu so many times, compiled alsa drivers so many times, played with mixers so many times.


Is this a bug??????? has anyone successfully managed to get analog jacks and optical jacks successfully working on the dg45fc or dg45id with the same driver?

Currently clean ubuntu install gives me sound through my front n rear jacks - no optical (not even light - i believe its not supported with this driver)

compile new alsa_1.0.18a driver get optical working great  but no sound from jacks.

so output using alsa 1.0.18a driver -

```
[COLOR="Blue"]htpc@adi-htpc:~$ lspci -nn | grep Audio
00:1b.0 Audio device [0403]: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller [8086:3a3e][/COLOR]
```

```
[COLOR="Blue"]htpc@adi-htpc:~$ cat /proc/asound/card0/codec#* | grep Codec
Codec: IDT 92HD73E1X5
Codec: Generic 8086 INTEL G45 DEVELK[/COLOR]
```

```
[COLOR="Blue"]htpc@adi-htpc:~$ dmesg | grep HDA
[   26.548686] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 22 (level, low) -> IRQ 22
[   26.548704] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   26.583028] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input6
[   26.868227] input: HDA Intel at 0xff940000 irq 22 Mic at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input8
[   26.875756] input: HDA Intel at 0xff940000 irq 22 Mic at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input9
[   26.888888] input: HDA Intel at 0xff940000 irq 22 Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input10
[   26.905520] input: HDA Intel at 0xff940000 irq 22 Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input11
[   26.920820] input: HDA Intel at 0xff940000 irq 22 Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input12
[   26.940712] input: HDA Intel at 0xff940000 irq 22 Speaker at Ext Rear Jack as /devices/pci0000:00/0000:00:1b.0/input/input13
[   26.956678] input: HDA Intel at 0xff940000 irq 22 HP Out at Ext Front Jack as /devices/pci0000:00/0000:00:1b.0/input/input14
[/COLOR]
```

```
[COLOR="Blue"]aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/COLOR]
```

[COLOR="Blue"]aplay -D hw:0,0 file.wav[/COLOR] -- [COLOR="Red"]results in sound from optical[/COLOR]
[COLOR="Blue"]aplay -D hw:0,1 file.wav[/COLOR] -- [COLOR="Red"]results in sound from optical[/COLOR]
[COLOR="Blue"]aplay -D hw:0,3 file.wav[/COLOR] -- [COLOR="Red"]results in sound from optical[/COLOR]

```
[COLOR="Blue"]htpc@adi-htpc:~$ mplayer -channels 6 /home/htpc/Audio/Eminem/stan.wav 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Duo CPU     E8400  @ 3.00GHz (Family: 6, Model: 23, Stepping: 10)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
Creating config file: /home/htpc/.mplayer/config

Playing /home/htpc/Audio/Eminem/stan.wav.
Audio file file format detected.
==========================================================================
Forced audio codec: mad
Opening audio decoder: [pcm] Uncompressed PCM audio decoder
AUDIO: 44100 Hz, 2 ch, s16le, 0.5 kbit/0.04% (ratio: 64->176400)
Selected audio codec: [pcm] afm: pcm (Uncompressed PCM)
==========================================================================
AO: [pulse] 44100Hz 2ch s16le (2 bytes per sample)
Video: no video
Starting playback...
A:76806.1 (21:20:06.1) of 1112202.0 (308:56:42.0)  0.1%[/COLOR]
```

[COLOR="Red"]result in no sound[/COLOR]


I've got lots more tests and things to say -- please please someone with a little more knowledge help me -I would like to know if this is a bug or i'm just being stupid..

---

### Post by markbuntu on 2009-01-06
You can look in here, there is some help for figuring out digital sound and everything else and a ton of links. You should look in the links in the HDA section, there may be some option you need to get a switch in your sound mixer for digital. There is also a digital section further on and a section on setting up the sound server that might be helpful.


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by adix81 on 2009-01-07
Hi thanks for you reply,

I've got optical digital working - the problem is i cannot get sound from my audio analog jacks. (alsa 1.0.18a)

but... if i use a clean ubuntu 8.10 install i get sound from analog jacks but nothing from optical (no matter how much playing i do - optical light doesn't even come on)

I've actually come across many of those threads in my previous time troubleshooting this - but there are some new suggestions i will try tonight.

I would like to stay on alsa 1.0.18a as this has hdmi sound support for my card (not working yet either :( - but that is another issue i which i havne't got round to figuring out)

It would good to know if anyone has managed to get optical and analog working at the same time on dg45fc or dg45id. (G45 ich10)

if you or anyone has any other thoughts please speak up.

cheers

---

### Post by Topfs on 2009-01-07
Just wanted to show my support and say I have the same issue.

sound on clean intrepid
updated to 1.0.18a no sound on analog jacks.

Can´t verify optical working as I have no optical, and HDMI audio doesnt work either.

Intel DG45FC.
I´ve tried removing /var/lib/alsa/asound.state and ~/.asound.rc both but it didnt help

---

### Post by Topfs on 2009-01-07
Forgot to say I run latest xorg from xorg-edgers which is according to aptitude 2.5.99.1 which should be lots later than the addition needed for HDMI audio.

Although this version I run doesnt have issues with software rasterizer so I wonder how good my X is but my HDTV is quite after the update (on clean intrepid I just get static on my tv, bad tv I know ;) ) so something have clearly worked somewhat.

---

### Post by adix81 on 2009-01-07
submitted a bug over at Alsa-project.org

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4324](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4324)

---

### Post by adix81 on 2009-01-08
Please someone correct if they think differently or possibly help me if you have more knowledge. I believe these sound issues maybe related to the 1.0.18a alsa driver codec mappings and this card.

As you know through my messages - i do not get analog audio when i upgrade to 1.018a. 
aplay -l gives lists the devices as expected - i.e. analog hw:0,0, digital hw:0,1, hdmi hw:0,3. (see above for actual results)

however with 1.0.18a aplay -D hw:0,x file.wav always results in sound being sent via the optical jack. regardless of what device you select. i'd expect sound from hw:0,0 to go through the jacks, hw:0,1 optical etc.. but i hear sound via optical jack on all.

on alsa 1.0.17, aplay -D hw:0,0 file.wav will give sound from analog jacks as expected, aplay -D hw:0,1 file.wav results in no sound as optical isn't supported i believe. hw:0,3 doesn't exist on 1.0.17. 

this is further reinforced as dmesg seems to show it initialising my analog jacks (see above)

to get HDMI audio I tried an upgrade to latest intel drivers also upgraded xorg i didn't get hdmi audio - but as explained above aplay -D hw:0,3 file.wav results in audio from optical.

Does anyone have any experience with codec mappings - that could make suggestions or anyone have any further thoughts.

all suggestions welcome - I need help

---

### Post by Topfs on 2009-01-08
I´ve tried compiling the latest one from git and using that but still no luck.

Gonna try jaunty now to see if kernel version helps

---

### Post by Topfs on 2009-01-08
I´ve tried compiling the latest one from git and using that but still no luck.

Gonna try jaunty now to see if kernel version helps.

---

### Post by 404wanderer on 2009-01-30
I'm using a DG45ID and have the same issues. Anyone any ideas yet before I throw the motherboard away?

---

