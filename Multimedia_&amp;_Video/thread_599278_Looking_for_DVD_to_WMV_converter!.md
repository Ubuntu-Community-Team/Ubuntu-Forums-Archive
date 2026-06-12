---
title: "Looking for DVD to WMV converter!"
date: 2007-11-01
forum: Multimedia &amp; Video
---

### Post by dawson9b7b on 2007-11-01
Hi friends,
Is there any free DVD to WMV converter?
If you know please let me know, I need it argent.
Any recommendation will be appreciated!

---

### Post by BennBuntu on 2007-11-01
Could try VLC, not much experience, but if you go file menu, wizard, transcode/save to file. Mine offers wmv. 

I'm sure there's a better way, But maybe a start.

Benn

---

### Post by erginemr on 2007-11-01
Are you writing from under Windows, or from under Linux? I am asking you this, because there may be several programs running under Windows that can rip DVD's into wmv (even MS's own program, Windows Movie Maker after installing Windows Media encoding codecs). But it is quite unlikely to find one that can encode to it, becasue wmv (Windows Media Audio) codec is deliberately an MS product.

In case you are using Linux right now, there is a program "Mencode", developed by the same people who created the famous MPlayer, but although it can encode from wmv video to other codecs, I am not sure if it can encode from other codecs into wmv.
For more info, see:
[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

There is also another video editing program, Avidemux that is praised by Linux users. You may also try your luck with it:
[http://fixounet.free.fr/avidemux/](http://fixounet.free.fr/avidemux/)

If you do not have to use wmv, I would suggest you to use another format, say xvid for the best compression / quality balance.

---

### Post by daengbo on 2007-11-01
Install lame, mencoder and ffmpeg by [clicking here]("apt:ffmpeg"), [here]("apt:lame") and [here]("apt:mencoder") (you'll need to have universe and multiverse enabled). Use the following line to encode your videos:
mencoder dvd://1 -oac lavc -ovc lavc -lavcopts acodep=mp3:vcodec=wmv2 -o DVDTitle.wmv

Best of luck!!!

---

### Post by daengbo on 2007-11-01
Should be:
mencoder dvd://1 -oac lavc -ovc lavc -lavcopts acodec=mp3:vcodec=wmv2 -o DVDTitle.wmv

---

### Post by Joseph for u on 2007-11-02
Yes! You can try on [http://www.dvd-to-wmv.com/](http://www.dvd-to-wmv.com/) you can convert DVD to WMV video format with high speed and easily. It’s really a best site on the net for DVD to WMV converter. Hope this will help you. 
Good luck!

---

