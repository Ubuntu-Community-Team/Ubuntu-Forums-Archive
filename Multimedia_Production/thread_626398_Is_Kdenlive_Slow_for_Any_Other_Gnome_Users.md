---
title: "Is Kdenlive Slow for Any Other Gnome Users"
date: 2007-11-29
forum: Multimedia Production
---

### Post by MCrittenden on 2007-11-29
I know Kdenlive is KDE based an requires KDE libs that my gnomey Ubuntu isn't used to, but this is terrible. Every time I click just about anything, the screen greys for about 10 seconds before performing the action. The only other KDE app I've used is amaroK which didn't give me any trouble.

I'm on a DELL 9300 with 1GB RAM, 1.8GHZ processor, ATi video card with fglrx on Ubuntu 7.10.  Anyone else having this trouble or do I have some kind of problem? If there are some terminal commands I can run to get you some more information just let me know.

---

### Post by MCrittenden on 2007-12-02
bump.

---

### Post by ugm6hr on 2007-12-17
I have just started to play with Kdenlive on Ubuntu7.10 (Gnome).

I think it's a fantastic program for easy editing, apart from the fact that it spontaneoulsy closes itself down every now and then.

On my AMD Turion 2GHz, 1GB RAM, ATI 1100 graphics card, it runs pretty slowly too.

Presumably it is something to do with manipulating large video files with insufficient RAM or Graphics RAM?

---

### Post by eye208 on 2007-12-18
Responsiveness of video editing applications is often related to the [GOP](http://en.wikipedia.org/wiki/Group_of_pictures) length of the format being edited. For example, in H.264-encoded video there may be hundreds of P- and B-frames between two I-frames. Frame accurate editing is very slow in this case because seeking a particular frame in the stream may involve decoding dozens or hundreds of P-frames.

In order to improve responsiveness, use intraframe video, i.e. video encoded without P- or B-frames. DV and MJPEG are intraframe-based by nature, but you can also encode MPEG-2 and MPEG-4 streams with I-frames only.

FFMPEG will produce intraframe-based video if you use the -intra option. MEncoder accepts several codec-specific options to suppress creation of P- and B-frames. For example, -x264encopts keyint=0 will generate H.264 intraframe streams. The resulting files will be larger than usual. Since they are meant for editing and not for distribution, try to avoid loss of quality at this early stage, e.g. by setting the -sameq option with FFMPEG.

---

### Post by ugm6hr on 2007-12-18
> **eye208 said:**
> In order to improve responsiveness, use intraframe video, i.e. video encoded without P- or B-frames. DV and MJPEG are intraframe-based by nature, but you can also encode MPEG-2 and MPEG-4 streams with I-frames only.


This is really interesting, but makes perfect sense.

My problem is that the video I am working with was created on someone else's camcorder, and I'm not sure how it creates DVDs.  Is it possible (or reasonable) to convert a DVD movie into intraframe images only?

Out of interest, if this is the case, presumably it is the processor speed that is of importance, rather than RAM (or graphics RAM)?

---

