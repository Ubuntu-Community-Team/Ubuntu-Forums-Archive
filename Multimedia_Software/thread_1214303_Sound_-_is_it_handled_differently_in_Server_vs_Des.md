---
title: "Sound - is it handled differently in Server vs Desktop"
date: 2009-07-15
forum: Multimedia Software
---

### Post by bmullan on 2009-07-15
I've been spending alot of time lately troubleshooting a variety of sound issues in Jaunty.   NOTE I'm not saying they are bugs just problems I've been having.

I've learned alot lately about Pulseaudio, used several great wiki posts (debian's perfect pulseaudio setup, etc).

However, I started wondering after spending time with Pulseaudio's
**pasuspender** as to why that's really needed regarding the sound device.

In particular... if I understood the purpose of **pasuspender** correctly it was to free up the sound device dsp for other apps to use.

But... that brought the question to mind about HOW does Ubuntu/Linux handle sound on a multiuser server where you could have contention for the sound device by several apps simultaneously from one or more applications or people.

On the Server version of Ubuntu/linux is the sound device virtualized or handled differently  than the Desktop version of the OS ?

Hope this question makes sense.

---

### Post by igorzwx on 2009-07-15
Let us better discuss OSS4

---

