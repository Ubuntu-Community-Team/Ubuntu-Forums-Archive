---
title: "ATI HDMI sound device replacing soundcard"
date: 2008-09-19
forum: Multimedia Software
---

### Post by v4npro on 2008-09-19
I'm trying to get my soundcard to be device 0 but everytime its the ati hdmi sound.  Everything works, but when the ati sound is at 0 then i can't get my usb microphone to work with ventrilo through wine. How can i disable the ati sound or set my soundcard to be default always.  Also when I use,

 pcm.!default {
         type asym
         playback.pcm {
                 type plug
                 slave.pcm "hw:0,0"
         }
         capture.pcm {
                 type plug
                 slave.pcm "hw:1,0"
         } 
 }

before when my sound card was device 0 everything works great, but now its device 3 so i changed the playback to hw:3,0 and everything looks fine in ventrilo/wine, but now when I test it i don't hear people, so I checked it out in System, Pref., sounds, I get error with the playback.  Deleteing the .asoundrc makes the sounds test work but ventrilo/wine not work all because my soundcard an't device 0.


Thanks

---

### Post by markbuntu on 2008-09-19
You can force the order of your sound cards by adding lines like these to the end of your etc/modprobe.d/alsa-base file:

options snd-atiixp index=0
options snd-cmipci index=1
options snd-hda-intel index=2
options snd-usb-audio index=3

Of course, what you put there depends on your sound cards but this will make the order of your sound cards permanent. My ATI HDMI card is listed as snd_hda_intel in the above lines so I have indexed it to device 2 and that is how it always shows up.

---

### Post by v4npro on 2008-09-19
Ok, I will try that and reply back thanks.!!!

---

### Post by v4npro on 2008-09-19
When I do aplay -l it's still showing my sound card as the third one down.  I need it to be the first on the list, card 0 not card 3.  Any ideas on how to do this? Thanks

---

### Post by markbuntu on 2008-09-20
You need to restart alsa or reboot for that to take effect.

---

### Post by v4npro on 2008-09-20
Yeah I did, i set it to snd-oxygen index=0 save, then reboot and then my soundcard doesnt get picked up at all.. .... oh well...  I'll just keep trying with things.. THanks for the help though!! :P

---

### Post by markbuntu on 2008-09-21
You may be using the wrong name for your card in that line. I wish I could remember how I found the names of the codecs for the cards. I think it was something like:

cat /proc/asound/card0/codec#* | grep Codec

Changing the card0 to card1 etc for each card. That should give you the names you need for the index line.

---

