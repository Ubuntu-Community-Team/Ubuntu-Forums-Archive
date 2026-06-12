---
title: "Streaming from one pulseaudio pc to another"
date: 2010-03-31
forum: Multimedia Software
---

### Post by ltk5 on 2010-03-31
Hello!
I am trying to get the music my desktop computer is playing to be streamed to my laptop which is in another room. Both are connected to a router and I found that this should be relatively easy with pulseaudio.

I was following this tutorial: [http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio](http://x4.6times7.org/dokuwiki/doku.php/devlog/blog/streaming_on_ubuntu_8.04_with_pulseaudio) installed all the software it suggested and selected the options for the server (my desktop pc) and the client (my laptop).

However, I avoided this (because then my desktop speakers wouldn't make a sound): > How to avoid Time Delay between Server and Client

If your sound server plays his own stream through his speakers, then it should use its own network stream (loopback) instead of the sound from the original audio device. Otherwise there is a slight delay between the audio streams on client and server. So this doesn't really

    *
      Select Create separate audio device for Multicast/RTP
    *
      Check Loopback audio to local speakers
    *
      Check Enable Multicast/RTP Receiver (to allow loopback)
    *
      Start the sound on your application, let's say, play a song on Amarok
    *
      Then open pavucontrol and on the Playback tab, right click on the audio stream (e.g. Amarok) and click on Move Stream&#8230; and then on RTP Multicast Sink


I also set up the client side, with no effects. The laptop can be found with padevchooser but not the desktop (which is what I wanted).

The site also suggest to use [this]("http://www.pulseaudio.org/wiki/PerfectSetup") but I don't even know where (and why) to run the models. Some are already found with padevchooser's Manager.

---

### Post by ltk5 on 2010-03-31
Following this [http://equima.pfpfree.net/2009/sharing-sound-between-pulseaudio-instances-in-ubuntu-karmic-9-10/](http://equima.pfpfree.net/2009/sharing-sound-between-pulseaudio-instances-in-ubuntu-karmic-9-10/) everything looks ok. Still no sound. I also opened the port 4713 on Firestarter (desktop PC).
Maybe the router is blocking something?

---

### Post by ltk5 on 2010-04-01
any ideas? should I add more info?

---

### Post by 00arthuryu on 2010-05-05
i've never managed to get pulseaudio loopback to work with firestarter, it seems to just dislike pulse, however, if you install gufw and enable your desktop and laptop's IPs it should work.

However, you should have this problem:
[http://ubuntuforums.org/showthread.php?t=1300722&highlight=pulseaudio+multicast](http://ubuntuforums.org/showthread.php?t=1300722&highlight=pulseaudio+multicast)

---

