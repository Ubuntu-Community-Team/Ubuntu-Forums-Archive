---
title: "FOCUSRITE SCARLETT 2i2 USB"
date: 2012-10-05
forum: Multimedia Software
---

### Post by saldomik on 2012-10-05
I bought this soundcard few days ago.
I read several positive articles on internet about its compatibility with Linux, so I decide to take it.
The OS recognized the soundcard immediately and I could hear the sound reproduced from the headphones connected on the front and from the speakers connected to the rear.
The problem is that, before the sound starts, there are some popping noises, like interferences, that come out.
This happens every time and it's quite annoying.
When using youtube on Google Chrome this problem is even more marked.
I tried changing kernel version, and also changing audio configuration, but nothing.
Can anyone help me? ;)

---

### Post by syncopated on 2012-10-15
I'm having similar problems and wanted to add some more information in case it may help diagnose and resolve the problem.

I have a Focusrite Scarlett 2i2 connected to a Thinkpad W520 running Ubuntu 12.04 LTS.

The interface works (produces sound) but any time a program is using the interface, I hear popping sounds at regular intervals of approximately 2 seconds. At each pop, the input level indicators flash. These pops are heard in groups of 2. The sound cuts out with the first pop, then back in with the second. When this is happening, the sound is slightly but noticeably pitched up. Oddly, the problem is resolved by opening the sound settings panel. The pitch drops back to normal, and playback is continuous (no pops).

I am not very familiar with the sound systems in use here or audio drivers in general, but if I were to venture a wild guess it seems like the playback sample rate on the device is set too high, and it is emptying a buffer somewhere faster than new data is provided (because the component filling the buffer thinks the sample rate is lower). When some client forces the sample rate to the proper value, playback is seamless.

I have blacklisted the modules for the internal Intel sound and disabled the discrete graphics hardware in case there was any interference, and this made no difference at all.

If anyone knows in which component this problem is likely to be happening, please let me know so I can report it on the proper list/forum.

---

### Post by tom0 on 2012-12-12
I just recently bought this soundcard too. I am running Ubuntu 12.10. I have pretty much the same issues as mentioned here.

The popping noises come in groups of 2 and the input level indicators flash (even though no inputs are connected). This happens fairly infrequently though, not every 2 seconds as @syncopated mentioned. I get the flashes every time I skip a song in Rhythmbox but this no longer gives the popping noise.

This problem and other general noise issues that I had with this soundcard and other previous soundcards were massively improved by using stereo jack connectors to my monitor speakers thereby using the balanced output. (Note, mono jack cables are NOT balanced - I only just found this out!)

Most annoying for me is when using Rhythmbox I occasionally (every 15mins or so) get the click/pop noises followed by a noticeable pitch increase. This can be fixed by flicking the output in sound settings and back again or just skipping to a different point in the song.

I have no idea how to fix this. @syncopated, @saldomik - have you guys had any luck?

---

### Post by drewm1980 on 2013-01-12
I'm experiencing the described problem on both:

My Lenovo ideapad U460 running Debian 6.0
My Dell Latitude E6510 running Ubuntu 12.04 LTS

I also read online positive reviews about linux compatibility and even tested it in-store briefly, but didn't notice this since I didn't have headphones plugged in.

I can get audacity to record and playback sound.  The card shows up in the Sound system preferences and seems to behave "normally". That is to say it shows up under two different names, but they both seem to work. The clicks occur whenever you select the sound card, which is reasonable.  However, other apps (chrome, audacity) make this sound far more frequently/intermittently.  The apps hang during the clicking (like right now making it harder to type this post).  This is not a subtle effect.

Update: Based on the report at:

[http://eldhuset.org/2012/03/04/focusrite-scarlett-2i2.html](http://eldhuset.org/2012/03/04/focusrite-scarlett-2i2.html)

I tried using rmmod (after bootup) to remove as many snd_* related modules as possible, including snd_hda_intel. Unfortunately, this did not have any affect on the problem.  The remaining modules are:

$ lsmod | grep snd
snd_usb_audio         122982  2 
snd_usbmidi_lib        25395  1 snd_usb_audio
snd_hwdep              13668  1 snd_usb_audio
snd_pcm                97188  1 snd_usb_audio
snd_rawmidi            30748  1 snd_usbmidi_lib
snd_seq                61896  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  2 snd_rawmidi,snd_seq
snd                    78855  12 snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  1 snd_pcm

Update 2:
I have also tried uninstalling pulseaudio.  No affect.

---

