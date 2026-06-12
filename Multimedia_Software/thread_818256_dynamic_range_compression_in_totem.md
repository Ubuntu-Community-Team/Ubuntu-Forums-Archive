---
title: "dynamic range compression in totem?"
date: 2008-06-04
forum: Multimedia Software
---

### Post by VCSkier on 2008-06-04
I'm watching a video that has incredible fluctuation in volume levels, but it all needs to be audible (preferably without my ears bleeding).  Is there some sort of dynamic range compression, or even just a limiter, that I can turn on in totem.  Thanks.

---

### Post by jeffus_il on 2008-06-04
Here's a thread about it, it's called volume normalization.
[http://ubuntuforums.org/showthread.php?t=708277&highlight=normalization](http://ubuntuforums.org/showthread.php?t=708277&highlight=normalization)

Totem may be either based on Xine or Gstreamer, both seem to do it. Which Totem have you installed? See Help->About

Xine has an option to enable a52.dynamic.range in it's preferences section.

---

### Post by VCSkier on 2008-06-04
Thanks for the help jeffus_il.  I'm currently using the gstreamer based totem.

Regarding the thread you posted, that thread is for normalization which is to raise or lower the volume of an entire track, file, or folder of audio files.  I'm looking for something to dynamically adjust the volume of certain frames withing the file or track.  Both are very useful, and I'll keep that thread bookmarked for when I want to replaygain (normalize) a batch of files), but I don't think it's what I'm looking for now.

Thanks for the tip regarding the xine backend though.  I was hoping to stick with gstreamer, but if gstreamer can't do the trick, it sounds like xine can and that's where I'll be.

---

### Post by bni on 2009-06-16
Hello VCSkier

I have the same problem, did you find a solution?

I have tried xine a52 DRC (gives no effect), [http://vlevel.sourceforge.net](http://vlevel.sourceforge.net) (cant enable it)

---

### Post by VCSkier on 2009-06-18
Never did find a solution...  Sorry.

---

### Post by Darxus on 2009-08-16
It looks like this should be possible with alsa:
[http://www.google.com/search?q=alsa+dysoncompression](http://www.google.com/search?q=alsa+dysoncompression)

And xine:
[http://www.xine-project.org/faq#compressor](http://www.xine-project.org/faq#compressor)
(right click / show controls, and the infuriatingly tiny "setup window" button is all the way on the left, second from the bottom)

And was an "upcoming feature" of pulse audio a year ago:
[http://0pointer.de/blog/projects/jeffrey-stedfast.html](http://0pointer.de/blog/projects/jeffrey-stedfast.html)

But I haven't figured out how to get it to work.  

It sure would be nice to be able to hear all dialog without waking up neighbors (which is entirely what audio dynamic range compression is).

Lots of details on what it is:  [http://en.wikipedia.org/wiki/Dynamic_range_compression](http://en.wikipedia.org/wiki/Dynamic_range_compression)

---

### Post by Darxus on 2009-08-16
Filed a bug against ubuntu pulseaudio: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/414489](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/414489)

You could subscribe to the bug and click the "this affects me" thing.

---

