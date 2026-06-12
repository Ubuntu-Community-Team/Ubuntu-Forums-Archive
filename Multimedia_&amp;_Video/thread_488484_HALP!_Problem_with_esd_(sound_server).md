---
title: "HALP! Problem with esd (sound server)"
date: 2007-06-30
forum: Multimedia &amp; Video
---

### Post by thebeefytaco on 2007-06-30
whenever I try to play music in totem or any similar program I get an error that says "An error occurred: Could not establish connection to sound server ".
Also when i type "esd" in the terminal i get "ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore"

I have libesd-alsa0 installed instead of libesd0 
Here's what my /etc/esound/esd.conf looks like:
```
[esd]
auto_spawn=1
spawn_options=-terminate -nobeeps -as 2 -d default
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=
```
WOOAH wtf, when I opened that (using gedit and the terminal) I got this as an error message(in the terminal):
```
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
- using device default
- using device default
ALSA lib pcm_dmix.c:831:(snd_pcm_dmix_open) unable to create IPC semaphore
```


anyway,  /etc/asound.conf looks like this:
```
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
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
```
/etc/libao.conf looks like this: 
```
default_driver=alsa
```
Screenshot of the first tab of my sound preferences
[IMG]http://img329.imageshack.us/img329/4623/screenshotsoundpreferenfy9.png[/IMG]
and the next:
[IMG]http://img148.imageshack.us/img148/7233/screenshotsoundpreferenzs2.png[/IMG]

I'm running Feisty and I use GNOME and xfce, please help me with this problem asap b'cuz I <3 my ubuntu w/ sound ^-^.

---

### Post by thebeefytaco on 2007-06-30
=[ noone is halping me..

---

### Post by .t. on 2007-07-01
First off, I would always wait at least 24 hours before bumping the post; this allows everyone in every time zone to see it.

Now to business. The alsa-lib messages you are getting seem to suggest there is a problem with the IPC (inter-process communication). Perhaps your "ipc_key"s are not unique. I suggest changing them to unique (or at least different) values. Moreover, could you post the output of `cat ~/.asoundrc*`

I'm also wondering why you are using ESD as a default GStreamer playback device (at least, I think that's what that setting changes). ESD is a poor attempt at a sound daemon in my opinion, and in most cases can be successfully by-passed: GStreamer can render sound directly to ALSA or OSS devices, without the need for a middle man. Should you want the functionality a good sound server provides, like network sound, or separate volume controls for applications, or on-the-fly sink switching, I recommend looking into PulseAudio. This would also solve your problem of mixing: PulseAudio in most cases supersedes dmix, as it can do the software mixing for you.

Having said all that, PulseAudio itself is not necessary most of the time.

---

### Post by .t. on 2007-07-01
Hi - I got your PM, but I'm unsure if it means that the above helped. Did it? If so, I think it would be beneficial to the knowledge base if you could post here ;)

---

### Post by thebeefytaco on 2007-07-01
```
josh@ubuntu:~$ cat ~/.asoundrc*
cat: /home/josh/.asoundrc*: No such file or directory
```

I'm still having sound problems, I sent the pm before i realized you had replied to the post.

also, clean install should be my last resort, because it took a long time to get my wireless drivers working and other settings
```
 josh@ubuntu:~$ cat /etc/asound.conf ~/.asoundrc*
# Set default sound card
# Useful so that all settings can be changed to a different card here.
pcm.snd_card {
     type hw
     card 0
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
cat: /home/josh/.asoundrc*: No such file or directory

```

---

### Post by .t. on 2007-07-02
You're right. I would try to never advocate a clean install, as most cases can be solved with a bit of work. I'll do some research and see what comes up.

---

### Post by .t. on 2007-07-02
Right, thanks to Thingol79; could I ask you to test with "ipc_perm 0666" in the pcm* stanzas which contain "ipc" references?

---

### Post by thebeefytaco on 2007-07-02
well, idk what i did but sound is working in everything but flash

---

### Post by thebeefytaco on 2007-07-04
ugh all sound stopped working, i think im going to back up my stuff and do a clean feisty install... the only thing im worried about is getting my wireless drivers working again

---

### Post by thebeefytaco on 2007-07-06
uuugh still having sound problems after a clean install, this is an error i've been getting when i log into KDE[IMG]http://img396.imageshack.us/img396/8236/errorhk6.png[/IMG]

---

