---
title: "How do I configure sound cards ?"
date: 2006-08-31
forum: Multimedia &amp; Video
---

### Post by dw5437 on 2006-08-31
dw5437@dw5437-desktop:~$ cat /proc/asound/modules
0 snd_hda_intel
1 snd_emu10k1
dw5437@dw5437-desktop:~$ sudo gedit /etc/modprobe.d/alsa-base

# autoloader aliases
install sound-slot-0 modprobe snd-card-0
install sound-slot-1 modprobe snd-card-1
install sound-slot-2 modprobe snd-card-2
install sound-slot-3 modprobe snd-card-3
install sound-slot-4 modprobe snd-card-4
install sound-slot-5 modprobe snd-card-5
install sound-slot-6 modprobe snd-card-6
install sound-slot-7 modprobe snd-card-7

# Cause optional modules to be loaded above generic modules
install snd modprobe --ignore-install snd $CMDLINE_OPTS && { modprobe -Qb snd-ioctl32 ; : ; }
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe -Qb snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe -Qb snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe -Qba snd-seq-midi snd-seq-oss ; : ; }

# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { modprobe -Qb snd-emu10k1-synth ; }
install snd-via82xx modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { modprobe -Qb snd-seq ; }

# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 modprobe --ignore-install saa7134 $CMDLINE_OPTS && { modprobe -Qb saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options snd-bt87x index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2

I only want the soundblaster audigy zs2 working. not the Intel. How do I accomplish this ? Soundblaster is card 1 and intel is card 0.
Any help appreciated.

---

### Post by sebastfr on 2006-09-01
Edit /etc/asound.conf and replace/add the default settings:

pcm.!default {
         type plug
            slave {
                pcm "dshare"
                channels 4
            }
            ttable.0.0 1
            ttable.1.1 1
#            ttable.0.2 1   #uncomment for 4-speaker configuration
#           ttable.1.3 1    #same comment
}


pcm.dshare {
    type dmix
    ipc_key 2048
    slave {
        pcm "hw:1"
        rate 44100
        period_time 0
        period_size 1024
        buffer_size 8192
        channels 2
#        channels 4    # uncomment for 4-speaker conf.
    }
    bindings {
        0 0
        1 1
#        2 2   #uncomment for 4-speaker conf
 #       3 3   # and same again.
    }

}


Save the file and try play some sound again (restart the player though).

Seb

---

### Post by dw5437 on 2006-09-01
Ok, I tried your suggestion and now I get errors when trying to play a cd. What I done was cut and pasted your list into the file you told me to edit. Maybe that was a mistake. I couldnt see any sound card options in the file you suggested. I am definately not a Linux guru, so maybe someone can explain it a little simpler. Thanks for the info.

---

### Post by Voodoonix on 2007-06-02
i recently installed a game on ubuntu the game starts good but there is no sound,  i have sound everywhere else in ubuntu just not in the game is there any way i can fix this? my sound card is Soundblaster Live!

---

