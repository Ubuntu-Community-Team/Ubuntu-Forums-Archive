---
title: "Converting VHS to Digital"
date: 2017-06-14
forum: Multimedia Software
---

### Post by GNUway Tech on 2017-06-14
I know this has already been gone over before in other treads, but I have never done this before. I have a VCR I am using in conjunction with a USB dongle to record home videos to my computer. It connects by RCA stereo patch wire.

It's taken me a little bit, but I've figured out how to use VLC to record the video. The only problem is, I am not getting any sound out of it. :confused: Is there a particular setting I need to change to hear sound.

---

### Post by Autodave on 2017-06-15
"It connects by RCA stereo patch wire."   I am assuming that this is a 3 wire RCA cable?

When recording, have you opened up the volume control center to see if the USB is recognized as an audio input?  Have you installed *pavucontrol* yet?

If *pavucontrol *is not installed, start there.

---

### Post by GNUway Tech on 2017-06-15
Yes, this is a 3 wire stereo cable.

I've just installed pavucontrol, and checked the sound settings in Ubuntu. Ubuntu is recognizing the USB plug as an input.

Should I be using a particular input level for the sound from USB???

---

### Post by Autodave on 2017-06-16
I have no idea. Try it and then crank it up some more until you (hopefully) get a signal. You can also raise the recording level in the volume control: input.

When you try to record, are you seeing the signal coming through the input section? You will want the recording leve as high as possible without exceeding 0db.

---

### Post by GNUway Tech on 2017-06-17
It took a lot of playing in the app settings, but the problem was the capture device audio setting. Thanks for your help, I really appreciate it.

---

