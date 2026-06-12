---
title: "saa7134 - gnomeradio - no sound"
date: 2008-06-01
forum: Multimedia Software
---

### Post by brainformat on 2008-06-01
hi! 
so, i have ubuntu 8.04 and asus my-cinema p7131 dual tv/fm tuner with philips saa7134 chip
it works great out of box. well allmost out of box :)
on earlier versions of ubuntu i had to use this script for starting gnomeradio. without it was silent.

```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/audio1 -t ossdsp -w -r 32000 /dev/dsp &
gnomeradio --mixer=/dev/mixer:pcm
wait gnomeradio
t=`pidof sox`;
kill $t;
alsamixer -c 0 sset PCM 80%,80% unmute
```

i've tried it also on hardy but with no success 
help me pls!

---

### Post by alexef on 2008-12-16
Well, I've got it working on intrepid with the following script:

```
#!/bin/sh
sox -r 32000 -w -t alsa hw:1,0 -t alsa hw:0,0 &
gnomeradio
wait gnomeradio
t=`pidof sox`;
kill $t;
```

I have an Avermedia Avertv Super 007 card.

---

### Post by lacoona on 2009-07-15
hi, same problem here... TV working fine, but radio not...
/dev/radio0 is created, but no sound in gnomeradio.
My card is Avermedia AVerTV GO 007 FM [card=57,autodetected]
Does anyone have a solution?

---

### Post by igorzwx on 2009-07-15
on 8.04 you should have Pulse.
This is the difference.

---

### Post by lacoona on 2009-07-15
yes, I have pulse but that does not bring me closer to the solution. 
As I said, tv works correctly.
I have Linux Mint Gloria, which is based on Jaunty.

---

### Post by igorzwx on 2009-07-15
ask markbuntu, he knows everything

---

### Post by fbugnon on 2009-07-16
The same problem here: no sound with gnomeradio with saa7134 chipset.

Running Ubuntu 9.04 x86_64 with updates.
I've installed a Pixelview PlayTV MPEG2 M4900, TV works fine under tvtime, but I hear nothing when playing Gnomeradio even though the program is able to run (/dev/radio0) and detects the radio stations.

**lspic** tells me:
```
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
```

**aplay -f** says:
```
placa 0: IXP [ATI IXP], dispositivo 0: ATI IXP AC97 [ATI IXP AC97]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
placa 0: IXP [ATI IXP], dispositivo 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Dispositivo secundário: 1/1
  Dispositivo secundário #0: subdevice #0
```

and from **dmesg** I get:
```
[    8.950179] bttv0: registered device radio0
[   22.833733] Registered led device: b43-phy0::radio
[    8.942009] tuner-simple 1-0061: creating new instance
[    8.942013] tuner-simple 1-0061: type set to 5 (Philips PAL_BG (FI1216 and compatibles))
[    8.943266] tuner' 1-0063: chip found @ 0xc6 (bt878 #0 [sw])
```

while under **/etc/modprobe.d/alsa-base.conf**:
```

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet -$
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
options snd-usb-caiaq index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from beeing loaded as first soundcard
options snd-pcsp index=-2
```

I've tried to play around with Volume Control, and also try following a couple of how-to like in

```
http://ubuntuforums.org/archive/index.php/t-232230.html

```

 but couldn't find the solution.

Any ideas how I can get this fixed?  All help is greatly appreciated.

__________________________________________
HP Pavilion a1130n

---

### Post by fbugnon on 2009-07-18
I'm sorry to reply to my own post. I forgot to say I also tried those scripts but they made no better.

But just now I've notice the error message when running from the terminal.  I've copied both scripts under files named radio and radio1.  Here are the messages I receive when they are executed:

```
./radio: 2: sox: not found
Fontconfig error: "/etc/fonts/conf.d/30-cjk-aliases.conf", line 1: no element found
lirc_init: Could not fine file/folder
gnomeradio-Message: Could not start lirc!
```

---

### Post by madmarx on 2010-11-13
This worked for me:
Open terminal
Launch alsamixer
Unmute "line" and increase volume
:guitar:

---

