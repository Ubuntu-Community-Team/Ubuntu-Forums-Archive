---
title: "Profire 610 recognized by ffado mixer but not jack"
date: 2013-09-25
forum: Multimedia Software
---

### Post by jhawl on 2013-09-25
I have a M-Audio Profire 610 firewire audio interface.  It is recognized by the ffado mixer but not jack.  After following the directions found here: [https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204](https://help.ubuntu.com/community/UbuntuStudio/ProAudioIntro/1204) (see Firewire section), I start jack and get this message:

Could not connect to JACK server as client.
- Overall operation failed.
- Unable to connect to server.
Please check the messages window for more info.

Not sure what is going on.  Anybody have any ideas?

---

### Post by jhawl on 2013-09-25
It is now recognized in Jack by installing the low latency kernel.
```
sudo apt-get install linux-lowlatency linux-headers-lowlatency
```
But there is still no audio going from the Profire to either Audacity or Ardour or even jack-capture.  I can hear an instrument plugged into the audio interface thru headphones, but it seems as though the computer is not recognizing any audio input.

---

### Post by jhawl on 2013-09-25
Solved it! A stupid mistake on my part - I was using the power adapter when the Profire is powered solely thru the Firewire port. For some reason this prevented it from working properly. Everything works fine!

---

