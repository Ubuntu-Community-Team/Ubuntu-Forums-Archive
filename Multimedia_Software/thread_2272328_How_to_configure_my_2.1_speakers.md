---
title: "How to configure my 2.1 speakers?"
date: 2015-04-05
forum: Multimedia Software
---

### Post by lucas38 on 2015-04-05
Hi, I'm new to Ubuntu, I was using Windows 7 before, and my 2.1 speakers worked fine. But now, on Ubuntu 14.04 my 2 front speakers work, but I can't get my subwoofer to work.
In the Sound Settings, there is just one option: "Analog Output (Built-in Audio)" where the subwoofer control is disabled and in the "Test sound" window I can only see "Front left" and "Front right" speakers.

I have already tried:

**1) /etc/pulse/daemon.conf**
enable-lfe-remixing = yes
default-sample-channels = 3
default-channel-map = front-left,front-right,lfe
Result: no changes

**2) /etc/pulse/default.pa**
load-module module-combine channels=3 channel_map=front-left,front-right,lfe 
**/etc/pulse/daemon.conf**
enable-lfe-remixing = yes
Result: another option appeared in the Sound Settings: "*Simultaneous output to Caicos HDMI Audio [Radeon HD 6400 Seris] Digital Stereo (HDMI), Buil-in Audio Analog Stereo*". Within it, when I clicked "Test Sound", a new option appeared - "Subwoofer". But the sound was played by the 2 front speakers, and the subwoofer is still not working.

I tried to follow some tips at [this link]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"), but I could not find anything useful for my case... I executed Step 3, and attached the output here [ATTACH]261114[/ATTACH]

Does anybody have any idea?

Thanks!

---

### Post by dino99 on 2015-04-06
install 'paman' to set the pulseaudio settings: glance at 'configuration' & 'output devices' tabs from the 'pulseaudio volume control' Sound menu

---

### Post by efflandt on 2015-04-06
What type of 2.1 speaker system do you have? The 2 systems I have (1 Creative and 1 Klipsch) simply use a single 3.5 mm stereo plug and the speaker system itself has controls for an additional volume control and subwoofer mix. So to any computer system it simply looks like analog stereo.

---

### Post by lucas38 on 2015-04-06
**9d9**, sorry didn't understand your suggestion...  please take a look in my attachment with screenshots from PulseAudio Volume Control, and let me know if I should do anything: [ATTACH]261143[/ATTACH]

[COLOR=#000000]**efflandt**, see my attachment with the speakers configuration... I guess it's like yours, but I can't get it to work properly... on windows works fine: 
[/COLOR][ATTACH=CONFIG]261144[/ATTACH]

Thanks

---

### Post by lucas38 on 2015-04-11
Any other suggestions?

Thanks!

---

### Post by Rob Sayer on 2015-04-12
Is this it:

[http://www.edifier.com.br/produtos-detalhes.php?cod_cat=2&codigo=107](http://www.edifier.com.br/produtos-detalhes.php?cod_cat=2&codigo=107)

???

If so, it seems to just have analog headphone input.  As mentioned, that has nothing to do with getting 2.1 sound in alsa or pulseaudio.  It's just passive crossovers in the speakers.

Do headphones work?

---

### Post by lucas38 on 2015-04-12
Yeah, it's this one..
I got it now.. yeah it's a problem with the subwoofer it self, I just tested with my IPod...

sorry the dumb post..

thanks all

---

### Post by Rob Sayer on 2015-04-13
Don't worry about it, you gotta ask ...

---

