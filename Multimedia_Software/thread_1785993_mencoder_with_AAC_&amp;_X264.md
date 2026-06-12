---
title: "mencoder with AAC &amp; X264 ?"
date: 2011-06-19
forum: Multimedia Software
---

### Post by pieroxy on 2011-06-19
Hi there,

I wanted to transcode some of my videos for my iPhone and I am stumbling on this issue. Here is what I did:
[LIST=1]
[*]Checked ou latest mplayer code
[*]install libfaac-dev
[*]build mplayer
[/LIST]

Up to that point everything is find with libfaac. I can encode using faac codec. Now for x264 I tried:

[LIST=1]
[*]installing the x264 & libx264-dev packages
[*]configure mplayer
[/LIST]
but configure still doesn't detect x264. So I tried:


[LIST=1]
[*]I pulled the latest x264 codec from sources
[*]removed x264 & libx264-dev packages
[*]configure && make && make install
[/LIST]

configure for mplayer still doesn't detect x264.

In both cases, adding a --enable-x264 fails the build.

Any help appreciated.

---

### Post by andrew.46 on 2011-06-19
You might be better to use FFmpeg for your files and follow this guide:

HOWTO: Install and use the latest FFmpeg and x264
[http://ubuntuforums.org/showthread.php?t=786095](http://ubuntuforums.org/showthread.php?t=786095)

If you are set on MEncoder, remembering that this has not been developed for quite some time now, the steps you have described should get you x264 encoding. Certainly it works on my case:

```

andrew@skamandros~$ **[COLOR="Red"]mencoder -ovc help[/COLOR]**
MEncoder SVN-r33597-4.5.3 (C) 2000-2011 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
   libdv    - DV encoding with libdv v0.9.5
  **[COLOR="Red"] x264     - H.264 encoding[/COLOR]**

```

Have a look in config.log for the section:

```
============ Checking for x264 ============
```

and the errors should give a clue as to what is going wrong. I note currently you will need x264 >= 115 which is current git at the moment.

---

### Post by pieroxy on 2011-06-19
Seems to be working now, thanks.

So, the libx264-dev in the Natty repos is too old a version  for the latest mplayer.

I then installed the latest x264 from git, but what I missed last time is:
```
make install install-lib-dev install-lib-shared install-lib-static
```

I just did make install.

Thanks. I didn't know about config.log.

---

### Post by andrew.46 on 2011-06-19
> **pieroxy said:**
> Seems to be working now, thanks.

So, the libx264-dev in the Natty repos is too old a version  for the latest mplayer.

Indeed, looks like Natty has 106 which is ancient in media terms :). Good to hear it is all working for you!

---

