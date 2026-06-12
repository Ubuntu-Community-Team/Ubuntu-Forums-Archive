---
title: "How do I configure multiple audio I/O (USB &amp; Onboard)"
date: 2007-02-17
forum: Multimedia &amp; Video
---

### Post by richardq on 2007-02-17
I'm running Edgy and I recently got a Logitech USB headset. I can get it working to record and playback under Audacity (by setting the Audio IO sources to /dev/dsp1 within Audacity). However, I'd like to be able to use the USB headset as headphones to listen to my normal audio (music files, youtube videos etc..). I can't seem to figure out how to get the normal sound to come out the USB headset. 

Following the recommendations of a posting I found here, I did the following to show the modules I have:

```
richard@ubuntu:~$ cat /proc/asound/modules
 0 snd_hda_intel
 1 snd_usb_audio
```

Then I tried messing with the end of my /etc/modprobe.d/alsa-base file to change to priority of the devices, but it seemed to just mess things up when I restarted. I don't quite understand how two different audio devices (speakers and standard mic, and usb headphones and mic) are handled by the system. Can anybody give me a hand here?

---

### Post by mcduck on 2007-02-17
you only need to go to Audacious preferences and there select the audio hardware you wantto use..

---

### Post by richardq on 2007-02-17
> **mcduck said:**
> you only need to go to Audacious preferences and there select the audio hardware you wantto use..

From what I see Audacious is an audio player. I'm interested in getting the sound to play out of my USB headset system-wide. So if I change the audio preferences in Audacious, will this change the system so that something like a youtube video will play out my USB headset when I watch it in Firefox? 

For audio playback I use MOC, and I could probably configure that to play out my USB headset, but I wanted to change the audio output system-wide, not just in each app.

---

### Post by mcduck on 2007-02-17
Ok, have you looked in System/Preferences/Sound? I just tried it and was able to switch my system sound from sound card to USB headset from there..

---

### Post by richardq on 2007-02-17
> **mcduck said:**
> Ok, have you looked in System/Preferences/Sound? I just tried it and was able to switch my system sound from sound card to USB headset from there..

I re-checked that and everything was set to autodetect. So I changed them all to USB Audio. Now it seems that some applications (like Banshee for instance) will use the headphones for audio output, while others like Gxine, Xmms and MOC will not, and still use the speakers. 

Also, changing all the System->Preferences->Sound settings to USB Audio does NOT get my browser (firefox) to play flash sound from sites like YouTube to play through the USB headphones. I'm not sure how apps like Firefox get their sound output device settings. 

You'd think changing them in the System menu would change the default output for all the applications not explicitly set otherwise.

I wonder if disabling my on-board audio would do anything. I'm not sure how I'd do that anyway without wrecking my system ;)

---

### Post by Jabran Asghar on 2007-02-17
Hi,

Seems we are in the same boat ([http://www.ubuntuforums.org/showthread.php?t=358748](http://www.ubuntuforums.org/showthread.php?t=358748). I have not found an answer to this problem. Only my laptop, I am able to use  USB headset and internal soundcard correctly (except for the volume control button of the USB headset!), but on my desktop, no way! I am desparately trying to get some sound out of it.

I ended up thinking the same that if some how I disable other sound cards, when using USB headset and vice versa then the problem could be solved ... how to do that? Does anyone has an idea?

Jabran

---

### Post by Jabran Asghar on 2007-02-17
I worked out something ... check [here]("http://www.ubuntuforums.org/showthread.php?p=2171700").

---

