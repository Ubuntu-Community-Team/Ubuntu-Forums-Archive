---
title: "Multiple users at one sound card with ALSA"
date: 2011-12-01
forum: Multimedia Software
---

### Post by Shockrates on 2011-12-01
There are situations where multiple Xsessions are  running by different users at the same time on one workstation. Often on  environments without a sound server like Pulseaudio or ESD is that one  user is blocking one output device so that the other users have to work  without sound. Also if a music daemon like MPD runs over its own user,  one user has *exclusive* access to the sound device by the rule "first come, first served".

A possible three-steps solution using plain ALSA is based on the dmix plugin:             
                          dmix  plugin is mostly known for its ability to allow multiple processes use  only one sound device (which has no hardware mixing feature)  simultaneously via software mixing. Less known is that dmix also makes  it possible to share one sound output device between different users.

**1. _Put dmix into your asound.conf_**

A relevant part of ***/etc/asound.conf***:


```
pcm.!default {
    type plug
    slave.pcm "dmixer"
}

pcm.dsp0 {
    type plug
    slave.pcm "dmixer"
}

pcm.dmixer {
    type dmix
    ipc_key 1024                 # the key must be unique
    ipc_key_add_uid 0
    ipc_perm 0666                # permissions - octal notation
    slave {
        pcm "hw:0,0"
        period_time 0
        buffer_time 0
        period_size 2048
        buffer_size 32768
        rate 44100
    }
}

ctl.dmixer {
    type hw
    card 0
}
```**ipc_key**, **ipc_key_add_uid** and **ipc_perm**  are the less popular options for the sharing of the software mixer  (dmix) also between the users. Important is that if using several sound  cards you have to choose unique ipc_keys.

**2. _Set ALSA as default in /etc/libao.conf_** 
That is done with the following entry (change the existing entry if one exists already):
```
[COLOR=#007800]default_driver[/COLOR]=alsa09
```That will make most ALSA compatible applications use ALSA.

**3. _Deactivate & Blacklist the OSS module_**

Applications as flash player in browsers use OSS, do not give a damn  about the asound.conf entries and block the whole device. We prevent  that by deactivating and blacklisting the OSS module.

Edit /etc/modprobe.d/blacklist.conf and type in:
```
blacklist snd_pcm_oss
```Also,some programs which rely on OSS can be still used with an OSS wrapper tool provided by ALSA (aoss):
```
sudo apt-get install alsa-oss
```Used as: ```
aoss yourcommand
```**_NOTICE_:** To make sure that the approach works you have  to  take care that no application is bypassing the dmix plugin and is  using  the hardware device directly. In some cases you will have to set  the  dmix device as output device to be used for an application  explicitly.
[B]
P.S.:[/B] Note, however, software mixing might/will cause a  quality loss of the sound. At everyday work with some common desktop  speakers you won't notice that. One of the reasons for quality loss is  for example the possibly required resampling of your audio to the rate  specified in asound.conf. For serious working with audio or playback  over high-end speakers you will anyway have bought some high-quality  sound interface which allows hardware mixing in conjunction with JACK  (and doubtful you will need share the device on serious work at all).

---

