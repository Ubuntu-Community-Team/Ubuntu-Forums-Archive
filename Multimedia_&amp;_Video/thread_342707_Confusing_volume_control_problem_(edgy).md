---
title: "Confusing volume control problem (edgy)"
date: 2007-01-20
forum: Multimedia &amp; Video
---

### Post by shailiha on 2007-01-20
Hello everyone, long time lurker first time poster :-)

Well, I have run into a small conundrum wich I've tried to fix by reading around here and googling etc, but alas I'm at a loss.

It all started (I think) After installing the latest Amarok (1.4.4) from source to fix the problems I had with my iPod.

Anyways, after rebooting that evening for some reason I can't remember, I appear to have lost the ability to change volume. The speaker in the top right corner of my screen has a red circle on it.

If I click it I get the "No volume control GStreamer plugins and/or devices found." that I have seen others suffering from across the forums. None of those threads I could find could however help me.

I have sound, but I can't change the volume other than through the media players I use.

I have followed the Comprehensive Sound Problem Solutions Guide to no avail.

aplay -l gives:
```

**** List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
 
```

lspci -v gives:
```

00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
        Subsystem: Micro-Star International Co., Ltd. K8T NEO 2 motherboard
        Flags: medium devsel, IRQ 209
        I/O ports at b000 [size=256]
        Capabilities: <access denied>


```

sudo modprobe snd-via82xx does not return an error so I assume it it successful.

alsamixer allows me to change the volume, but it is quite a hassle to go in there all the time. I would much prefer to be able to change the volume with my g15 keyboard like I could a few days ago.

My user is a member of the audio group:
```

audio:x:29:shailiha

```

gstreamer-propreties gives a long list of errors:
```

shailiha@storken:~$ gstreamer-properties 
gstreamer-properties-Message: Skipping unavailable plugin 'autoaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasink'
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'osssink'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesink'
gstreamer-properties-Message: Skipping unavailable plugin 'autovideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'ximagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'xvimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'videotestsrc is-live=true'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4l2src'
gstreamer-properties-Message: Skipping unavailable plugin 'alsasrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'osssrc'
gstreamer-properties-Message: Skipping unavailable plugin 'pulsesrc'
gstreamer-properties-Message: Skipping unavailable plugin 'audiotestsrc wave=triangle is-live=true'
gstreamer-properties-Message: Skipping unavailable plugin 'audiotestsrc wave=silence is-live=true'

```

And it has Output and Input set to Custom and the pipelines can not be edited. If I click on Test I get:

Output:
```

Autodetect: no element "audiotestsrc"

```

Input:
```

ALSA - Advanced Linux Sound Architecture: no element "alsasrc"

```

I have pretty much all the gstreamer1.10 packages from the SPM installed (except docs).

I don't know what else I can post to shed some light on the problem, but I appreciate your time and if any more information is needed I'll provide it momentarily.

---

### Post by wrathful mite on 2007-02-16
It looks like the problem isn't with your sound, but with your user/group privileges. Try opening "users-admin" (as root) and change your group to what it originally was; and also go into your user's properties and make sure you have all of the User Privileges set.
To get into users-admin, open a terminal window and type:
```

$ su
(Enter your root user's password -- it may not work with just your password if you don't have sudo privileges)
# users-admin

```

---

