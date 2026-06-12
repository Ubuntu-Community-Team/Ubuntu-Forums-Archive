---
title: "USB headphones doesn't play flash audio (youtube) and VLC audio"
date: 2009-02-22
forum: Multimedia Software
---

### Post by rahunar on 2009-02-22
Hi,

I am using Microsoft Lifechat usb headphones for audio in 8.10. At first it is utter chaos with so many mixers and there is no sound from either laptop speakers or headphones. Then took advice in several help threads and removed everything that is pulse audio. In preferences-sound I put everything to Microsoft Lifechat Lx-3000 USB audio (ALSA) for everything and everything is working fine. When I use my headphones I gt sound in my head phones and when I dont I get sound in my laptop speaker. However flashaudio (youtube) and VLC still play sound in PC speaker ever when I use USB headphones. I want everything sound from the laptop to be played in my USB headphones when I use them. Any help in this regard will be appreciated. Thank you.

P.S.: I now have three sound mixers installed:

          HDA Intel (Alsa mixer)
          Microsoft LifeChat LX-3000 (Alsa mixer)
          Realtek ALC268 (OSS Mixer)

---

### Post by markbuntu on 2009-02-22
Your first mistake was removing pulseaudio because it is about the only reasonable way to handle more than one hardware sound device.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by rahunar on 2009-02-24
> **markbuntu said:**
> Your first mistake was removing pulseaudio because it is about the only reasonable way to handle more than one hardware sound device.

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
Hi markbuntu,

Thanks very much. The thread you have specified solved everything and I am able to hear everything in my usb headphones. I have searched many threads but no one seems to have formulated such a nice set of instructions. The *pulseaudio device chooser* did the trick. Thanks a lot..............

---

### Post by kennyschiff on 2009-03-14
Was banging my head against the wall until I read this carefully, especially the section about "move the stream" in the Pulse volume control applet. for example, for me flash audio was going to my laptop speakers, not my external usb sound card. clicking on the playback tab, then right clicking on the alsa plug-in allowed me to move the stream to my usb device.

---

### Post by HermitZ on 2009-04-22
Thanks heaps, helped me fix my problem.

---

### Post by Cypher1101 on 2009-09-25
TYVM, my lifechat headset works perfectly now. This thread needs to be stickied if it isn't already. (There are a lot of Lifechat threads)

---

