---
title: "mplayer compile errors"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by soulfury on 2008-02-29
I'm trying to compile mplayer so it will make use of my dual core.  I thought I had solved all the deps via apt-get builddeps mplayer, but this is the output of my configure string && make && make install[LIST]
[*]mplayer.o: In function `main':
[*]mplayer.c.text+0x516f): undefined reference to `***_track'
[*]mplayer.o.data+0x55d: undefined reference to `fribidi_charset'
[*]mplayer.o.data+0x5610): undefined reference to `flip_hebrew'
[*]mplayer.o.data+0x564: undefined reference to `flip_hebrew'
[*]mplayer.o.data+0x5680): undefined reference to `fribidi_flip_commas'
[*]mplayer.o.data+0x56b: undefined reference to `fribidi_flip_commas'
[*]libao2/libao2.a(ao_v4l2.o): In function `play':
[*]ao_v4l2.c.text+0xce): undefined reference to `v4l2_write'
[*]libao2/libao2.a(ao_v4l2.o): In function `init':
[*]ao_v4l2.c.text+0xf6): undefined reference to `v4l2_fd'
[*]libmpcodecs/libmpcodecs.a(vf_vo.o): In function `control':
[*]vf_vo.c.text+0x393): undefined reference to `***_track'
[*]vf_vo.c.text+0x4e3): undefined reference to `***_track'
[*]libmpcodecs/libmpcodecs.a(vf_***.o): In function `put_image':
[*]vf_***.c.text+0x53c): undefined reference to `***_track'[/LIST]collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Any ideas?

---

### Post by soulfury on 2008-02-29
Nevermind.  make clean all fixed it.







> **soulfury said:**
> I'm trying to compile mplayer so it will make use of my dual core.  I thought I had solved all the deps via apt-get builddeps mplayer, but this is the output of my configure string && make && make install[LIST]
[*]mplayer.o: In function `main':
[*]mplayer.c.text+0x516f): undefined reference to `***_track'
[*]mplayer.o.data+0x55d: undefined reference to `fribidi_charset'
[*]mplayer.o.data+0x5610): undefined reference to `flip_hebrew'
[*]mplayer.o.data+0x564: undefined reference to `flip_hebrew'
[*]mplayer.o.data+0x5680): undefined reference to `fribidi_flip_commas'
[*]mplayer.o.data+0x56b: undefined reference to `fribidi_flip_commas'
[*]libao2/libao2.a(ao_v4l2.o): In function `play':
[*]ao_v4l2.c.text+0xce): undefined reference to `v4l2_write'
[*]libao2/libao2.a(ao_v4l2.o): In function `init':
[*]ao_v4l2.c.text+0xf6): undefined reference to `v4l2_fd'
[*]libmpcodecs/libmpcodecs.a(vf_vo.o): In function `control':
[*]vf_vo.c.text+0x393): undefined reference to `***_track'
[*]vf_vo.c.text+0x4e3): undefined reference to `***_track'
[*]libmpcodecs/libmpcodecs.a(vf_***.o): In function `put_image':
[*]vf_***.c.text+0x53c): undefined reference to `***_track'[/LIST]collect2: ld returned 1 exit status
make: *** [mplayer] Error 1


Any ideas?

---

