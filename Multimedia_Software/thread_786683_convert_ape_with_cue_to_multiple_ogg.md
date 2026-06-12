---
title: "convert ape with cue to multiple ogg"
date: 2008-05-08
forum: Multimedia Software
---

### Post by Tarvok on 2008-05-08
I was wondering what the simplest way to convert a single ape file with a cue file into multiple ogg files is. I can play it in mplayer, but I'd like to add it to my Rhythembox library..

---

### Post by foresto on 2008-05-08
I would start by converting your Monkey's Audio file to a format that is more widely supported, like FLAC.  I use the [shntool]("http://etree.org/shnutils/shntool/") package (available through the ubuntu repositories) for this.  For Monkey's Audio support, shntool requires the mac program to be in my path.  I had to build mac manually from the source code on [this page]("http://supermmx.org/linux/mac/").  (Look for a tarball called something like "mac-*.tar.gz")

---

### Post by disturbedite on 2008-05-08
i wouldn't convert it to ogg as you will lose quality. with the lossless ape format it keeps the original source quality.
you could convert it to flac (another more widely used lossless format) & not lose any quality, like foresto said.
unfortunately, i don't know of any programs that can do this.  i'm sure there are some that can, but i just don't know of them as i usually burn these types of files (audio+cue) to disc right away.

i used to use cdwave editor on windows to do what you want to do though...

---

### Post by gladstone on 2008-05-08
I followed this guide successfully when I converted all my ape collection to flac:

[http://aidanjm.wordpress.com/2007/02/04/converting-monkey&#8217;s-audio-ape-files-to-flac-in-ubuntu/](http://aidanjm.wordpress.com/2007/02/04/converting-monkey&#8217;s-audio-ape-files-to-flac-in-ubuntu/)

Flac would be the better choice in the long run.

---

### Post by Tarvok on 2008-05-08
I suppose I'll keep it as a flac for a while. I'll likely end up wanting to compress it further, as I'll likely end up with flacs eating up space, but for now, I have plenty of extra space.

Is there any way to split the flac into individual song files (as per the cue file)? I've used [another method]("http://gimpel.gi.funpic.de/wiki/index.php?title=Howto:convert_ape_to_wav/mp3/ogg_on_Linux#cueape.sh") to do this with an ogg file (heh, it appears my original problem is solved), but I am digging the fidelity of the flac.

---

### Post by disturbedite on 2008-05-09
technically speaking, flac is better, basically cuz it has wider support across software & hardware.

---

