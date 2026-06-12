---
title: "A8N-SLi Nforce4 5.1 Surround Sound"
date: 2006-06-03
forum: Multimedia &amp; Video
---

### Post by MattToner on 2006-06-03
Hi All,

ive been using Ubuntu since 5.10.

Currently have got a new motherboard as per title, and waited to get the new 6.06 version (for the last 4 months ive just been running windows)

The problem i have is that i cannot get my 5.1 speakers working, after reading over 100 threads regarding Asla mixer and getting 5.1 working, all i can get is the front a rear speaker working (rears are only a duplicate of the fronts)

I have just installed a fresh ubuntu and have nothing on here at the moment as i NEED to get the surround settings working.

I use my PC a lot for listening to music and without the Centre and Sub working i have no bass at all on any music.

System specs are;

AMD X2 3800+
A8N-SLi Deluxe (Nforce4)
2.5gb DDR Ram
Nvidia 6600GT

On Alsa Mixer it displays this;

Card: Nvidia CK804
Chip: Realtek ALC850 rev 0

Hope someone out there has an answer

Regards

Matt

---

### Post by MattToner on 2006-06-03
bumpo

---

### Post by MattToner on 2006-06-05
c'mon someone must know, this is the only thing keeping me in windows :(

---

### Post by rainefan on 2006-07-04
same problem here...

---

### Post by MiKuS on 2006-07-04
and me.

i've been trying over at another forum - 

