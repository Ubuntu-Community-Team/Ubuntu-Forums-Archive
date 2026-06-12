---
title: "SB X-fi stops 96khz spdif output"
date: 2012-11-07
forum: Multimedia Software
---

### Post by mattkarikomi on 2012-11-07
running 12.04 with sb x-fi working, sort of.  the system boots and i get a conformation on my external DSP showing 96khz feed from the sb-xfi over coax.  then i do a sound test by going to sound settings --> output --> test sound, and the test clip plays through the speakers and my DSP shows this as a 96khz feed.  then i go to listen to a song or play a video (vlc or rhythmbox) and i get no upsampling, the DSP shows only 48khz sample rate.

of course i have googled stuff like "x-fi 96khz ubuntu, x-fi broken linux", etc and found nothing to suggest what part of the multimedia interface controls the upsampling functionality of this card or how this functionality might be manipulated differently by apps running on the same installation.  what do you think is the problem here and how can i fix it.  or even better, where is the documentation that answers this question?  thanks

---

### Post by BicyclerBoy on 2012-11-08
There multiple way to achieve this:

1. upsampler in the player app
2. alsa libsamplerate plugin
[/etc/asound.conf]
defaults.pcm.rate_converter "samplerate_best"
pcm.rate_convert {
    type plug
    slave {
        pcm "hw:1,0"
        format S32_BE
        rate 96000
    }
}
# have to determine what to change hw:1,0 to...
# have to check your sound codec can accept 32bit be..
# test with:
# speaker-test -c 2 -l 2 -r 48K -D pcm.rate_convert

3. pulse samplerate plugin/module?
[/etc/pulse/default.pa] 
default-sample-rate = 96000
resample-method=src-sinc-best-quality

1. VLC might let you upsample, rhymthmbox just uses default system settings.
2. works well but you need to have apps that can be pointed at a specific audio device (clementine, VLC, MythTV etc)
3. allows system wide sound upsampling.

2. & 3. lets you play 192KHz/24bit by downsampling..

---

### Post by whell on 2012-11-08
I'm not sure if this relates to the issue you describe.  However, if your source is a 24/96 music file, and you're playing it back using Rhythmbox, then he signal will get down-sampled to 48 kHz when is passes through PulseAudio.  VLC, however, can be set to bypass PulseAudio and use ALSA, which will retain the sample rate of the music file during playback.  

You'll need to access VLC settings, go into the "Audio" section of VLC settings, and select ALSA from the first pull down menu in that section.  Below that in a separate pull down menu, you can set the sound device you want ALSA to output the signal to.

Rhythmbox doesn't alllow the user to bypass PulseAudio, therefore I don't use it to playback hi res audio files.  Clementine will allow the user to bypass PulseAudio, as well as other players like Audacious, deadbeef, and Guayeduque.

---

### Post by BicyclerBoy on 2012-11-09
The previous posted pulse audio tweaks allows 96KHz playback & hi quality upsampling..

To get 24bit s/pdif (32bit frame):
[/etc/pulse/daemon.conf]

default-sample-rate = 96000
resample-method=src-sinc-best-quality
default-sample-format = <mode>

where <mode> = [s24le, s24be, s24-32le, s24-32be, s32le, s32be, float32le, float32be] depending on what the sound card codec accepts.

Mistake in prev post suggesting /etc/pulse/default.pa..

---

