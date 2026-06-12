---
title: "Switch audio in/out sockets on Natty"
date: 2011-05-23
forum: Multimedia Software
---

### Post by neogarfield on 2011-05-23
Hey,
i'm running Ubuntu Natty, and i have this little problem with my sound card. i have three jacks on the card, the usual with a normal home PC, - one for the speakers, second for the microphone, and third for line in. Now my speakers (Line out) jack is damaged a little. So when i plug in my speaker jack there, i get audio only in the right speaker (not a problem of the speakers, because i tested it, and not Ubuntu either, because this problem existed when i used to run Windows XP as well).

Now in Windows XP, what i used to do is, there was this tool (i think it came with the sound driver - Realtek) whenever i plugged in a jack into either of the sockets, a gui would ask me what i just plugged in, and it would allocate audio in and out according to what i specify then. So i used to plug in my speakers into the line in, because thats something i do not use, and used the tool to identify that jack as the line out.

Is there some way i can do this on Ubuntu? i want to get line-out through the line-in socket. i'm a beginner with Ubuntu, and know only to use the GUI...

Help would be appreciated :) Thank you!

---

### Post by neogarfield on 2011-05-24
Any clues on this anybody?

---

### Post by lidex on 2011-05-25
You may need realtek drivers to do that, however post your stats and we'll see. Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications-> Accessories-> Terminal"]

---

### Post by neogarfield on 2011-05-26
Thanks! Did that. Here's the link-
[http://www.alsa-project.org/db/?f=9121891e6813d81afa8060b8042de27e7e1e5f46](http://www.alsa-project.org/db/?f=9121891e6813d81afa8060b8042de27e7e1e5f46)

---

### Post by lidex on 2011-05-27
Open alsamixer:
**Alsamixer**
Using a Terminal="Applications-> Accessories-> Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

Adjust the 'Line' element

---

### Post by neogarfield on 2011-05-30
Hey lidex, thank you for the reply. Sorry i couldn't try this out earlier - i had gone away from home for a couple of days.

i tried what you suggested. First, there was no Line in capture. There were Capture, Capture 1, Capture 2, Input source [Mic], Input source 1 [Mic], and Input source 2 [Mic]. Of this only the first, Capture, was unmuted. The others were muted. i found a line in Playback, and increased levels, but that didn't help my case...

What next?

Thank you...

---

### Post by lidex on 2011-05-30
```
Simple mixer control 'Line',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 65
  Mono:
  Front Left: Playback 0 [0%] [-35.00dB] [off]
  Front Right: Playback 0 [0%] [-35.00dB] [off]
```
You'll need to unmute also. The mute and level functions are separate.

---

### Post by neogarfield on 2011-05-31
Oops, didn't see that one.

So i unmuted and increased the levels for the "Line" element in Playback, but it still doesn't help my case. My speakers are plugged into the Line In on my CPU...

What next?

---

### Post by lidex on 2011-05-31
I feel there should be an easy way to do this, but I've been wrong before. Perhaps hda analyzer can solve this.
> hda-analyzer
~~~~~~~~~~~~
hda-analyzer provides a graphical interface to access the raw HD-audio
control, based on pyGTK2 binding.  It's a more powerful version of
hda-verb.  The program gives you an easy-to-use GUI stuff for showing
the widget information and adjusting the amp values, as well as the
proc-compatible output.

The hda-analyzer:

- [http://git.alsa-project.org/?p=alsa.git;a=tree;f=hda-analyzer](http://git.alsa-project.org/?p=alsa.git;a=tree;f=hda-analyzer)

is a part of alsa.git repository in alsa-project.org:

- git://git.alsa-project.org/alsa.git


---

### Post by neogarfield on 2011-06-01
Hmmm. i'm sorry! You'll have to guide me through this! How can i go ahead and use it?

---

