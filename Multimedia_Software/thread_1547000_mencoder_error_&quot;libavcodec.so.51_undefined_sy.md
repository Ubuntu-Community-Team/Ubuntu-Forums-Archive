---
title: "mencoder error: &quot;libavcodec.so.51: undefined symbol: faacDecDecode&quot;"
date: 2010-08-06
forum: Multimedia Software
---

### Post by segalerez on 2010-08-06
Hi,

I'm trying to use mencoder and get these errors:
```
/>mencoder
mencoder: /usr/local/lib/libavformat.so.52: no version information available (required by mencoder)
mencoder: /usr/local/lib/libavutil.so.49: no version information available (required by mencoder)
mencoder: /usr/local/lib/libavutil.so.49: no version information available (required by /usr/lib/libavcodec.so.52)
mencoder: /usr/local/lib/libavutil.so.49: no version information available (required by /usr/lib/libpostproc.so.51)
mencoder: /usr/local/lib/libavutil.so.49: no version information available (required by /usr/lib/libswscale.so.0)
mencoder: symbol lookup error: /usr/local/lib/libavcodec.so.51: undefined symbol: faacDecDecode

```

I've tried reinstalling faac, libavcodec51 and mencoder with no success.

I'm attaching ldd which I've read helped advanced users help newbies in other forums...
```
/usr/local/lib>ls -la | grep libavcodec
-rw-r--r--  1 root root  5686754 2008-03-14 05:04 libavcodec.a
lrwxrwxrwx  1 root root       21 2008-03-14 05:04 libavcodec.so -> libavcodec.so.51.51.0
lrwxrwxrwx  1 root root       21 2008-03-14 05:04 libavcodec.so.51 -> libavcodec.so.51.51.0
-rwxr-xr-x  1 root root  4284384 2008-03-14 05:04 libavcodec.so.51.51.0
/usr/local/lib>ldd libavcodec.so
libavcodec.so          libavcodec.so.51       libavcodec.so.51.51.0
/usr/local/lib>ldd libavcodec.so.51
	linux-vdso.so.1 =>  (0x00007fff67ad5000)
	libavutil.so.49 => /usr/local/lib/libavutil.so.49 (0x00007f13cb302000)
	libz.so.1 => /lib/libz.so.1 (0x00007f13cb0eb000)
	libm.so.6 => /lib/libm.so.6 (0x00007f13cae67000)
	liba52-0.7.4.so => /usr/lib/liba52-0.7.4.so (0x00007f13cac59000)
	libfaac.so.0 => /usr/lib/libfaac.so.0 (0x00007f13caa47000)
	libfaad.so.0 => /usr/lib/libfaad.so.0 (0x00007f13ca806000)
	libgsm.so.1 => /usr/lib/libgsm.so.1 (0x00007f13ca5f8000)
	libmp3lame.so.0 => /usr/lib/libmp3lame.so.0 (0x00007f13ca380000)
	libvorbisenc.so.2 => /usr/lib/libvorbisenc.so.2 (0x00007f13c9fa4000)
	libvorbis.so.0 => /usr/lib/libvorbis.so.0 (0x00007f13c9d77000)
	libx264.so.54 => /usr/lib/libx264.so.54 (0x00007f13c9aef000)
	libxvidcore.so.4 => /usr/lib/libxvidcore.so.4 (0x00007f13c97e0000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f13c95c3000)
	libc.so.6 => /lib/libc.so.6 (0x00007f13c9240000)
	libogg.so.0 => /usr/lib/libogg.so.0 (0x00007f13c9038000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f13cbc46000)
/usr/local/lib>

```

Thanks,

Erez

---

### Post by mc4man on 2010-08-06
Well it appears you have installed ffmpeg as shared to usr/local and are trying to use a repo mplayer/mencoder build which depends on the shared ffmpeg libs.

That's not going to work out so well, so remove mplayer and mencoder and build yourself fresh versions from a current mplayer source. ( and possibly a new x264 first.

In that case ffmpeg support will come from an internal source and what you have or have done with ffmpeg system wise will be irrelevant.


Edit: or see here - made mention of using a ppa mplayer/mencoder, should work as well.

[http://ubuntuforums.org/showthread.php?t=1546254](http://ubuntuforums.org/showthread.php?t=1546254)

---

### Post by segalerez on 2010-08-07
Thanks!

Could you attach a link to mencoder build instructions? I've never compiled before...

Meanwhile I tried removing ffmpeg, and now mencoder seems to be missing libfaad.0 which I can't install using synaptic since it says: 

```
libfaad0:
Package libfaad0 has no available version, but exists in the database.

```

```
/>mencoder
mencoder: error while loading shared libraries: libfaad.so.0: cannot open shared object file: No such file or directory

```

Thanks,

Erez

---

### Post by mc4man on 2010-08-07
> I've never compiled before...
Somehow you've installed ffmpeg libs to /usr/local - do you use ppa's 

Otherwise I'm guessing you're on Intrepid - while I've never used a release that's reached 'end of life' I'd think you may need to adjust your sources to continue to use. (as far as adding packages

See here for a mention how - post 3
[http://ubuntuforums.org/showthread.php?t=1496269](http://ubuntuforums.org/showthread.php?t=1496269)

---

### Post by segalerez on 2010-08-07
I'm using lucid, not sure how the libs got there though. Here's what I've done:

```

cd /usr/local/lib
mkdir libav_files
mv libav* libav_files/
sudo apt-get remove libavcodec52
sudo apt-get install mencoder

```

And It works!

Thanks for your help,

Erez.

---

### Post by mc4man on 2010-08-07
> not sure how the libs got there though
I'm using lucid,
That is a bit of a mystery then, the libav* versions you had in /usr/local were from intrepid (51

At least you're back on track...

---

### Post by areskz on 2010-12-22
```

cd /usr/local/lib
mkdir libav_files
mv libav* libav_files/
sudo apt-get remove libavcodec52
sudo apt-get install mencoder

```

It helped me too, thanks!

---

### Post by MeXiCaN_At_LaRgE on 2011-04-03
i have the same prob and i tried like 3 time using the code above but when i hit y and enter, its says abort...
help anyone???

---

