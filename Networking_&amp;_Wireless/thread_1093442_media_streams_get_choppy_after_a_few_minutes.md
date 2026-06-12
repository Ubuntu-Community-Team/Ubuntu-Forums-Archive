---
title: "media streams get choppy after a few minutes"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by xjgnsdof on 2009-03-11
Server: Ubuntu Server Edition 8.10 with Xubuntu desktop
Client: Ubuntu Desktop Edition 8.10

When I want to stream videos, I hop on the client PC, SSH into the server PC, find the video I want to play, and open it in Totem. After a few minutes, it plays just fine, but then it either pauses or gets so choppy that it's unplayable. I can only play low-quality videos that I downloaded from YouTube without this stuttering or pausing.

I have Comcast Blast! service, which gives me anywhere from 10MB/s to 16MB/s and am not running any other downloads or uploads.

I have streamed video over the same network using a different computer with no problem. The other computer had a 7200RPM hard drive and Ubuntu Desktop 8.10. My current server PC has a 5400RPM hard drive, which may or may not be an issue.

What is slowing down my streams so much?

---

### Post by mhgsys on 2009-03-11
try playing with mplayer 
It has framedropping when you press d.
Also you can play it with a different video driver:
```

mplayer -vo x11 -zoom 

```

I think your network is slowing it down.
Do you have any firewalls installed?

---

### Post by xjgnsdof on 2009-03-11
I have no firewalls installed. I streamed a video in mplayer and, after about a 5-minute delay, it stuttered to the point of being unplayable. The screen flickered wildly, so I didn't bother turning on framedropping. It also gave the following error message: [AO_ALSA] Unable to find simple control 'PCM',0.

I tried again with Totem, this time launching Totem from the command line, and I got this output: (totem:32178 ): Gtk-WARNING **: Operation not supported by backend. There was also a long delay before playing.

---

### Post by andrew.46 on 2009-03-11
Hi,

When using MPlayer have you tried using the -cache option?

Andrew

---

### Post by xjgnsdof on 2009-03-11
I just plugged in my laptop/server into my router with an ethernet cable, and everything I play streams perfectly. I just had a hunch that was the problem.

Perhaps the LAMP stack on the laptop/server is cutting into my bandwidth for media streaming. Why else would wireless streaming be so bad on this laptop but decent on my other, non-server laptop?

---

