---
title: "Ubuntu (7.10) -VLC media player will not play Nero 7 burned Data DVDs (mkv files)"
date: 2008-03-15
forum: Multimedia &amp; Video
---

### Post by spiritsongtress on 2008-03-15
]I burned about 12 dvds, all of which are MKV files which will not play on my Linux laptop (I am not sure if it because it a Nero 7 problem (which said it would play on all Windows Platforms but nothing about not of the other platforms) or whethere I just need a codex for mkv files. Freel free to to shoot me a few ideas on how to fix this please?

Are there Codex I needed to get mkvs playing if where can I get them?

---

### Post by warp99 on 2008-03-16
Have you installed the win 32 codecs package from medibuntu.org repositories:

[http://www.medibuntu.org/index.php](http://www.medibuntu.org/index.php)

I believe that the codec for mkv is included with this package. If not you can download a windows mkv codec and put the file in your /usr/lib/codecs directory, then use mplayer instead of vlc. :)

---

### Post by spiritsongtress on 2008-03-16
Thank you!

Well this would be really helpful if I new how to install it... but I know nothing about linux other then that it is great...

Someone help please.

---

### Post by shirilover on 2008-03-16
Since VLC uses its own internal codecs, installing w32codecs will not aid you.
VLC should not have any problems playing mkv files. Displaying styled subtitles is another matter.
So, are you try to play the files using disc mode or file mode?

---

### Post by spiritsongtress on 2008-03-16
Disc mode... I also have ogm files... so now I am wondering if it because I burnedI burned it with Nero as a dataCD which was said to read 'on all Windows Platforms' and since Linux isn't windows it might not read it..

---

### Post by warp99 on 2008-03-16
Adding extra repository information is here:

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)

You would have to use mplayer or gmplayer instead of vlc to use the w32codecs, which I mentioned in my previous post but not very clearly.  

Also I would bookmark the following pages:

[https://help.ubuntu.com/](https://help.ubuntu.com/)
[http://ubuntuguide.org](http://ubuntuguide.org)

Most if not all of your basic questions are going to be answered in these two places. :)

---

### Post by warp99 on 2008-03-16
Found some information that may be helpful:

> Matroska is a container format for storing or streaming video and audio files. The Matroska format has many features, such as a DVD-style menu system.

File-extensions: .mkv .mka .mks
Module options

    * --mkv-use-ordered-chapters (boolean)

          Ordered chapters: Play ordered chapters as specified in the segment. Default true. 

    * --mkv-use-chapter-codec (boolean)

          Use chapter codecs found in the segment. Default true. 

    * --mkv-preload-local-dir (boolean)

          Preload matroska files from the same family in the same directory (not good for broken files). Default true. 

    * --mkv-seek-percent (boolean)

          Seek based on percent not time. Default false. 

    * --mkv-use-dummy (boolean)

          Read and discard unknown EBML elements (not good for broken files). Default false. 

Compatability

VideoLAN can only read matroska files. Also, some of the video codecs that can be used inside this type of file are not supported by VLC. Most notably, this includes the RealVideo 9 and 10 formats.

[http://wiki.videolan.org/Mkv](http://wiki.videolan.org/Mkv)

The compatibility issue could be your problem. I would look around the VideoLan wiki to see how to check which codecs your mkv files are using. ;)

---

### Post by cor2y on 2008-03-16
I think its a compatibility issue mkv is only a container after all what codec was used in the encoding is the question, nero has it own video codec i believe but i don't know if its linux friendly.

---

### Post by shirilover on 2008-03-16
> **spiritsongtress said:**
> Disc mode... I also have ogm files... so now I am wondering if it because I burnedI burned it with Nero as a dataCD which was said to read 'on all Windows Platforms' and since Linux isn't windows it might not read it..

You should be using File mode, from the File tab instead of disc mode(used for DVD/VCD/SVCD).

---

### Post by spiritsongtress on 2008-03-18
Tried file mode, it doesn't work. And it could be that Nero-codec thing you all talked it... I wish there was some way to skirt it, like skirting my Broadcom wireless card.

---

### Post by shirilover on 2008-03-19
If you burned the files with nero as a data DVD, there should not be any problems. I have done this with several videos and have not encountered any playback problems; however, I use MPlayer for all my video playback.

Have you tried copying the files to a temp folder and playing them from there?

---

### Post by spiritsongtress on 2008-04-11
Any one know how I get MPlayer (ect) and I'll try and reburn myDVDs and see if it works)

---

### Post by spiritsongtress on 2008-04-13
Someone mentioeds ISO 996 (?) what's that? How do I burn Nero Data DVDs with it?

---

