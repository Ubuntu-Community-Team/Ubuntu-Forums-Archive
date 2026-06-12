---
title: "Hardy: Multiple programs playing sound at once"
date: 2008-04-25
forum: Multimedia Software
---

### Post by jordon on 2008-04-25
I can't get two programs to play sound at the same time in Hardy. Even if I stop the sound playback in one, the other won't output any sound.

For example, if I try to use Ekiga while another program is playing sound, I'll get an error message saying: "An error occured while trying to play audio to the soundcard for the audio reception. Please check that your soundcard is not busy and that your driver supports full-duplex. The audio reception has been disabled."

I didn't have this problem in Gutsy because I set programs' audio output devices from "Default" to "HDA Intel." Now it doesn't make a difference; I still can't get the sound.

---

### Post by jordon on 2008-04-26
I should mention that the method described here:
[https://help.ubuntu.com/community/DebuggingSoundProblemsMisc](https://help.ubuntu.com/community/DebuggingSoundProblemsMisc)
doesn't help at all.

This is especially annoying when I'm using Rhythmbox and Firefox at the same time since I can't set the playback devices for either of them.

---

### Post by jordon on 2008-04-26
I've done a little more research. My main issue was that if I was listening to something in Rhythmbox and paused it to listen to the sound of a Flash video in Firefox, the Flash wouldn't play. Now I've installed libflashsupport, and that works, so that's good. The description for the package is:

"Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible."

Poking around Synaptic a little more, I see that gstreamer also has a plugin for PulseAudio, which was already installed. That explained why I could use Totem (with gstreamer) and Rhythmbox at the same time. But does this imply that other programs I've having a problem with (namely, Audacity and Ekiga) don't support PulseAudio at all? I seem to have discovered that Audacity doesn't support PulseAudio, but Ekiga is a GNOME program, so I would expect more from it than that.

---

### Post by eriksallstrom on 2008-04-26
Maybe you could try installing the package libasound2-plugins.

You can start Audacity with the command
padsp audacity
Since it uses OSS. I get clicking disturbances in the sound though, but haven't found anyone else who has that problem though.

---

### Post by jordon on 2008-04-26
Thanks, that works. I still can't get Ekiga to work yet (probably because I can't choose OSS in the options, only ALSA), but it's a good step.

---

### Post by analoog on 2008-04-26
> **jordon said:**
> I've done a little more research. My main issue was that if I was listening to something in Rhythmbox and paused it to listen to the sound of a Flash video in Firefox, the Flash wouldn't play. Now I've installed libflashsupport, and that works, so that's good. The description for the package is:

"Due to various bugs in the Flash 9 plugin sound output of Flash 9 through the pulseaudio soundserver doesn't work properly. This library adds a clutch to make Flash 9 sound output in pulseaudio possible."

Poking around Synaptic a little more, I see that gstreamer also has a plugin for PulseAudio, which was already installed. That explained why I could use Totem (with gstreamer) and Rhythmbox at the same time. But does this imply that other programs I've having a problem with (namely, Audacity and Ekiga) don't support PulseAudio at all? I seem to have discovered that Audacity doesn't support PulseAudio, but Ekiga is a GNOME program, so I would expect more from it than that.
After the upgrade to hardy flash didn't produce any sound anymore. While hunting for a solution I found this post, after installing libflashsupport it now works. :)

---

### Post by jhnphm on 2008-04-27
I believe you can run "asoundconf set-pulseaudio" to enable pulseaudio for alsa apps (after installing libasound-plugins)

---

### Post by jordon on 2008-04-27
> **jhnphm said:**
> I believe you can run "asoundconf set-pulseaudio" to enable pulseaudio for alsa apps (after installing libasound-plugins)

That didn't do anything for Ekiga, but it did seem to have an effect. Now Thunderbird can play the new mail sound while I have music playing instead of waiting until I close Rhythmbox.

---

### Post by svaens on 2008-04-27
Hi Guys, 

I want to make this quick, as I don't even know if i have an issue with multiple programs playing at once. I just noticed this because of what eriksallstrom mentioned in his post:

> I get clicking disturbances in the sound though,

I wondered if I could ask if anyone else has had this problem, and if there is a solution?

I have what could be the same problem. I will start another thread to help find people who might know a solution.... But since it was mentioned here, I just wanted to ask. 

My symptoms are: 

playing sound via any program, be it Rhythmbox playing mp3, or vlc playing .avi, gives me problems. The problem being that any activity in the operating system; minimizing windows, browsing internet, and worse, viewing the System Monitor causes pops and clicks in the sound. Very annoying and not something you want to listen to. Which means that if you want to listen to music or watch a video, you have to make sure you don't do anything else with your computer at the time. And even then, you get the occasional small pop or click. 

anyone know what could be causing this? I have only noticed this since installing Hardy yesterday. I installed it clean after having before had Gutsy on my machine (without the said problem).

---

### Post by PinkFloydX on 2008-04-27
Hi
I also have a similar problem in Hardy. XMMS was always open in my laptop (toshiba satellite u300-151). When I wanted to play an avi by using Movie Player it was too slow and without sound, when I used VLC, it was playing normally but without sound. I also had problem during playback of youtube videos. They stopped after 2 seconds and there was no sound.
I checked many forums. People had similar problems with different versions of flashplayer, programs, etc. Some of them solved their problems by different configurations. However, there is no complete solutions for everyone. 
Indeed I do not have one either. However, this looks like soundcard problem. If one program uses it (like XMMS) it blocks the card and other program cannot use. Programs behave differenly.
One more comment, I did not have that problem with Gutsy.

---

