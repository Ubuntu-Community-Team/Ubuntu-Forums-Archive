---
title: "Songbird 1.4.1 won't play music"
date: 2010-02-22
forum: Multimedia Software
---

### Post by wolf_3d on 2010-02-22
I've installed Songbird using the synaptic package manager and songbird will appear to run without errors. As I am a lastfm user I use Songbird to play the lastfm website and from the website log into my account and play tracks using the player. However when I click on the play button within the web page it will try to buffer the track and then after a few seconds display the message "Oops! Error connecting".

When I run songbird from the terminal. This is the output that I get:

```
john@john-CUSTOMMACHINE:~$ songbird

(songbird-bin:12616): GLib-WARNING **: g_set_prgname() called multiple times
ImportError: No module named gst

(songbird-bin:12620): GStreamer-WARNING **: Failed to load plugin '/usr/lib/gstreamer-0.10/libgstpython_d.so': /usr/lib/gstreamer-0.10/libgstpython_d.so: undefined symbol: _Py_RefTotal

(songbird-bin:12616): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:12616): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:12616): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:12616): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
```

It does play music tracks from my /home folder but occasionally the program goes dark grey and appears to crash. It doesn't play youtube videos from within the lastfm website as the video will play but not the sound. When I try to play a lastfm track, this is the output from the terminal;

```
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory
mmap() failed: Cannot allocate memory

```

I've done some research on the net and I've read that removing gstreamer will work. So I have removed all instances of gstreamer from /usr/share/Songbird/lib.

I do not have libvisual-0.4-plugins installed.

I have tried the following;

```
sudo mv /usr/lib/python2.6/dist-packages/gst-0.10/ /usr/lib/python2.6/dist-packages/gst-0.10_bad
```

I'm stuck for further ideas.

---

### Post by wolf_3d on 2010-02-22
I have followed the instructions from here;

[http://translate.google.com/translate?hl=pt-BR&ie=UTF-8&sl=pt&tl=en&u=http://carlrobers.wordpress.com/2009/11/10/songbird-nao-inicia/&rurl=translate.google.com.br](http://translate.google.com/translate?hl=pt-BR&ie=UTF-8&sl=pt&tl=en&u=http://carlrobers.wordpress.com/2009/11/10/songbird-nao-inicia/&rurl=translate.google.com.br)

to remove all gst files from the gst-plugins folder in /usr/share/songbird.

The terminal output now reads;

```
(songbird-bin:4137): GLib-WARNING **: g_set_prgname() called multiple times

(songbird-bin:4137): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:4137): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:4137): Gdk-WARNING **: gdk_window_set_icon_list: icons too large

(songbird-bin:4137): Gdk-WARNING **: gdk_window_set_icon_list: icons too large
ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large

ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large

ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large

ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large

ALSA lib pcm_pulse.c:724:(pulse_prepare) PulseAudio: Unable to create stream: Too large

```

---

### Post by wolf_3d on 2010-03-16
I have now updated Songbird to 1.4.3 and I'm still having issues.

If I run Songbird from Applications > Sound & Video > Songbird it still returns the "Oops! Error connecting" message when I try to play a lastfm track. 

If I try and play a youtube video, I can see the video but I can't hear any sound.

I tried running Songbird using the command;

```
sudo -H songbird
```

...and I can't even see the lastfm player on the website. If I try and play a youtube video, youtube says that I have either got javascript turned off (it's definately on I've checked) or that I'm running an older version of Adobe Flash player.

---

### Post by wolf_3d on 2010-03-25
So, I don't know what fixed it but after trying out a few possible solutions I can now play youtube and lastfm tracks using the flash player from within Songbird.

Yesterday the Update Manager installed a new version of one of the gstreamer bad or ugly versions aswell as gstreamer0.10-sdl. And now it seems that I've had a good few hours of music from Songbird.

I'll mark this as solved as its behaving itself *touches wood*.

---

