---
title: "Dynamic Range Compression"
date: 2008-09-02
forum: Multimedia Software
---

### Post by forbjok on 2008-09-02
Does anyone know if there is any utility, preferably one that is available for installation through the Ubuntu repositories, that is capable of performing Dynamic Range Compression on audio files?

To immediately clear up any possible misunderstandings, what I'm talking about is [dynamic range compression]("http://en.wikipedia.org/wiki/Dynamic_range_compressionhttp://en.wikipedia.org/wiki/Dynamic_range_compression") - this is _NOT_ the same as space compression (such as encoding to mp3, etc).

What I'm looking for is a utility, preferably commandline-based, that can perform DRC on files, and save the result back to a file. (for example: decode an mp3, perform DRC on the audio, and re-encode to a new mp3)

Thanks in advance. :)

---

### Post by jpkotta on 2008-09-04
Audacity has a compressor/expander, but it's not scriptable as far as I know.

---

### Post by kbmorris on 2008-11-06
I see that the thread is a little old.  I believe this is what you are looking for if you haven't found it yet...

[http://packages.ubuntu.com/gutsy/sound/sox](http://packages.ubuntu.com/gutsy/sound/sox)

Regards,

      Kevin

---

### Post by markbuntu on 2008-11-06
There are a number of dynamic compression utilities available in the LADSPA plugin set. If you are using ardour/jack or some other jack application, they are available in jack-rack.

If you just want to normalize the volume of your mp3s or something like that, some players like audacious and xmms and I think amarok have plugins for that.

---

