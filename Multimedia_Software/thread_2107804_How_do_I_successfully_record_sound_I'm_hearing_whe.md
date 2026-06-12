---
title: "How do I successfully record sound I'm hearing when I use my system to an audio file?"
date: 2013-01-22
forum: Multimedia Software
---

### Post by s3a on 2013-01-22
Ideally, I would prefer to use the terminal (and use arecord, for example) but, I am currently so extremely busy and stressed that I have no time to waste for learning anything right now so, could someone please suggest me a graphical application that will do this job easily?

I installed gnome-media and ran gnome-sound-recorder but, that didn't capture the audio in the audio file.

If you have a one-liner terminal command, that would be great too.

If more information is needed, just ask.

I would greatly appreciate any help!

---

### Post by tgalati4 on 2013-01-22
```
man aplay
arecord /dev/snd/pcmC0D0c
```

---

### Post by Habitual on 2013-01-22
This may help. not a one-liner and utilizes sox:

                                    [Record what comes out of your speakers]("http://www.bournetoraiseshell.com/article.php/20101116231547304?query=sox")

HTH? :)

---

### Post by s3a on 2013-01-22
Thanks for your answer.

I tried to save what is being captured to an audio file like so:
```
arecord /dev/snd/pcmC0D0c -t wav /tmp/test.wav
```

What am I doing wrong and how do I fix it?

---

### Post by tgalati4 on 2013-01-22
Are you sure pcmC0D0c is your current sound device?  I just pulled that from my system.  Your system may have different names for sound devices.

Play something and then look at the dates of the device files to see which one is being used.

tgalati4@Dell600m-mint14 /dev/snd $ ls -la
total 0
drwxr-xr-x   3 root root      240 Jan 22 16:15 .
drwxr-xr-x  15 root root     4160 Jan 22 19:31 ..
drwxr-xr-x   2 root root       60 Jan 22 16:15 by-path
crw-rw---T+  1 root audio 116,  8 Jan 22 16:15 controlC0
crw-rw---T+  1 root audio 116,  7 Jan 22 16:15 pcmC0D0c
crw-rw---T+  1 root audio 116,  6 Jan 22 20:06 pcmC0D0p  <===Hey, this one is different!
crw-rw---T+  1 root audio 116,  5 Jan 22 16:15 pcmC0D1c
crw-rw---T+  1 root audio 116,  4 Jan 22 16:15 pcmC0D2c
crw-rw---T+  1 root audio 116,  3 Jan 22 16:15 pcmC0D3c
crw-rw---T+  1 root audio 116,  2 Jan 22 16:15 pcmC0D4p

Looks like pcmC0D0p is my currently active sound device.

---

### Post by oldos2er on 2013-01-23
Moved to Multimedia & Video.

---

### Post by s3a on 2013-02-03
Sorry for the late reply.

The script you/Habitual linked to worked for me!

Thank you both for your answers.

---

