---
title: "Audacious and my new Creative USB sound card"
date: 2008-08-23
forum: Multimedia Software
---

### Post by Daan on 2008-08-23
Hi all,

Today I got a new external sound card: the Creative Sound Blaster USB X-Fi Surround ([http://uk.europe.creative.com/products/product.asp?category=1&subcategory=208&product=17751](http://uk.europe.creative.com/products/product.asp?category=1&subcategory=208&product=17751)).

The main problem now is that I cannot get it to play from Audacious, which I prefer for playing music.

I set up my HP notebook with Ubuntu Hardy to have Pulse audio as standard for all sounds, under System -> Preferences -> Sound. Hitting the test buttons there gives a sound. I also get good sound from Xine, Totem and Amarok, but VLC and Rhythmbox keep using my the internal sound device of my laptop. Audacious doesn't play anything, not even through my internal card. I tried different settings for the output plugin (e.g. Pulse Audio, ALSA with device 0,0, device 0,1 etc.). Here are the error messages:

```
daan@schmauck:~$ audacious
amidi-plug(amidi-plug.c:amidiplug_init:97): init, read configuration
amidi-plug(i_backend.c:i_backend_load:107): loading backend '/usr/lib/audacious/Input/amidi-plug/ap-alsa.so'
amidi-plug(i_backend.c:i_backend_load:145): backend /usr/lib/audacious/Input/amidi-plug/ap-alsa.so (name 'alsa') successfully loaded
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:11025): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:11025): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:11025): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:11025): WARNING **: alsa_setup(): Sample format not available for playback: Invalid argument
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:11025): WARNING **: alsa_setup(): Failed to open pcm device (hw:1,0): Device or resource busy
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed

** (audacious:11025): WARNING **: oss_open(): Failed to open audio device (/dev/dsp1): Device or resource busy
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

** (audacious:11025): WARNING **: oss_open(): Failed to open audio device (/dev/dsp): Device or resource busy
MADPlug-Message: failed to open audio output: XMMS reverse compatibility output plugin

(audacious:11025): GLib-CRITICAL **: g_thread_join: assertion `thread->joinable' failed


```

How do I get Audaciuos to work with my new sound card?

---

### Post by eggdeng on 2008-08-23
> ALSA with device 0,0, device 0,1 etc
Try running
```
asoundconf list
```
to see how alsa identifies the available sound cards. Then run
Code:
```
asoundconf set-default-card xyz
```
where xyz is the name of the card you want to use, according to the output of the 1st command.
Reboot for changes to take effect.

---

### Post by Daan on 2008-08-24
Thanks for your suggestion, eggden. It does not help, however. Now Audacious still doesn't play anything, and gives no error messages.

In mean time I am starting to like Amarok. It uses the xine Engine which in Amarok is configured to use the the Alsa plugin.

---

### Post by linuxchemist on 2008-10-11
I had the same problem and solved it with the following steps:

1) Uninstall audacious and remove all relative settings and directories:
sudo apt-get remove --purge audacious
rm -r .audacious/ /home/%username%/.config/audacious /home/%username%/.cache/audacious home/%username%/.local/share/audacious /home/%username%/.local/share/applications/audacious

2) Install PulseAudio
Go to the Add-Remove programs and install
PulseAudio Device Chooser
PulseAudio Volume Control
PulseAudio Volume Meter (Playback)
PulseAudio Volume Meter (Capture)
PulseAudio Manager

3) Install audacious again
sudo apt-get install audacious 

4) Run "Appcliations"-> "Multimedia" -> "PulseAudio Device Chooser"
or type on terminal padevchooser and run
On tray icon will appear PulseAudio applet

5) Now run audacious and in preferences in Audio Output choose PulseAudio Output Plugin
Now open some mp3 song with audacious and while it plays without sound make left click on tray icon of PulseAudio Applet and choose Volume Control. on card "Playback" choose your device and sound will appear immediately. Good luck!

---

