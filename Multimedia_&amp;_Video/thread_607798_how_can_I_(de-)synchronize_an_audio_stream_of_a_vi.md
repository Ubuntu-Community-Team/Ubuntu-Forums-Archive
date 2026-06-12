---
title: "how can I (de-)synchronize an audio stream of a video?"
date: 2007-11-09
forum: Multimedia &amp; Video
---

### Post by mamadu bwana on 2007-11-09
Hi,

Most of the videos I get off the Internet end up having a badly synchronized audio and video stream with the video preceding the audio by roughly 3-5 seconds. How can I fix that? Is there a video player in GNU/Linux which would make it possible to play a watch a video with a 4 seconds delay for the video stream (or an audio stream moved forward by 4 sec).

I tried doing that with VLC which in its advanced audio options has an "Audio desynchronization compensation option" in milliseconds. I tried +5000 and -5000 but in one case I lost the video signal altogether while in the other is the audio which was gone.

Can I tweak this with Totem or Mplayer or any other application?

Many thanks,

Mamadu

---

### Post by Nano Geek on 2007-11-09
Did you try [Avidemux]("http://fixounet.free.fr/avidemux/")? 
I haven't used it before, but it looks like it might solve your problem.

---

### Post by mamadu bwana on 2007-11-09
> **asjdfwejqrfjcvm msz34rq33 said:**
> Did you try [Avidemux]("http://fixounet.free.fr/avidemux/")? 
I haven't used it before, but it looks like it might solve your problem.

I haved used avidemux to change video formats, but I have not found a way to advance the audio stream by a number of seconds :-(

---

### Post by disturbedite on 2007-11-09
i was gonna recommend avidemux.  there is an option right there on the front of the app to mess with audio delay!  there is also a filter to do it in the filters sections as well in the audio options.

---

### Post by mamadu bwana on 2007-11-09
sorry, but for the life of me I do not see the option you are referring to.  can you please show me how I could take, say, an mp4 video file and delay the audio by 4 sec?

thanks!

---

### Post by rsambuca on 2007-11-09
Check the box that says "shift" right under the Audio section.  Then adjust the number in milliseconds for a/v timeshift.

You can also do it in one of the filter sections.  No offense, but there is an excellent manual and webpage wiki as well.

---

### Post by mamadu bwana on 2007-11-10
> **rsambuca said:**
> Check the box that says "shift" right under the Audio section.  Then adjust the number in milliseconds for a/v timeshift.

I have no idea how I could have missed this:confused:

> **rsambuca said:**
>   No offense, but there is an excellent manual and webpage wiki as well.

guilty as charged and begging for the clemency of the jury :(

Thanks for everything!

---

