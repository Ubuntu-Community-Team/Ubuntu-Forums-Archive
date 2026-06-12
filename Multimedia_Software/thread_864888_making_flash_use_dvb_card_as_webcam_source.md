---
title: "making flash use dvb card as webcam source"
date: 2008-07-20
forum: Multimedia Software
---

### Post by sunset_studies on 2008-07-20
Hi,

I want to stream some video content over the internet from my dvb card. The thing is, I want to do it using existing flash 'broadcast yourself' services such as [http://justin.tv/](http://justin.tv/) . Is there some clever hack that I can do to make the flash player think my dvb card is actually a webcam, and therefore make the flash player allow me to use it as a source for broadcasting at justin.tv (for example). 

I've seen people stream stuff like sport on justin.tv and it never looked as though it was just a webcam pointing at a screen so I suspect there is some way to do what I want :)

Thanks

---

### Post by loell on 2008-07-20
the closest would be

[Another Video Loopback Device]("http://allonlinux.free.fr/Projets/AVLD/")

---

### Post by sunset_studies on 2008-07-20
> **loell said:**
> the closest would be

[Another Video Loopback Device]("http://allonlinux.free.fr/Projets/AVLD/")

This looks very promising, thanks! Do you have any experience with it? Flash detected it immediately, now it's just a matter of getting the video to /dev/video... can I achieve this with mplayer [tv channel command] > /dev/video?

edit: howto from that site doesn't even work for me:

After I set mencoder running I get the following when running sudo mplayer tv:// -tv "driver=v4l:device=/dev/video0:noaudio:outfmt=rgb24"


unable to open '/dev/video0': Device or resource busy

---

### Post by loell on 2008-07-20
yes, a few times in the past but i was only streaming an avi file and that was it.

---

