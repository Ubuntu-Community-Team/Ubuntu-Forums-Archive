---
title: "I don't have sound now."
date: 2006-10-01
forum: Multimedia &amp; Video
---

### Post by Nesha on 2006-10-01
I tried to set up my sound card so I can have sound on my VMware player.
I found one manual and it goes like this:    1. We need to install libesd-alsa0 so
      Code:
      sudo apt-get install libesd-alsa0
   2. We need to create /etc/asound.conf, so
      Code:
      sudo gedit /etc/asound.conf
      Insert into it:
      Code:
      pcm.card0 {
      type hw
      card 0
      }

      pcm.!default {
      type plug
      slave.pcm "dmixer"

      }


      pcm.dmixer {
      type dmix
      ipc_key 1025
      slave {
      pcm "hw:0,0"
      period_time 0
      period_size 2048        #1024
      buffer_size 32768        #4096
                              #periods 128
      rate 48000                #44100
      }
      bindings {
      0 0
      1 1
      }
      }
   3. We need to change /etc/esound/esd.conf contents so:
      Code:
      sudo mv /etc/esound/esd.conf /etc/esound/esd.conf_backup
      sudo gedit /etc/esound/esd.conf
      Insert into it:
      Code:
      [esd]
      auto_spawn=1
      spawn_options=-terminate -nobeeps -as 2 -d default
      spawn_wait_ms=100
      # default options are used in spawned and non-spawned mode
      default_options=
   4. Now You need to change ubuntu sound server to alsa (you can leave it ESD but better use alsa because it has better sound handling):
      Code:
      gstreamer-properties
      Change both (in the Audio Tab not the Video) from ESD to ALSA so it looks just like the picture:

All that's left now is to restart your computer (after restart you must hear sound) to enable these changes. Also configure XMMS or Beep-media-player (or any player) to use ALSA instead of eSound/ESD. If you hear a strange sound, just change everything back to ESD. If everything worked correctly, now Audacity & Skype will work normally and all the program will play sound using either Alsa or ESD.

    Correct beep-media-player configuration:

* If you couldn't play any sounds using ALSA then your /etc/asound.cond & /etc/esound/esd.conf needs some more advanced tweaking (or your sound card just won't support it).


If I couldn't support it, how can I get it back.

---

