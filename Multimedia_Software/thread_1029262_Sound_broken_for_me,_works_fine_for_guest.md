---
title: "Sound broken for me, works fine for guest"
date: 2009-01-03
forum: Multimedia Software
---

### Post by feedmecereal on 2009-01-03
I have had so many problems with audio since upgrading to 8.10. I thought it was fixed for the past couple of weeks until just now. I am finally fed up with it and I need help.

Sound seems to work fine when I first login but then goes mute after playing a few files. The strange thing is that I just discovered that it seems to work fine under the guest session.

I went through the post at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) and reinstalled alsa. Here is some output when I try to start alsamixer:
```
danny@danny-desktop:~$ alsamixer
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection terminated


alsamixer: function snd_ctl_open failed for default: Connection refused

```

I have PulseAudio applet installed and when I try to start the volume control it gives me the message "Connection failed: Connection terminated."

I don't know what else to include right now because I am just tired of messing with everything. Please tell me anything I might be forgetting.

---

### Post by shoeheight on 2009-01-07
This might not help you, but it works for me.

My sound cuts out intermittently while playing video (you didn't mention the source of your sound problems).  My video sound won't return until I play music on one of my music players (ie. rhythmbox).  It is annoying, but it works.

Because your sound works for your guest, it isn't a driver problem. it might come from inadvertently changing your volume controls. Ie. don't forget to check all the obvious things like your main system sound control, program sound control, and keyboard sound control.

Using Ibex.

---

### Post by linux_tech on 2009-01-07
It sounds like pulse audio is failing because it is missing a few updates.

You can either try to fix pulse audio by installing a few packages or remove it and go back to original alsa configuration.

---

### Post by linux_tech on 2009-01-07
Try installing libasound
```
sudo apt-get install libasound2

sudo apt-get install libasound2-plugins
```
then 
esound ```

sudo apt-get install esound

```
and oss
```

sudo apt-get install alsa-oss

```

change setting to alsa-
Preference->Sound on Device tab, change all audio options to ALSA,   (you can also sometimes use autodetect here)
Preference->Sound on Sounds tab, disable alert and sound effects,
On Preference->Session, uncheck PulseAudio Session Management option

you can stop pulseaudio with 
```
killall pulseaudio
or pulseaudio -k
```
Test sound to see if there is any difference

---

