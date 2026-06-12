---
title: "AC3 via analog-plugs: Only Front speakers have sound"
date: 2008-05-14
forum: Mythbuntu
---

### Post by joe0815 on 2008-05-14
Hello,

I tried now everything I found with google. But there is no 5.1 sound available with an 5.1 DVD (german) and the Internal player as well as with live TV via DVB-C.

alsamixer seems to be set correctly because speaker-test works fine.

The only thing which seems to be missing is a correct setup in /etc/asound.conf. But this is what I don't know how to do it.

Does anybody have a 5.1 analog asound.conf vor me? Or is this a file which is set for every soundcard different? If so, how can I start building up my own asound.conf?

Perhaps anyone can help me a little bit.

Regards
Jo

---

### Post by volkswagner on 2008-05-14
How is your sound card connected to speakers/stereo?

What is the output of 

```
aplay -l
```

run the following to see if you need to unmute.

```
alsamixer
```

Check /var/log/mythtv/mythfrontend.log for errros.

---

### Post by joe0815 on 2008-05-14
Hello,

thanks for the fast answer. But I'm not at home at the moment. I'll send it this evening.

But the soundcard is connected with the three plugs from my amplifier. This one is not connected via spdif or optical or anything like that.

As I said, the rest I'll send this evening. Let me know if other informations are relevant.

Regards
Jo

---

### Post by joe0815 on 2008-05-14
Hello,

here are some outputs:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: CK8S [NVidia CK8S], device 0: Intel ICH [NVidia CK8S]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8S [NVidia CK8S], device 2: Intel ICH - IEC958 [NVidia CK8S - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

aplay -L
default:CARD=CK8S
    NVidia CK8S, NVidia CK8S
    Default Audio Device
front:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    Front speakers
surround40:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    4.0 Surround output to Front and Rear speakers
surround41:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=CK8S,DEV=0
    NVidia CK8S, NVidia CK8S
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
null
    Discard all samples (playback) or generate zero samples (capture)

And my mixer settings:
Hm, can you tell me how to give an output for these settings?

And there are no errors in mythfrontend.log. Only no Sound

regards
Jo

---

### Post by volkswagner on 2008-05-14
Try to play a DVD, not through myth.  Try mplayer or xine.  Do you get 5.1 outside of myth?

In mythtv frontend setup, do you have 5.1 or stereo selected for max channels?  Utilities/setup>setup>General, page 3.

---

### Post by laga on 2008-05-14
Did you tell MythTV to output 5.1 audio? You might also have to set the audio device.

---

### Post by joe0815 on 2008-05-14
Hello,

when I tell mythtv in the mythfrontend configuration to play 5.1 sound only the front speakers have sound. The center and rear speakers are quiet. But the sound arrangement seems to be correct there is only no volume to the speakers even if I set them in alsamixer to 100% and unmute them.

mplayer sounds well with hwac3 but has no menu. Therefore I don't like to use it.

The audio devices are set to ALSA:default. If I select ALSA:surround51 no sound at all I have.

Any further hints?

Thanks and regards
Jo

---

### Post by joe0815 on 2008-05-14
Hello,

one thing is really strange. On the same PC I have linvdr installed. And there sound works great. Stereo and 5.1
So whats the problem there with mythbuntu? Is this a bug in 8.04?

Regards
Jo

---

### Post by joe0815 on 2008-05-14
Hello,

another question. I don't really wanna learn alsa programming. Is here anybody who uses 5.1 analog sound with a nvidia sound card? Then could you please post your settings:

alsa-base module list
/etc/asound.conf or .asoundrc
/var/lib/alsa/*

Would be really great.

Thanks in advance
Jo

---

### Post by joe0815 on 2008-05-14
Hello a last time now,

I found the solution in the mythtv-users mailing list. I don't understand how it works - alsa is really strange - but it works for me:

Just use this as asound.conf:

pcm.dmixs51 {
        type dmix
        ipc_key 1024
        ipc_key_add_uid false # let multiple users share
        ipc_perm 0660 # IPC permissions (octal, default 0600)
        slave {
                pcm "hw:0,0"
                rate 48000
                channels 6
                period_time 0
                period_size 1024
                buffer_time 0
                buffer_size 4096
        }
        bindings {
                0 0
                1 1
                2 4
                3 5
                4 2
                5 3
        }
}

pcm.!default {
        type plug
        slave {
                pcm "dmixs51"
        }
}

pcm.asym51 {
           type asym
           playback.pcm "dmixs51" 
           capture.pcm "hw:0,0" # this might be "dsnoop:0"
}

pcm.dsp0 {
         type plug
         slave.pcm "asym51"
}


Perhaps someone finds this usefull,

Regards and good night,
Jo

---

