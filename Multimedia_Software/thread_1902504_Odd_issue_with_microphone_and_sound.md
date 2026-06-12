---
title: "Odd issue with microphone and sound"
date: 2011-12-30
forum: Multimedia Software
---

### Post by datanalytics.com on 2011-12-30
I am running Xubuntu 11.10 and I am finding quite an odd issue with my sound settings.

I have an external speaker and a mic embedded into a USB Webcam. The mic does not work but as I was (just) hearing a friend over Gtalk, she found out that she could hear the music I was playing in my computer.

So, she could hear my sound output, but not my voice! As is the output signal was routed directly into the microphone.

Any idea of what is going on in my system?

---

### Post by lidex on 2011-12-31
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.

---

### Post by datanalytics.com on 2011-12-31
I ran the script and the output is here:

[http://www.alsa-project.org/db/?f=fed5c6f28b3be2ddc0f67ec2fa976fec67754dd4](http://www.alsa-project.org/db/?f=fed5c6f28b3be2ddc0f67ec2fa976fec67754dd4)

Thanks for your reply and help!

---

### Post by datanalytics.com on 2012-01-01
More info concerning my sound issue:

1) I switch off my external speakers (so I cannot hear any sound).
2) I play some music (which I cannot hear).
3) Run "arecord -d 10 borrar2.wav"
4) After the recording, I switch on the speakers.
5) I run "aplay borrar2.wav" and I can hear the music that was playing at time (3).

It seems as if the output of my speakers were routed to my mic, doesn't it?

---

### Post by lidex on 2012-01-01
You're not using pulseaudio, correct? Does the webcam mic have a separate port or does it share the usb? If so it would require the snd-usb-audio module which is not being loaded.
You can try loading it thusly:
```
sudo modprobe snd-usb-audio
```
Then check for new devices:
```
aplay -l
```

---

### Post by ghoppa on 2012-02-11
I had the same issue and tried this solution. It works! thank you very much lidex!!!!

I have read about many people having this problem, we should mark this as solved so that others might use it, it's quite important!:)

---

