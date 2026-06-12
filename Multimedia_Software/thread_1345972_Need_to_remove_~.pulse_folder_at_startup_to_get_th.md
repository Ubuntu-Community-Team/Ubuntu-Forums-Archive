---
title: "Need to remove ~/.pulse folder at startup to get the soundcard working"
date: 2009-12-04
forum: Multimedia Software
---

### Post by ittiam on 2009-12-04
I am using Toshiba L505D-S5986 laptop. I did a fresh installation of karmic and there are acpi issues and sound card issues. 

Here, let me post about the sound card issue alone.

This is what happens, after logging in to my laptop

[LIST=1]
[*]The speakers are in mute by default even if I hadn't set it in mute during my previous login.
[*]So I toggle the mute into off and try playing an audio (mp3 using banhsee), it plays the first song when I do next, all I hear is crackling sound.
[*]The above issue is resolved if I delete the ~/.pulse folder and restart banshee.
[*]This issue is not specific to banshee or anything. I have tried amarok and rhythmbox as well. Same behavior.
[*]So I decided to write a trivial script to remove ~/.pulse folder and put it in startup applications. This does not work. For some reason when I do this, I absolutely hear no sound although I can see the time progress bar for the song moving nicely. I have to remove ~/.pulse manually after the startup is complete to get the sound card playing without any crackling sound.
[*] I have tried removing alsa-base and pulseaudio and reinstalling again. Did not work. 
[*] I tried setting  the model to auto in /etc/modprobe.d/alsa-base.conf, did not work.
[/LIST]

Any suggestions or pointers?

---

### Post by otiuq on 2011-06-19
Hello, I have the same problem. How you solved the Problem.?

---

