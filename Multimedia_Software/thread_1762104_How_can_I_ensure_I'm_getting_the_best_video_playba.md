---
title: "How can I ensure I'm getting the best video playback performance?"
date: 2011-05-18
forum: Multimedia Software
---

### Post by Dr_Rent on 2011-05-18
First, the hardware in question: a [Shuttle XS35GT]("http://www.directron.com/xs35gt.html").

I'm trying to use this as a small media PC, but I'm not getting great performance out of it, and I'm not sure whether it's just because I haven't configured it properly for performance. Even playing a standard-def AVI file with MPlayer, I'm getting tearing and choppy playback. It's watchable, but annoying, and I fear it'll do even worse if I subject it to full HD (even though it's advertised as capable of playing 1080p video).

First, I've already installed the proprietary NVidia drivers. I found some online advice suggesting I use '-vo vdpau' with MPlayer, and that gives me some improvement. I also read about installing 'vdpau-va-driver', which I did via apt-get, but I'm not even sure what, if anything, installing that did.

I'm just wondering what I need to check to make sure I've got everything configured properly for best performance.

---

### Post by papibe on 2011-05-18
I helped my bother to configure a similar machine, with perfect 720p/1080p playback using XBMC.

The easiest way to run/test the nvidia hardware acceleration is install smplayer on top of mplayer. Then in SMplayer go to Options -> Preferences -> General -> Video -> Output Driver, and set it to vdpau. It just works.

For testing try any h.264 video like this [ones]("http://www.h264info.com/clips.html").

I hope it helps.

---

### Post by Dr_Rent on 2011-05-18
Well, setting -vo to gl_nosw speeds things up a bit. I don't see any more tearing with that setting. The thing is, I tried viewing a 720p and a 1080p video from the page you linked, and it runs both of them ridiculously poorly. The video cannot keep up with the audio at all. Absolutely unwatchable.

I decided to install XBMC to compare the performance, and it was an incredible difference. It could play even the 1080p video very well, (with the occasional dropped frame, but that was hardly noticeable). I wonder what kind of voodoo magic XBMC is performing to get such a ridiculous performance boost. It's great, but it doesn't look like XBMC provides a nice command line interface like MPlayer, which is really inconvenient for me. I really wish I could use MPlayer, but with some magical configuration that would get me the performance I see with XBMC. If anyone has any ideas, I'd love to hear them.

---

### Post by papibe on 2011-05-18
Could you post the logs of the video that is not playing smoothly? While playing it with SMplayer go to Options -> View Log -> MPlayer.

Regards.

---

