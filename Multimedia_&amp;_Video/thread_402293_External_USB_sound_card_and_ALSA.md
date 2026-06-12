---
title: "External USB sound card and ALSA"
date: 2007-04-05
forum: Multimedia &amp; Video
---

### Post by garbage792 on 2007-04-05
Hi please help me because this is driving me mad.

Basically I am forced to use an external USB sound card because my on board headphone jack is dead. 
The external USB sound card is properly detected and does work in some ways.

I can use the usb sound card by going to system-->preferences-->sound and then selecting "USB Audio" from the drop down list. But sadly the flash in firefox does not detect this. I love youtube and so many other flash based sites like pandora etc. But these flash sites do not give me any sound even though I have set USB audio as default in my sound settings. :-/ 

The only solution I found that works for other people is to somehow make ALSA work with my USB and then use ALSA as a base for firefox.
The same problem is with wine. I do not get any sound in wine from my external usb card. So I am motivated to make alsa work with my USB sound card (unless someone can suggest any alternatives that can help me avoid ALSA).


Executing the following command gives me this
less /proc/asound/modules

0 snd_intel8x0
1 snd_usb_audio

It means that mu usb card is being detected by alsa. So its a good sign right?


Executing this command gives the following.

cat /proc/asound/cards
 0 [I82801DBICH4   ]: ICH4 - Intel 82801DB-ICH4
                      Intel 82801DB-ICH4 with STAC9750,51 at 0xe0100c00, irq 10
 1 [default        ]: USB-Audio - C-Media USB Audio       
                      C-Media INC. C-Media USB Audio        at usb-0000:03:00.0-1, full speed

So yes ALSA is aware of mu usb card.





Again alsa seems to be recognizing


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [C-Media USB Audio       ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Now here is the problem. I read through other posts in this forum and other forums and found out that I have to edit the /etc/modprobe.d/alsa-base file.

Here is the file

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --Qb snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq-midi ; /sbin/modprobe --quiet snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe -Qb saa7134-alsa ; : ; }

# Load snd-seq for devices that don't have hardware midi;
#   Ubuntu #26283, #43682, #56005; works around Ubuntu #34831 for
#   non-Creative Labs PCI hardware
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe -Qb snd-seq ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options cx88-alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388



I have done numerous things to the file and re-booted without any success
1.) I tried commenting out the line "options snd-usb-audio index=-2" 

2.) I tried replacing the line "options snd-usb-audio index=-2"  with "options snd-usb-audio index=0" .This turns the sound card off :( (The blue power light on the usb sound card basically turns off when I do this)

3.)I tried replacing the line "options snd-usb-audio index=-2"  with "options snd-usb-audio index=1". Nothing happened :*(

4.) I tried replacing the first line "install sound-slot-0 /sbin/modprobe snd-card-0" by 
"install sound-slot-0 /sbin/modprobe snd_usb_audio" and then tried messing again with the line "options snd-usb-audio index=-2" by changing the value to 1 or 0. It just does not work.

I have already spent hours and have rebooted dozens of times. I hate to give up using ubuntu due to this problem. Flash without audio is no fun :(.

---

### Post by garbage792 on 2007-04-05
Never mind. I just fixed the problem.
I basically used this command
 sudo gedit /etc/modprobe.d/blacklist

and then added this line at the end

blacklist snd_intel8x0

I also added these lines to the /etc/modprobe.d/alsa-base   file.

# autoloader aliases
install sound-slot-0 /sbin/modprobe snd_usb_audio
#install sound-slot-1 /sbin/modprobe snd_intel8x0

And commented this 
#options snd-usb-audio index=1
#options snd-usb-usx2y index=-2

yeah!!!!!!!!!!!!!!!!!!!

---

### Post by bldninja on 2007-06-21
Thank you for your post, my sound is now working :-)

Dell Inspirion 8600 (Laptop)
Ubuntu 7.04
Internal sound card: Intel I82801DB-ICH4 with Sigmatel STAC9750,51 chip (snd-intel8x0).
PCMCIA sound card: creative Audigy 2 ZS

I got Ubuntu on an Inspiron 8600 with Intel/Sigmatel integrated sound card. The internal soundcard is defect, but Ubunto still used this card for playback insted of my Audigy 2 ZS pcmcia card.

I had no other alternative but turning of the internal card to get the external to work. No option for disable internal card in bios so i had to do something in Ubuntu.

gedit /etc/modprobe.d/blacklist
blacklist snd-intel8x0

gedit /etc/modprobe.d/alsa-base
# options snd-cmipci mpu_port=0x330 fm_port=0x388

Reboot and no sound from internal card, but sound from my Audigy card.

//bld

---

### Post by cfmunster on 2008-03-12
Kick ***! This fix worked for me to set up my Bose Companion 3 USB sound system on Gutsy (7.10). Thanks for the post.

---

### Post by dontcopymusic on 2008-05-08
> **garbage792 said:**
> yeah!!!!!!!!!!!!!!!!!!!

Dude, you made my day!! Thanks!

---

### Post by uppsju on 2008-05-08
> **bldninja said:**
> Thank you for your post, my sound is now working :-)

Dell Inspirion 8600 (Laptop)
Ubuntu 7.04
Internal sound card: Intel I82801DB-ICH4 with Sigmatel STAC9750,51 chip (snd-intel8x0).
PCMCIA sound card: creative Audigy 2 ZS

I got Ubuntu on an Inspiron 8600 with Intel/Sigmatel integrated sound card. The internal soundcard is defect, but Ubunto still used this card for playback insted of my Audigy 2 ZS pcmcia card.

I had no other alternative but turning of the internal card to get the external to work. No option for disable internal card in bios so i had to do something in Ubuntu.

gedit /etc/modprobe.d/blacklist
blacklist snd-intel8x0

gedit /etc/modprobe.d/alsa-base
# options snd-cmipci mpu_port=0x330 fm_port=0x388

Reboot and no sound from internal card, but sound from my Audigy card.

//bld

Thanks, this worked for me on my Dell XPS M1710 as well. Have to sudo before gedit, though.

---

