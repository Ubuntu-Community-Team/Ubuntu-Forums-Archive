---
title: "no sound in hardy. 2.6.24.16, nvidia hd audio, ALC882"
date: 2008-04-22
forum: Multimedia Software
---

### Post by bdean42 on 2008-04-22
So I'm not very happy with Hardy so far. My sound card stopped working and I've never had a problem with it in Feisty or Gutsy. It was actually one of the things I liked about Linux but now I have to reboot to WinXP just to listen to music.

Anyway, here's some info on my setup. It is a evga nvidia 680i motherboard which has nvidia hd audio. Here's the output from lspci:
```
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
```


and here's the output of **[FONT="System"]lsmod | grep snd[/FONT]**
```
snd_hda_intel         359192  1
snd_hwdep              10628  1 snd_hda_intel
snd_pcm_oss            42528  0
snd_pcm                78852  2 snd_hda_intel,snd_pcm_oss
snd_seq_midi            9504  0
snd_mixer_oss          18048  1 snd_pcm_oss
snd_rawmidi            25888  1 snd_seq_midi
snd_seq_dummy           4996  0
snd_seq_oss            35456  0
snd_seq_midi_event      8576  2 snd_seq_midi,snd_seq_oss
snd_seq                54096  6 snd_seq_midi,snd_seq_dummy,snd_seq_oss,snd_seq_midi_event
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_midi,snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq
snd                    57124  13 snd_hda_intel,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_rawmidi,snd_seq_dummy,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
soundcore               8800  1 snd

```

and the output from **[FONT="System"]aplay -l[/FONT]**
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also, **[FONT="System"]alsamixer[/FONT]** shows the device and nothing is muted and all the volume levels are reasonable.

I looked through dmesg for anything related to sound but didn't see any sort of warnings or errors. I'm no Linux guru so I may be missing something obvious but I went through the common sound problems sticky thread and according to that I should have sound. And it's odd because all the modules that need to be there are there in the lsmod. Even alsamixer shows the card. I tried playing an ogg file in mplayer from the command line and it plays just fine and says it's using alsa but there is no sound whatsoever coming out of the speakers. I even tried compiling the alsa modules with module-assistant and that didn't make a difference.

There's nothing wrong with the speakers because I haven't changed them at all since I upgraded to Hardy and they worked fine in Gutsy and still works fine in WinXP and *cough* Vista.

Any help would be much appreciated.

---

### Post by bdean42 on 2008-04-22
**Update:**

So this is odd and I'm not really sure what it means but I can get sound out of the front side headphone jack. I had a suspicion that ALSA was more or less working because none of the applications that use it (mplayer and amarok (xine)) complained at all about it not working and they all seem to actually be playing the files but no sound is showing up.

So I thought that maybe I'd try the headphone jack and surprise, it works. But I don't know what this means or where to go from here. And like I said before, I can't find any error or warning messages anywhere to say what is going on.

---

### Post by bdean42 on 2008-04-23
More weirdness.

It's way too late at night to stay up and investigate what is happening here but I tried another thing at random and it seems to have magically fixed things.

I had seen in some other thread where someone changed the master channel and it made a difference. They were changing it from PCM to headphones or something like that. I use KDE so I opened up kmix and told it to change the master channel from "Master" to "PCM".

When I did this sound seemed to work. So I changed it back... and sound still worked. So I rebooted and sound still works! I'm really confused as to what happened but I am happy that things seem to be working now. My volume is all messed up from playing with alsamixer and kmix but that's something I can easily adjust.

Does anyone have a reasonable explanation for what is going on? Does anyone even care about this problem? I mean a lot of people out there have nvidia hd audio on their motherboard and if it is finicky then that might be a problem with Hardy. I'm wondering if a clean install vs. an upgrade would have made a difference and if so, why?

---

### Post by Gwaihirjp on 2008-05-05
I seem to be having the exact same problem as you with my Hardy.. I've updated my Dell Inspiron 1420 about a week ago and suddenly the sound just stopped working. Since then I've been googling for solutions and found very many suggestions and fixes, but none of them seem to work.

I tried and found out that the sound still works on my headset. I wanted to try your interesting solution involving changing the master channel, but I'm not sure how to do that as mine is not kubuntu.

Oh well, I guess I just gotta keep trying or wait until they release an update to fix it.

---

