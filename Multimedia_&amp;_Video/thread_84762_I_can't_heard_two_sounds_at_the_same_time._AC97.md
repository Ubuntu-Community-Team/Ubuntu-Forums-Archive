---
title: "I can't heard two sounds at the same time. AC97"
date: 2005-10-31
forum: Multimedia &amp; Video
---

### Post by Lantius on 2005-10-31
I am trying to resolve this famous problem. 

I have AC97 it is integrate in mother board. 
--
root@Zape:/home/xenon# lspci | grep AC97
0000:00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 20)
---

I looked for and I tryied this : 
> 
killall esd

> sudo aptitude install libesd-alsa0 alsa-oss

I changed file /etc/asound.conf with it : 

> # .asoundrc for use with ALSA and the dmix plugin, for ALSA-level
# software mixing across all apps.
#
# [http://alsa.opensrc.org/index.php?page=AlsaSharing](http://alsa.opensrc.org/index.php?page=AlsaSharing)
# [http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)

pcm.dmix0 {
    type dmix
    ipc_key 219345           # any unique number here
    slave {
            pcm "hw:0,0"
            period_time 0
            buffer_time 0
            period_size 2048    # jm: much smoother than 1024/8192!
            buffer_size 32768
            rate 48000
    }

    bindings {
        0 0   # from 0 => to 0
        1 1   # from 1 => to 1
    }
}

pcm.dsp0 {
  type plug
  slave.pcm "dmix0"
}

# this makes native ALSA apps default to using dmix
pcm.!default {
  type plug
  slave.pcm "dmix0"
}

ctl.dsp0 {
  type hw
  card 0
}

ctl.!default {
  type hw
  card 0
}


and I changed  > default_driver=esd  to > default_driver=alsa
in /etc/libao.conf

And I selected Alsa in twice options in selector multimedia.

I rebooted, But this don't Go. 

Other friend told me that I should change /etc/modprobe.d/alsa-base adding other line in the end with > snd-via82xx index=0 dxs_support=1

and using > update-modules after>  apt-get install modutils

But . I didn't get to heard two sound at the same time ...

Someone know what is the solution ?

---

### Post by suoko on 2005-11-14
same problem here.
Alsa dmix doesn't work with AC97

---

### Post by suoko on 2005-11-14
I found out what the problem is:

ALSA DMIX only works with applications which support ALSA or aoss. It doesn't work with applications which support OSS only.(It might not be a technically correct explanation but it gives you an idea)


Applications which support DMIX:

- rhythmbox
- totem
- vlc
- mplayer
- gaim
- xine
- xmms
- alsaplayer
- gnome-sound-recorder (guess so)
- realplayer (through aoss)
- avidemux (through aoss - bad sound)
- flash player in firefox (through aoss - modify /etc/mozilla-firefox/mozilla-firefoxrc to FIREFOX_DSP="aoss")


Applications which don't support DMIX:

- skype 
- gizmo
- audacity
- java plugin
- flash player in epiphany 

WHAT IS aoss?
aoss lets applications written for OSS use ALSA output, therefore it works with DMIX.

HOW TO USE aoss?
EXAMPLE: aoss realplay

---

