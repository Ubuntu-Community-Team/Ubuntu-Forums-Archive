---
title: "choppy 1080p video"
date: 2012-01-17
forum: Multimedia Software
---

### Post by Unguidedone on 2012-01-17
720p video plays fine
1080p lags pretty bad :\

I think its a hardware issue but how do i rule out its not software?

how do i trouble shoot this?

:D

---

### Post by papibe on 2012-01-17
Hi Unguidedone.

It is very difficult to make any comment without more information.

Which version of Ubuntu are you running?
What is your graphic card?
Do you have any proprietary driver installed?
What software are you using to reproduce the videos?
What are the codecs of the videos that can't be played smoothly?

Regards.

---

### Post by Unguidedone on 2012-01-17
> **papibe said:**
> Hi Unguidedone.

It is very difficult to make any comment without more information.

Which version of Ubuntu are you running?
What is your graphic card?
Do you have any proprietary driver installed?
What software are you using to reproduce the videos?
What are the codecs of the videos that can't be played smoothly?

Regards.


im using ubuntu 10.10
82945G/GZ Integrated Graphics Controller
N10/ICH 7 Family High Definition Audio Controller
no proprietary drivers
flash video (youtube)
mp4 at 1080p

---

### Post by papibe on 2012-01-18
Thanks.

I'm afraid you don't have the hardware to play full HD videos. In order to do that you need a GPU that supports video hardware acceleration.

You can get a very simple card like an Nvidia 210, or similar, for about $40. There are also AMD cards that support HD video, but I'm not very familiar with them.

Although AMD cards also offer acceleration, AFAIK only Nvidia supports acceleration for flash.

Regards.

---

