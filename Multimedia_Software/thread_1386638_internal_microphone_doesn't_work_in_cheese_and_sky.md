---
title: "internal microphone doesn't work in cheese and skype"
date: 2010-01-20
forum: Multimedia Software
---

### Post by engzks on 2010-01-20
I am using UNR 9.10

Sound recording from build-in mic was fine in skype and cheese after i installed UNR in my Acer Aspire One 110L in early December last year. 

But somehow, i just realized that my sound recording was not functioning when i use skype this morning.

(i don't know since when this problem occur as i never use skype and cheese in past few weeks and i did update a few time from synaptic and install ubuntu-boot kernel)

just now i remove ubuntu-boot and reinstall the 2.6.31-17-generic kernel and run

sudo dpkg-reconfigure pulseaudio

but skype and cheese still does not record from build in microphone but only record from external microphone.

One weird thing is Sound recorder do record from both the build-in mic and external mic.

i tried "parec -r test.wav" and "parec -p test.wav" and it also record from both mic.

Anyone know how to configure my netbook so that the internal mic work on skype?

---

### Post by engzks on 2010-01-20
Now i realize that it is not no sound but it is actually the recording volume is very low in skype and cheese but it is alright else where.

if i set the mic boost in alsamixer to maximum and the input volume (in the "Input" tab in "Sound Preferences") to maximum, i manage to record some very very soft sound in cheese.

Anyone know where to set the recording volume?

---

### Post by engzks on 2010-01-22
sloved

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055)

---

### Post by tubunu on 2010-06-26
> **engzks said:**
> sloved

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/433055)

Thanks for the link, the sound in Skype works now!

---

### Post by Chiapo on 2010-10-08
Since nobody has added what the above link contains, I thought I'd add it here:

At the end of the discussion, a suggestion is made to invoke the alsamixer from terminal, navigate to the "Mic-boost" & "Capture" areas by using the [TAB] key, use the left|right arrow keys to select individual elements, & the up|down arrow keys to adjust levels.

```
alsamixer
```

I followed the instructions in this thread, but failed to follow the link shared above, thus had no sound from my mic until running alsamixer.

Thanks for sharing!

---

