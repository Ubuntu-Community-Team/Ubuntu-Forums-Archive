---
title: "Inspiron 9300 Mixer Problem"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by jbro on 2007-05-18
Hello all,

I am running Feisty Kubuntu on a Dell Inspiron 9300 and while pretty much everything has worked out of the box, I do experience one small problem with sound mixing. The 9300 has a subwoofer whose volume is controlled by what is shown as the "Master Mono" channel in alsamixer. (It shows the same in GNOME mixer or kmixer -- the mixer itself doesn't matter.) Now, if I adjust the mono master volume through the mixer, everything is fine and I can adjust the subwoofer volume. The problem is that if I use the laptop's multimedia buttons to control volume, they only adjust the Master channel, so the subwoofer has to be adjusted separately via the mixer. It is particularly annoying when you mute, since the master channel mutes and you are left with the subwoofer at normal volume.

Is there a way to configure ALSA so that the Master Volume control will control both the subwoofer and the master channel, thus keeping them synchronized? Fixing this would give me a perfect Feisty install.

Thanks and regards,
jbro

---

### Post by GrejpFrut on 2007-05-18
I have a 9300 and I had this same issue.  You can download this program called keytouch which will map commands to certain keys allowing you to control the PCM volume.  This way you leave the master and mono to a set value and when you press the volume buttons you will simply be controlling the PCM.  Here is a thread that addresses this issue:

[http://ubuntuforums.org/showthread.php?t=199579]("http://ubuntuforums.org/showthread.php?t=199579")

Good luck

---

### Post by jbro on 2007-05-18
Grejpfrut,

Thanks for the response. I had seen that thread, but didn't want to install keytouch just yet. I've done some looking around and I think that this should be doable through the asound.conf or .asoundrc files so that it requires no extra software and is transparent to applications. I've tried with the following .asoundrc file, but no luck:
```
pcm.!default {
    type            plug
    slave.pcm       "softvol"   #make use of softvol
}

pcm.softvol {
    type            softvol
    slave {
        pcm         "dmix"      #redirect the output to dmix (instead of "hw:0,0")
    }
    control {
        name        "PCM"       #override the PCM slider to set the softvol volume level globally
        card        0
    }
}
```

I'll have to try another round with the ALSA docs to see if I can't get this going just by proper configuration.

Thanks and regards,
jbro

---

### Post by jbro on 2007-05-18
OK, I solved it without resorting to extra software or even cryptic asound.conf settings. In Feisty with KDE KMix you can solve the problem by editing ~/.kde/share/config/kmixrc and inserting the line ```
MasterMixerDevice=<device>
``` where <device> is the number of the device you want KMix to control as the master. I couldn't find a direct way to find out which <device> number corresponded to which control, so I used ```
dcop kmix Mixer0 setMute <N> true
``` and varied <N> until I saw that the control I needed was muted. It is probably best to edit the config file while you are not logged into KDE (i.e. in a console.)

Thanks and regards,
jbro

---

### Post by johnnyzazza on 2007-06-05
ADJUSTING DIFFERENT SOUND SOURCES SIMULTANEOUSLY UNDER GNOME:
The volume for PCM Master and LFE (for example) can be adjusted simultaneously by launching [Sound Preferences] from the [Control Panel].
Under [Default Mixer Tracks], highlight all the items that you wish to be controlled simultaneously (for example, highlight Master, PCM, and LFE). Click [Close] to confirm you choices.
NOTE: LFE corresponds to your laptop's subwoofer.

---

### Post by jstn128 on 2007-06-13
> **johnnyzazza said:**
> ADJUSTING DIFFERENT SOUND SOURCES SIMULTANEOUSLY UNDER GNOME:
The volume for PCM Master and LFE (for example) can be adjusted simultaneously by launching [Sound Preferences] from the [Control Panel].
Under [Default Mixer Tracks], highlight all the items that you wish to be controlled simultaneously (for example, highlight Master, PCM, and LFE). Click [Close] to confirm you choices.
NOTE: LFE corresponds to your laptop's subwoofer.


This works great!  And since I subscribe to the KISS method, I love it.

Thank you so much.

---

