---
title: "Please explain digital sound options, cause some things are not working"
date: 2014-01-26
forum: Multimedia Software
---

### Post by sdowney717 on 2014-01-26
In windows 7, I can set frequencies from 44.1 to 48 to 96 and up
I see no settings for this in pavucontrol.
I set pavucontrol to play AC3, MPEG2, DTS

Playing Dolby Digital 5.1 test file ChannelCheck.m2ts from the Dolby website = no sound in VLC, sound in movie player is only PCM 48, no LFE, no right and no left surround sounds.

Playing a test file with an avi extension, 
VLC plays dolby digital 5.1, in the sony receiver Dolby Digital 3/2.1 is displayed, it works fine.
Movie player is only PCM 48 in the sony receiver, no LFE, no right and no left surround sounds.

So VLC will not play any sounds with an m2ts extension.

---

### Post by sdowney717 on 2014-01-26
screen shot vlc with an m2ts file with no  audio output set to spdif

---

### Post by sdowney717 on 2014-01-26
download links for the test files, the one I showed above was mountain bikes.
[http://www.dolby.com/us/en/consumer/technology/home-theater/dolby-digital-plus-download.html](http://www.dolby.com/us/en/consumer/technology/home-theater/dolby-digital-plus-download.html)

I downloaded the large TS files.

---

### Post by sdowney717 on 2014-01-26
i just tried all the other mp4 file.
movie player errors with stream general stream error

vlc plays only video no sound

do i need codecs?

---

### Post by sdowney717 on 2014-01-26
I installed ubuntu restricted extras which uninstalled vlc-obnox

I then reinstalled vlc
I can now play mp4 in movie player, but sound is not digital 5.1 only pcm 48
VLC still cannot play m2ts sound. With the test mp4 files, VLC is only pcm 48

---

### Post by sdowney717 on 2014-01-26
[https://help.ubuntu.com/community/DigitalAC-3Pulseaudio](https://help.ubuntu.com/community/DigitalAC-3Pulseaudio)

I have found this. So I have to compile something.

---

### Post by sdowney717 on 2014-01-26
pulse audio is now dead no sounds at all
system problem at boot
who is responsible for the instructions?

---

### Post by sdowney717 on 2014-01-26
This instruction fails due to the folder 'alsa-lib' does not exist there.
So I created the folder and then the copy works.
sudo cp libasound_module_pcm_a52.la libasound_module_pcm_a52.so /usr/lib/alsa-lib/

But the whole sound system is wrecked now.

---

### Post by sdowney717 on 2014-01-26
following new instructions
[http://opennomad.com/content/ubuntu-1210-and-spdif-or-iec958-or-optical-audio-output](http://opennomad.com/content/ubuntu-1210-and-spdif-or-iec958-or-optical-audio-output)
pulse audio now broken
system failure detected

i am using 13.10

---

### Post by sdowney717 on 2014-01-26
I undid all the installs, copies, etc...
And it is back to a working condition, albeit no dolby 5.1 playback on spdif.

---

### Post by sdowney717 on 2014-01-26
I will try this later.
The Linux sound system is tampering with the stream? and not allowing it to pass through unmodified.
[http://globatic.blogspot.com/2013/07/dts-and-ac3-dolby-digital-surround.html](http://globatic.blogspot.com/2013/07/dts-and-ac3-dolby-digital-surround.html)

> The standard way of getting this stack to work is to pass through the digital audio signal as-is from the source media to the amplifier. This means that the system cannot mix in other sounds, like system notifications, to the audio output stream without scrambling the original proprietary DTS/AC3 digital encoding of the audio stream. In short, you need an exclusive access to the audio stream for the application you are using.** Normal Linux sound system mixers, such as Pulse and GStreamer are poison,** I haven't been able to get digital surround sound working with these, and I am not convinced that there is a way. However, you don't need to uninstall your convenient sound system stack, just make sure that your video player application skips the stack and goes directly to the sound card, for example by using ALSA.

---

### Post by sdowney717 on 2014-01-27
Well that did not work at all with mplayer as it could not open the sound device. So no sound.

I found so far that only VLC can play dolby digital sound AC3.
Only so far on file extensions of ac3  or avi.

Working example video and audio DD 5.1 surround perfect in VLC.
[http://www.tfm.ro/win32-projects/test-avi-ac3/](http://www.tfm.ro/win32-projects/test-avi-ac3/)
[http://www.lynnemusic.com/surround.html](http://www.lynnemusic.com/surround.html)

Can anyone give me more info on what to do about the m2ts DD 5.1 files and vlc?

The m2ts files show the same audio codec as the avi files.
Sometimes the m2ts files play like R2D2 squeaky sounds, sometimes silent.
In windows7, with VLC they play DD 5.1 sound fine.

---

### Post by sdowney717 on 2014-01-27
well, next step is to follow mythtv instructions for DD playback
[http://www.mythtv.org/wiki/Digital_Audio_Tutorial](http://www.mythtv.org/wiki/Digital_Audio_Tutorial)

---

