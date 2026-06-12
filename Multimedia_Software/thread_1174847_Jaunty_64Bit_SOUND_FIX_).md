---
title: "Jaunty 64Bit: SOUND FIX :)"
date: 2009-05-31
forum: Multimedia Software
---

### Post by Fluffy13 on 2009-05-31
After literally like two weeks with only sound in my headphones, i finally have full working sound from headphones, mic, and speakers. Hopefully this fix can help others!

System: Jaunty 9.04 64Bit
Model: Gateway FX6831

Ok so first we need to open up out alsa base config file:

> 
sudo gedit /etc/modprobe.d/alsa-base.conf
Mine looks like this. We are focusing on the end of the file.

> 
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
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
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

#options snd-hda-intel model=laptop enable=1 index=0
#options snd-hda-intel enable_msi=1

options snd-hda-intel model=stac92xx enable=1 index=0
options snd-hda-intel enable_msi=1

#options snd-hda-intel model=hp-m4 enable=1 index=0
#options snd-hda-intel enable_msi=1
The last three chunks, you will notice only the center two lines are uncommented. I tried so many fixes that as i went along, i just uncommented them so i would remember what i tried. 

What finally worked is this. Copy the following into your file:

> 
#options snd-hda-intel model=laptop enable=1 index=0
#options snd-hda-intel enable_msi=1

#options snd-hda-intel model=stac92xx enable=1 index=0
#options snd-hda-intel enable_msi=1

options snd-hda-intel model=hp-m4 enable=1 index=0
options snd-hda-intel enable_msi=1Notice that now the second set is commented off, and the last is not. Save this and restart your computer (i did).

Now we open the config file again, and change it back to this:

> 
#options snd-hda-intel model=laptop enable=1 index=0
#options snd-hda-intel enable_msi=1

options snd-hda-intel model=stac92xx enable=1 index=0
options snd-hda-intel enable_msi=1

#options snd-hda-intel model=hp-m4 enable=1 index=0
#options snd-hda-intel enable_msi=1Now go into your volume control settings, and change your playback device to OSS while some music is playing. After a few seconds, change it back to the Alsa device. Viola, sound is working!

Now im a newb to linux, only been using it for about two years. I have no idea how audio works in linux, and i dont know why this worked for me. All i know is i did nothing else in the past week, and this was something i stumbled upon. I had added the hp-m4 lines based on a tip in another thread i found today. When it didnt work, i swapped it back. My speakers didnt work, so i tried OSS...again. They didnt work, and when i went back to alsa they did.

Who knows why, but maybe it helps someone :popcorn:

---

### Post by redenex on 2009-05-31
Thanks for sharing, it might help someone I am sure!

But no, not helping my issue! For me, the sound cuts off after a few seconds of playing. The funny thing is that, if I am on Pidgin and say I type something and te system beeps, the sound (totem) starts working again for a few more seconds!!!

---

### Post by Fluffy13 on 2009-05-31
Thats certainly strange....

What software are you using? Maybe you have more then one program fighting for access to the card? Does/Did your sound work on another version or OS? Try and weed out the possibility of a hardware issue.

---

### Post by redenex on 2009-05-31
> **Fluffy13 said:**
> Thats certainly strange....

What software are you using? Maybe you have more then one program fighting for access to the card? Does/Did your sound work on another version or OS? Try and weed out the possibility of a hardware issue.
There is no trouble with my sound card, it works well on Windows Vista. 

The good part is that earlier I had no sound, but now atleast I have it.

---

### Post by Fluffy13 on 2009-05-31
I think intermediate sound might bother me more then no sound lol. Hopefully someone can help, it's certainly above my pay grade

---

### Post by Fluffy13 on 2009-06-01
My heart was broken a little while ago when i restarted and it stopped working. Will report back if i can fix it again :(

---

### Post by redenex on 2009-06-01
Good luck with that, I am waiting too! :D

---

### Post by Fluffy13 on 2009-06-02
repeating the steps fixed it....till next reboot i assume. Eh...

---

### Post by redenex on 2009-06-02
For me, I can play songs, but it get stuck after a while. I to to the terminal, press backspace so that the system beep works, and immediatly after that the sound returns for another few minutes! Only problem is that I have to keep pressing the backspace to generate the beep.

---

### Post by Fluffy13 on 2009-06-03
I'm really tempted to go back to Intrepid Ibex where everything worked as its supposed to hehe.

---

