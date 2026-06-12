---
title: "Logitech C600 webcam, video yes mic no"
date: 2012-01-15
forum: Multimedia Software
---

### Post by alexisazen on 2012-01-15
Hi all,

I recently purchased a new webcam, Logitech C600. Although the video works great in Cheese and Skype, the mic input doesn't work in either the Sound Recorder or Skype. I am using Ubuntu 11.10. Any hints welcome. I see in the forum that a lot of people are having a hard time with their webcams, but for most people mic in Sound Recorder seems to work fine. Many thanks.

---

### Post by ajgreeny on 2012-01-15
Run ```
alsamixer
``` in terminal and check that the levels of inputs and outputs are not set too low.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Check that the mic is enabled in the capture page.  It will show
[COLOR=Red]L          R
CAPTURE[/COLOR]
beneath the mic column if enabled;  if not move to the mic column with cursor keys and hit spacebar to enable it.

---

### Post by alexisazen on 2012-01-15
[IMG]http://i39.tinypic.com/qxtksp.png[/IMG]

This was what was shown for this device in alsamixer.

Maybe there is a mix-up with pulseaudio?

---

### Post by ajgreeny on 2012-01-15
It is certainly worth looking in pulseaudio volume control in the sound and video menu to see if microphone is muted, as it can be.

---

### Post by sarahlizz3 on 2012-01-15
Might want to try some of these ideas, one of them worked for me:

[http://ubuntuforums.org/showthread.php?t=1860715](http://ubuntuforums.org/showthread.php?t=1860715)

---

### Post by papibe on 2012-01-15
Hi alexisazen.

I have a Logitech webcam pro 9000. In order to make the mic work in Skype, I have to change the sound settings before creating a chat.

I go to Sound Preferences -> Input. There it is usually set to 'Internal Audio Analog Stereo, but I change it to '0809 Analog Mono'. Which is my web cam microphone.

Hope it helps,
Regards.

BTW, the '0809' coincides with the USB id if my camera:
```
$ lsusb | grep -i logitech
Bus 002 Device 003: ID 046d:**0809** Logitech, Inc. 

```

---

### Post by jestal on 2012-01-20
the alsamixer worked for me.
i had to enable the mic.

Logictec C515 i think, it's not marked.

---

