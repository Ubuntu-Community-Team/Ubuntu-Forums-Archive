---
title: "How to  record audio from operapluginwrapper using FFMPEG?"
date: 2011-10-06
forum: Multimedia Software
---

### Post by nhtrader on 2011-10-06
Mythbuntu 10.04 LTS (64bit)
XFCE 4.8.0
alsactl version 1.0.23
opera 11.51
audio stream is coming in via:
/usr/lib/opera//operapluginwrapper /usr/lib/flashplugin-installer/libflashplayer.so


1. my sound system works perfectly.
2. skype works perfectly.
3. internet radio playback works perfectly.

I'd like to record internet radio, but after a week of googling I'm stuck.
As you will see below, I've been stumbling around trying to find the correct way to record the output from the webbrowser's multimedia plugin. Conceptually, I get that the audio stream is flowing from webbrowser's plugin to sound card's mixer and then is sent out to the audio plug connected to my speakers. The problem is in being able to record this as it is flowing through to the speakers.

I've tried to identify the correct ALSA device, but can find it.

I've learned that command "amixer set" might be able to redirect the PCM playback stream to a capture stream, but I don't know how to do this.

I've learned that creating a ALSA plugin in file /home/user/.asoundrc might be the way to create a duplicate stream which would convert the webbrowser's output stream (playback) to an input stream (capture), but I don't know how to do this.

Lastly, I tried installing pulseaudio(PA) / sox / pavucontrol but this didn't work either. After the PA installation I lost all sound from any source to my speakers despite the fact that pavucontrol (PA's VU meter) showed a signal was being captured and should have played through internal card's speaker. This pavucontrol also showed opera's plugin as the sound source. But since I lost all sound, I uninstalled/purged  PA.

Secondly, I confirmed the sound source by hunting through all of my system's sound devices to find the one that was running (/proc/asound/card0/pcm0p/sub0)
I used commands:
cat /proc/asound/card0/pcm0p/sub0/status 
    output: running  owner_pid 5822

ps aux|grep 5822 which showed the opera flash_plugin as the source.
 

So after much effort I still can't figure this out. Does anyone know how to do this?


I've tried the following commands (all of these didn't work):
ffmpeg -f alsa -ac 2 -i hw:0,0 radio.mp3
ffmpeg -f alsa -ac 2 -i hw:0,1 radio.mp3
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i hw:0,0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i hw:0,1 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i hw:0,2 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i hw:1,0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i hw:1,1 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i ctl.hw:0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec copy -i dsnoop:0,0 radio.mp3
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i dsnoop:0,0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i PCMC0D0p radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i pcm0p radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i dmix:CARD-SB,DEV=0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i dmix:0,0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i ALSA:default radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i plughw:0,0,0 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i plughw:0,0,1 radio.wav
ffmpeg -f alsa -ac 2 -ab 192k -ar 44100 -acodec pcm_s16le -i plughw:0,0,2 radio.wav
ffmpeg -f alsa -ac 2 -acodec pcm_s16le -ab 192k -i hw:0,0 -f s16le radio.raw 

then variations of ...
arecord -D hw:0 -t wav -f S16_LE -c 2 -r 44100 radio.wav

then variations of ...
mplayer -ao alsa:noblock:device=hw=0.1 -volume 100 radio.wav
mplayer -dumpstream  -softvol -dumpfile radio.mp3
mplayer -dumpstream  -softvol -mixer pcm0p -dumpfile radio.mp3
mplayer -ao alsa -volume 100 radio.wav

---

