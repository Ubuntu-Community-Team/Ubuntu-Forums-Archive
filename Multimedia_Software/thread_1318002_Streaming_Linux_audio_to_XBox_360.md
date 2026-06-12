---
title: "Streaming Linux audio to XBox 360"
date: 2009-11-07
forum: Multimedia Software
---

### Post by Rob_H on 2009-11-07
I'm interested in streaming all audio from my Kubuntu box to my Xbox 360 (e.g. Pandora, Amarok, etc.). It seems to me that I need some combination of PulseAudio to get the audio onto the network and a UPnP AV MediaServer to make it visible to the XBox 360.

So I've got [PulseAudio](http://www.pulseaudio.org/wiki/PerfectSetup) installed with KDE and it seems to be working. I can see activity in the volume meter. Now, I assume I should use the RTP module to serve the audio onto the network, since the other network modules (native, ESOUND, and simple) seem aimed at serving only PulseAudio and ESOUND clients only. But is there an XBox 360-compatible [AV server](http://en.wikipedia.org/wiki/UPnP_AV_MediaServers) that can act as a proxy for an RTP stream? I've tried TwonkeyMedia, XBMC, and MediaTomb, but none of them seem capable of this. TwonkeyMedia can stream Shoutcast, so I know this kind of thing is possible in principle.

Any ideas? Or is there a simpler way to do what I'm trying to do?

---

### Post by tommynz1975 on 2009-11-07
a google for

ubuntu serv music 360 xbox

gave me these links have a look,
if they don't help try my google search words

**[HOWTO: Stream *music* to your *Xbox 360* - Page 2 - *Ubuntu* Forums]("http://ubuntuforums.org/showthread.php?t=794489&page=2")**

[http://ubuntuforums.org/showthread.php?t=794489&page=2](http://ubuntuforums.org/showthread.php?t=794489&page=2)

**[Xbox360Media - Community *Ubuntu* Documentation]("https://help.ubuntu.com/community/Xbox360Media")**

[https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media)

---

### Post by Rob_H on 2009-11-07
> **tommynz1975 said:**
> **[HOWTO: Stream *music* to your *Xbox 360* - Page 2 - *Ubuntu* Forums]("http://ubuntuforums.org/showthread.php?t=794489&page=2")**

[http://ubuntuforums.org/showthread.php?t=794489&page=2](http://ubuntuforums.org/showthread.php?t=794489&page=2)

**[Xbox360Media - Community *Ubuntu* Documentation]("https://help.ubuntu.com/community/Xbox360Media")**

[https://help.ubuntu.com/community/Xbox360Media](https://help.ubuntu.com/community/Xbox360Media)

These links don't answer my question. I already know uShare and TwonkeyMedia can be used to share a music library. That's not what I'm trying to do. I'm trying to pipe all audio from my Linux box to the XBox 360.

---

