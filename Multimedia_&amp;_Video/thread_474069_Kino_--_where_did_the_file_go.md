---
title: "Kino -- where did the file go?"
date: 2007-06-14
forum: Multimedia &amp; Video
---

### Post by scott_g on 2007-06-14
Hi,

I've tried many, many times to render different videos, using kino, in a xvid format to save space.  However, each time I render it, it says it completes fine, and takes a reasonable length of time, yet the file is nowhere to be found (even if I specify exactly where it should be saved; the file is not hidden either).  When I render the file in another format, say mpeg, it shows up in my home folder by default (like it should, I think).  Does anyone know where the file is going?  Or how I can access it?

Note: I know the xvid library is installed correctly as I can use it with avidemux and acid rip.

Thanks a lot,
Scott G.

---

### Post by reclusivemonkey on 2007-06-15
You could try stating Kino from the command line and see if you get any more helpful messages.

---

### Post by scott_g on 2007-06-16
Good idea; wish I had thought of that.  The output is below:

```

>> Export::activate()
>>> output rate is 48000, adjusted rate is 48000
>> on_main_window_unmap_event
>> on_main_window_map_event
[mp3 @ 0x876c7e8]Could not find codec parameters (Audio: mp1, 192 kb/s)
LAVF_header: av_find_stream_info() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
[mp3 @ 0x876c7e8]Could not find codec parameters (Audio: mp1, 192 kb/s)
LAVF_header: av_find_stream_info() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.

```

The 
> 
[mp3 @ 0x876c7e8]Could not find codec parameters (Audio: mp1, 192 kb/s)
LAVF_header: av_find_stream_info() failed
============ Sorry, this file format is not recognized/supported =============
=== If this file is an AVI, ASF or MPEG stream, please contact the author! ===
Cannot open demuxer.
 
looks promising; does anyone know what it means?  Am I missing a library?

Thanks a lot,
Scott

---

### Post by scott_g on 2007-06-18
Any ideas?  I'm almost certain its a software issue; does anyone have an idea as to what I should install?  I tried installing the lame library, but it didn't help.

Thanks again,
Scott

---

### Post by steevc on 2007-07-11
Scott,

I wish I could help, but I have exactly the same problem. From a few things I found via Google it looks like it could be an issue with the particular version of mencoder that I have.

I'm on kino 0.9.2, but version 1.0.0 is out. Perhaps that works better, but I have not installed it yet.

I did find that installing ffmpeg expands the types of formats you can export, but mencoder is still being used for Xvid. I want to use that format as it should be supported by my DVD player and I will be able to fit lots of home movies on a disk.

---

### Post by scott_g on 2007-07-12
Hmm,

I haven't made any progress.  I'm still hoping an update will fix it.  I'm still very interested in a fix if anyone knows how to fix it.

Thanks,
Scott

---

### Post by ph_gachoud on 2008-07-13
[mp3 @ 0xb7f9d110]Could not find codec parameters Audio: mp3, 192

solved the problem by installing lame encoder

---

