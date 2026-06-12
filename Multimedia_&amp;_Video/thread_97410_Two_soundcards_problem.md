---
title: "Two soundcards problem"
date: 2005-11-30
forum: Multimedia &amp; Video
---

### Post by jrincon87 on 2005-11-30
Hey, I have two soundcards in my computer. The one I have the speakers plugged into, is the second one (that would be hw:1,0). Anyway, I went to System->Preferences->Sound and indicated the second soundcard to be the default one. And everything sounds through the second card except the MIDI (timidity for example) and now the flash animations too (at least when I play one in Firefox. I haven't tried playing them alone). These two things are sounding through the first soundcard. What should I do to make ABSOLUTELY everything to sound through the second card?
(My output is ALSA).
Thanks.

---

### Post by arnieboy on 2005-12-01
[QUOTE=jrincon87]Hey, I have two soundcards in my computer. The one I have the speakers plugged into, is the second one (that would be hw:1,0). Anyway, I went to System->Preferences->Sound and indicated the second soundcard to be the default one. And everything sounds through the second card except the MIDI (timidity for example) and now the flash animations too (at least when I play one in Firefox. I haven't tried playing them alone). These two things are sounding through the first soundcard. What should I do to make ABSOLUTELY everything to sound through the second card?
(My output is ALSA).
Thanks.[/QUOTE]
try this:
[http://doc.gwos.org/index.php/Multisounds/](http://doc.gwos.org/index.php/Multisounds/)

---

### Post by jrincon87 on 2005-12-01
Thanks. That's exactly what I needed.

---

### Post by jrincon87 on 2005-12-01
Hey. It seems that I sang victory too soon. That didn't solve my problem. The same thing keeps happening.

---

### Post by arnieboy on 2005-12-01
[QUOTE=jrincon87]Hey. It seems that I sang victory too soon. That didn't solve my problem. The same thing keeps happening.[/QUOTE]
for flash sound try the following howto. if flash sound is redirected thru aoss, it shd come thru ur PCI sound card.
[http://ubuntuforums.org/showthread.php?t=75237](http://ubuntuforums.org/showthread.php?t=75237)
for midi play, u need to tell me what u added to your ~/.bashrc
or did u use automatix?

---

### Post by jrincon87 on 2005-12-01
Hey. I followed all the steps and all I achieved is to let Ubuntu without system sounds and that the GStreamer sounds choppy (or gappy... I can't remember the expression, bad anyways) through AmaroK, now I have to use the Xine engine. The flash animations still sound through the other card (despite I changed the "card" value from 0 to 1 in the asound.conf file). And for MIDI... ~/.bashrc? I have no idea. No, I haven't use Automatix yet, because I tried it once and I achieved too is letting Ubuntu without system sounds, but the MIDI still played through the first soundcard.
My asound.conf looks like this:

> # Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 1===> *This is the only thing I modified (from 0 to 1)*
}

# Allow mixing of multiple output streams to this device
pcm.dmixer {
     type dmix
     ipc_key 1024
     slave.pcm "snd_card"
     slave {
          # This stuff provides some fixes for latency issues.
          # buffer_size should be set for your audio chipset.
          period_time 0
          period_size 1024
          buffer_size 4096
          # rate 44100
     }

     bindings {
          0 0
          1 1
     }
}

# Allow reading from the default device.
# Also known as record or capture.
pcm.dsnooper {
     type dsnoop
     ipc_key 2048
     slave.pcm "snd_card"

     bindings {
          0 0
          1 1
     }
}

# This is what we want as our default device
# a fully duplex (read/write) audio device.
pcm.duplex {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

###################
# CONVERSION PLUG #
###################
# Setting the default pcm device allows the conversion
# rate to be selected on the fly.
# duplex mode allows any alsa enabled app to read/write
# to the dmix plug (Fixes a problem with wine).

pcm.!default {
     type asym
     playback.pcm "dmixer"
     capture.pcm "dsnooper"
}

########
# AOSS #
########
# OSS dsp0 device (OSS needs only output support, duplex will break some stuff)
pcm.dsp0 {
     type plug
     slave.pcm "dmixer"
}

# OSS control for dsp0 (needed?...this might not be useful)
ctl.dsp0 {
     type plug
     slave.pcm "snd_card"
}

# OSS control for dsp0 (default old OSS is mixer0)
ctl.mixer0 {
     type plug
     slave.pcm "snd_card"
}


Am I lacking of something?

Why is this such a problem? I mean, this is Linux, and as far as I have experienced, everything can be made, solved or improved. How come the sound be such a problem? Can't I have all together (system sounds, MIDI, Flash through the right card, etc.)? Is there a distro that does all these things for you, or does it always has to be a headache?
Thanks.

---

