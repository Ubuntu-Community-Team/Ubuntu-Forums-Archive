---
title: "How to get flac encoding working with k3b"
date: 2008-10-19
forum: Multimedia Software
---

### Post by maturin on 2008-10-19
Anyone know how to get flac encoding to work with k3b?  

I do have flac installed (and can create flac files), but no matter what I try, k3b seems unable (or unwilling?) to rip to flac (from CD) and gives "Command failed".

I've noted that flac is not listed under "Audio Encoders" in the plugin configuration (it is listed as a decoder).  I did try adding the command for flac encoding under external audio encoders, but no luck.  

In desperation I've even compiled the latest version of k3b, making sure that all the appropriate libraries where configured into the compilation.  Still no luck.

Anyone have any advice?

Thanks.

(mp3, ogg, etc. seem to work just fine)

---

### Post by Yellow Pasque on 2008-10-19
So you have all of the libflac packages installed?

---

### Post by maturin on 2008-10-20
Yes, at least all that come up under "libflac" in adept.

---

### Post by ventper on 2009-02-13
as of intrepid, kde 4.2;

**synaptic** tells me i have(**flac** search);
flac
libflac++6
libflac8
libtag1c2a
libtunepimp5
libtunepimp5-mp3
soundconverter
vorbis-tools

a post on kubuntuforums.net mentioned **grip**, 
so i installed that as well before checkin if k3b would
offer me flac encoding.

i've tested encoding via k3b(workin) and playback via amarok(workin)

---

