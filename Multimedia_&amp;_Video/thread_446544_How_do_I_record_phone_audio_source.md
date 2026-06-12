---
title: "How do I record phone audio source?"
date: 2007-05-17
forum: Multimedia &amp; Video
---

### Post by patrick728 on 2007-05-17
Hello Everyone,

My modem and sound card are working properly; I can dial numbers with the modem, and listen to MP3s with the sound card. When I call a number I hear the dial tone and dialing through my sound card speakers. The idea hit me that I could maybe capture that audio and save it, for example, to record saved messages in my voice mail.

Trouble is, no matter which recording device I select in Ubuntu's Sound Recorder, it records silence. I've played with the different capture source options in the mixer but no change.

Any suggestions?

Thanks for your help,
Patrick

---

### Post by josesanders on 2007-05-17
I don't know about Ubuntu's sound recorder, but I believe that Audacity can be used to capture sound like that.

---

### Post by patrick728 on 2007-05-18
Hey Jose,

Good idea, I had forgotten about Audacity. Installed it but wasn't able to record anything. Choosing different capture sources either recorded silence or resulted in an error.

I had to install the free version of Linuxant's modem driver for my softmodem. Could it have something to do with how their driver interacts with ALSA?

---

### Post by gradedcheese on 2007-05-18
```

arecord -l

```

lists record sources, is the modem one of them?  If so, you can arecord to a file...

---

### Post by patrick728 on 2007-05-29
Hey GradedCheese,

I tried both Audacity and arecord. Both can't seem to see the phone audio as a valid recording source. So no success so far. I guess I could try running a cable from the sound card output to the input. Might get terrible feedback or it just might work.

Wish the software could do it for me though. Sigh.

Thanks for your suggestions,
Patrick

---

