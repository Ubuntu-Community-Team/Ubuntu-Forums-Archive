---
title: "Audacity and Snowball USB microphone"
date: 2008-08-27
forum: Multimedia Software
---

### Post by lduperval on 2008-08-27
In thread [http://ubuntuforums.org/showthread.php?t=736852](http://ubuntuforums.org/showthread.php?t=736852), someone explains that audacity records slowly with a Blue Snowball device.

I bought the same device and I see the same behaviour (Hardy, Audacity 1.3.3).

I tried using the GNOME sound recorder tool and it records at the proper speed, albeit with an annoying high-pitched sound.

I tried ardour but it doesn't allow recording with a digital device.

I tried compiling a newer version of audacity (1.3.5) to see if it fixed the issue, but it did not.

Is there another tool I can try to record with? If not, I'll have to go back to Windows to record. :(

L

---

### Post by markbuntu on 2008-08-27
You could try recording in ardour through a pulseaudio/jack sink. See my guide, the jack section is near the bottom:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Post 58 has some directions for getting a usb mic to work through the pulseaudio/jack sink. It might help. Pulseaudio may resample the input for you so it can be used by other apps.

---

### Post by littletinman on 2008-09-05
Jokosher

I'm planning on getting a hookup for my mixer so i can go straight into jokosher.

---

