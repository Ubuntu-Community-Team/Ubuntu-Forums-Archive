---
title: "Getting Zoom R16 to work as an interface"
date: 2010-02-09
forum: Multimedia Software
---

### Post by JJRJ on 2010-02-09
Hello Ubuntu users,

I've recently purchased the Zoom R16 Recorder, which can be used as an audio interface. Unfortunately there is no linux drivers available, but I'm hoping that there's something I can do to make it work.  

Is there anybody in here who has any experience with the R16 and Linux or knows how to fix the problem? Any help will be appreciated. Thank you!

Best regards,


Jim

---

### Post by no2498 on 2010-02-09
this may or may not help at all
but not changing any thing on your computer
open a terminal type ( gstreamer-properties ) click enter
it opens in audio you can try some settings in that
hope it helps some good luck

---

### Post by joeyimscared on 2010-10-02
Any luck getting the R16 up and running? I unfortunately lack the skills to help you out, but I would love to use the R16 as a control surface with Ardour.

---

### Post by mightysween on 2010-11-08
Still no linux support from Zoom. I guess it is time to take matters in our own hands...that is the Linux way, after all. :P

There are a few people working on it in the Alsa community...

[http://www.spinics.net/lists/alsa-devel/msg39181.html](http://www.spinics.net/lists/alsa-devel/msg39181.html)

but so far no one seems to have succeeded.

I contacted Samson in the US and Zoom in Japan to see if either can provide the source code for the Mac OS-X driver. I think having access to a unix-type driver source might help in developing and compiling one for Linux.  It would at least give definite hardware addresses and such...

Samson responded and said they did not have access to the source, and I am still awaiting a response from Zoom Japan.

I will post if anything develops.

---

