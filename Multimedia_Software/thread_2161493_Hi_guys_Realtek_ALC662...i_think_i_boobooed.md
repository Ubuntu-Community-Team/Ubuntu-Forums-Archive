---
title: "Hi guys Realtek ALC662...i think i boobooed"
date: 2013-07-10
forum: Multimedia Software
---

### Post by Furis on 2013-07-10
Alrighty finally got all the things done they wanted in the readme. I had to manually install the hd codexs...on the part where i'm suppose to edit the /etc/modules.conf file....but there is not modules config file there. i have a /etc/modules.swp file is that the one i edit?? i have a modprobe.conf but it's in /lib/fglrx so figured this would be the wrong one to edit. any guesses what this file looks like inside so i know what i'm lookin at when i find it??? says i gotta copy paste some crap in the bottom of it like this

Step 4. Edit your /etc/modules.conf or conf.modules depending on the distribution
     (Please refer to the attached modules.conf)
     
        snd-xxxx is the card ID.

    -- Azalia controller --ALC880 ALC882 ALC260 ALC262 ALC883 ALC885 ALC888
       --- Intel ICH6 ICH7 ---------
               snd-hda-intel
           --- ATI chipset -----
           snd-atiixp

        -- AC97 controller --ALC655 ALC650 ALC250 ALC255 
           --- Intel ICH6 ICH7 , SiS 7012 and NVidia----------
               snd-intel8x0
           --- Via8233 Via686a  -------------------------------    
           snd-via82xx
           --- ATI Chipset  -------------------------------
           snd-atiixp

        Copy and paste this to the bottom of your /etc/modules.conf or /etc/modprobe.conf file.
    # ALSA portion
          alias char-major-116 snd
          alias snd-card-0 snd-xxxx     
        # OSS/Free portion
          alias char-major-14 soundcore
          alias sound-slot-0 snd-card-0
        # card #1
          alias sound-service-0-0 snd-mixer-oss
          alias sound-service-0-1 snd-seq-oss
          alias sound-service-0-3 snd-pcm-oss
          alias sound-service-0-8 snd-seq-oss
          alias sound-service-0-12 snd-pcm-oss

Step 5. reboot your machine
*not this isn't the exact readme file from it but they say the same thing minus the models

---

