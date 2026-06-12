---
title: "ICH8 sound card not working in 8.04 LTS"
date: 2008-05-03
forum: Multimedia Software
---

### Post by Nitrox17 on 2008-05-03
Recently installed 8.04 LTS and my sound card isn't working!

In sound settings when I try to test any devices I get the following error message

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument

And when I try to adjust the volume I get the following error message

No volume control GStreamer plugins and/or devices found

(running 64bit by the way)...

Thanks for any help :)

---

### Post by Zorael on 2008-05-04
See if anything over at [http://ubuntuforums.org/showthread.php?p=4869649#post4869649](http://ubuntuforums.org/showthread.php?p=4869649#post4869649) applies. That is, if you have an Intel HDA chipset.

---

### Post by Nitrox17 on 2008-05-05
Nope didn't work
I tried changing the model in alsa-utils to no avail

aplay -l shows no soundcards found

lspci shows my audio device as "Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)"

Any other ideas?

---

### Post by Zorael on 2008-05-10
Is the driver assigned to the device and is the module loaded? Post the output of the following commands.
```
$ lshw -C multimedia
$ lsmod | grep snd
```

---

### Post by ShellyLewis on 2008-05-15
I just upgraded from 7.10 to 8.04 and have a similar problem.  My laptop computer came with ubuntu  7.10. I have an IHDA Sound card.  I'm pretty new to ubuntu.  How can I configure my soundcard to work with 8.04?  

How do I assign the driver to the device or load the module?  I don't see how I can access that.  How would I post output of the commands you laid out?  Do I have to enter the terminal?

---

### Post by Zorael on 2008-05-15
Yes, pop up a terminal and enter those commands.

Omit the dollarsigns though, they're syntax convention to show they should be entered in a terminal.

---

### Post by ShellyLewis on 2008-05-15
Should I use a backslash if I don't have a vertical line key?  Are those lower case L's or upper case i's?

---

### Post by xc3RnbFO8P on 2008-05-15
Just copy/paste in to terminal

---

### Post by ShellyLewis on 2008-05-15
The following is what it showed me:


 lsmod | grep snd
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  1 snd_pcm_oss
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  9 snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  1 snd_pcm

Then:

  lshw -C multimedia
WARNING: you should run this program as super-user.
  *-multimedia UNCLAIMED  
       description: Audio device
       product: 82801H (ICH8 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

It's still not working.  And I don't know what the following things are:
changing the model in alsa-utils 
aplay -l


What can be done next?

Thanks!

---

