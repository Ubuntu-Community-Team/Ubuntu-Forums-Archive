---
title: "Can't play certain .mp3 files"
date: 2007-03-27
forum: Multimedia &amp; Video
---

### Post by Porta-Chaves on 2007-03-27
I tried to play some musics I have on my Portable, but it says I don't have de codecs or something like that installed on the system...

where can i get these "codecs"

---

### Post by Spermy on 2007-03-27
Have you tried installing "easyubuntu" and using that to install the codecs?

Should be easy to find, as I managed to.

---

### Post by Porta-Chaves on 2007-03-27
where can i get that??

---

### Post by Spermy on 2007-03-27
This should do the trick....

[http://easyubuntu.freecontrib.org/get.html]("http://easyubuntu.freecontrib.org/get.html")

---

### Post by Porta-Chaves on 2007-03-27
I select to install free codecs, it downloads fine but then it gives an error:

(translation from portuguese)
Not possible to make changes.
Need to resolve broken packages

---

### Post by Porta-Chaves on 2007-03-27
I managed to install the following packages manually, by searching them in the synaptics:

gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-ffmpg
gstreamer0.10-plugins-bad
libxine-main1
sox
ffmpeg
vorbis-tools

This one I found but gave an error, saying that another package was needed but not installable:

gstreamer0.10-plugins-ugly-multiverse

And finally, the following i couldn't find:

gstreamer0.10-plugins-bad-multiverse
libxine-extracodecs
faad
lame
mjpegtools
libxvidcore4


help please?

---

### Post by mcduck on 2007-03-27
You need to enable universe & multiverse repositories to get non-free stuff: [http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")

---

### Post by Porta-Chaves on 2007-03-28
if I replace my sources.list with the one they provide if I do update he practicly wants me to install the intire list!

---

### Post by Porta-Chaves on 2007-03-28
now it's donwloading almost 1000 packages!! is it supposed to??

EDIT: now i see, you gave me the link for edgy but i'm using dapper :S, it's working now... SOLVED

---