[http://www.nvnews.net/vbulletin/showthread.php?p=927758#post927758](http://www.nvnews.net/vbulletin/showthread.php?p=927758#post927758)

---

### Post by onlysolution on 2006-07-07
have you tried using the advice at this thread? [http://www.ubuntuforums.org/showthread.php?t=207366&highlight=surround+sound]("http://www.ubuntuforums.org/showthread.php?t=207366&highlight=surround+sound")

---

### Post by MiKuS on 2006-07-08
i did try alsamixer, yes. 

for about 8 hours all up

---

### Post by Olympeus on 2006-07-08
I just started using Ubuntu but I'm currently running into the exact same problem. I hope someone has a solution for this?

---

### Post by enhancer2000@hotmail.com on 2006-09-10
[http://www.flaterco.com/kb/audio.html](http://www.flaterco.com/kb/audio.html)
[http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml](http://www.cse.ohio-state.edu/~bondhugu/alsamch.shtml)
Check these out.  This is what I used.

---

### Post by eje_s on 2008-04-10
I'm using Ubuntu hardy x64 (8.04) and I have struggled with my Asus Nforce 4 for a while now.
Card: NVidia CK804
Chip: Realtek ALC850 rev 0

The goal was to have 5.1 sound, stereo upmixing, and recording at the same time. Also, applications should still be able to share the sound card.

After ~week(!) I succeeded with my goals. The solution I finally found was using Alsa's dmix and some other plugins by looking at:
[http://alsa.opensrc.org/index.php/How_to_use_softvol_to_control_the_master_volume](http://alsa.opensrc.org/index.php/How_to_use_softvol_to_control_the_master_volume)

Oh, did I say that I can use venrilo in wine and have sound and recording at the same time as playing sound in other applications? Well I can.
Just use direct sound for output and wave for input.

My mixer settings:
All _speaker_ controls unmuted and set to the same level (ie -12 for all except pcm=0).
surround mode: Independent
Front mic on or off, depending on if you use the front jacks or not.
mic2 selected.
Mic boost on or off (on in my case).
IEC958 off.
Channel mode = 6
Duplicate front off
External amplifier off
Mic as capture device and capture enabled.

Current problems with my setup:
1) MPD wants to run as my own user and not as 'mpd' to be able to use the soundcard. I have set it to use my upmixing device by the way. This is not a problem in my case, and might just be some setting I have fiddled with.

2) The alsa main and pcm sound controls only control the left and right speaker. There are other controls for the rest, but in ubuntu only one control can be controlled by for example the mute key.

I don't have any ~/.asoundrc btw. Now to the point.
My working /etc/asound.conf follows:

```


#-------------------------------
#  Main hardware control
#-------------------------------

pcm.nforce {
    type hw
    card 0
    device 0
    channels 6
    rate 48000
    format "S16_LE"
}

pcm.softmixer {
    type dmix
    ipc_key 1024
    ipc_key_add_uid false
    ipc_perm 0660
    slave {
        pcm nforce
        format "S16_LE"
        channels 6
	rate 48000
        period_time 0
        period_size 1024
        buffer_size 5120
    }
    bindings {
        0 0
        1 1
        2 2
        3 3
        4 4
        5 5
    }
}

#-------------------------------
#  Recording
#-------------------------------

pcm.recording {
    type        dsnoop
    ipc_key     2589
    slave {
        pcm     "hw:0,0"
        format  "S16_LE"
    }
}

#-------------------------------
#  Upmix
#-------------------------------
# upmix stereo to 5.1
pcm.upmix {
    type        route
    slave.pcm   "softmixer"
    slave.channels    6
    ttable {
        0.0    1
        0.2    0.75
	0.4    0.5
        1.1    1
        1.3    0.75
	1.4    0.5
    }
}

pcm.upmix40 {
    type        route
    slave.pcm   "softmixer"
    slave.channels    6
    ttable {
        0.0    1
        1.1    1
        2.2    1
        3.3    1
	0.4    0.5
	1.4    0.5
    }
}

pcm.upmix41 {
    type        route
    slave.pcm   "softmixer"
    slave.channels    6
    ttable {
        0.0    1
        1.1    1
        2.2    1
        3.3    1
	0.4    0.5
	1.4    0.5
	4.5    1
    }
}

pcm.upmix50 {
    type        route
    slave.pcm   "softmixer"
    slave.channels    6
    ttable {
        0.0    1
        1.1    1
        2.2    1
        3.3    1
	4.4    1
    }
}

#-------------------------------
#  Downmix
#-------------------------------

pcm.downmix71 {
    type        route
    slave.pcm    "softmixer"
    slave.channels    6
    ttable {
        0.0    0.67
        1.1    0.67
        2.2    0.67
        3.3    0.67
        4.4    1
	5.5    1
        6.0    0.33
        6.2    0.33
        7.1    0.33
        7.3    0.33
    }
}

#-------------------------------
#  Overwrite existing devices
#-------------------------------

pcm.!default {
    type           asym
    playback.pcm   "plug:upmix"
    capture.pcm    "plug:recording"
}

ctl.!default {
    type hw
    card 0
}

pcm.!surround40 {
    type         plug
    slave.pcm    "upmix40"
}

pcm.!surround41 {
    type         plug
    slave.pcm    "upmix41"
}

pcm.!surround50 {
    type         plug
    slave.pcm    "upmix50"
}

pcm.!surround51 {
    type        plug
    slave.pcm    "softmixer"
}

pcm.!surround71 {
    type         plug
    slave.pcm    "downmix71"
}

pcm.dsp0 {
    type         plug
    slave.pcm    "softmixer"
}

```

Hopes this helps a lot of people.

---

### Post by ciccioermeglio on 2008-04-27
eje_s i have a dfi lanparty ut nforce 4 with a realtek alc850 and i use ubuntu 8.04 amd64. Can you send me your configuration files? I tried to create and edit asound but only works 2 of 6 speaker...

---

### Post by ciccioermeglio on 2008-04-28
> **ciccioermeglio said:**
> eje_s i have a dfi lanparty ut nforce 4 with a realtek alc850 and i use ubuntu 8.04 amd64. Can you send me your configuration files? I tried to create and edit asound but only works 2 of 6 speaker...

up :guitar:

---

### Post by ciccioermeglio on 2008-05-01
> **ciccioermeglio said:**
> up :guitar:

please help!:(

---

### Post by ciccioermeglio on 2008-05-01
> **ciccioermeglio said:**
> please help!:(

is there someone tha have a working surround sound with alc850?:confused:

---

### Post by DaveBG on 2008-05-02
> **eje_s said:**
> Hopes this helps a lot of people.

I have created this file (since i did not have it too). Now do i need to reset PC since the sound still comes from front 2 speakers and not the rest?

---

### Post by ciccioermeglio on 2008-05-03
> **DaveBG said:**
> I have created this file (since i did not have it too). Now do i need to reset PC since the sound still comes from front 2 speakers and not the rest?

eje_s is died, or...he is lying:(

---

### Post by ciccioermeglio on 2008-05-04
> **DaveBG said:**
> I have created this file (since i did not have it too). Now do i need to reset PC since the sound still comes from front 2 speakers and not the rest?

have you resolved the problem?

---

