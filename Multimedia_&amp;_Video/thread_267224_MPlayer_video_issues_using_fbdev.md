---
title: "MPlayer video issues using fbdev"
date: 2006-09-28
forum: Multimedia &amp; Video
---

### Post by deesine on 2006-09-28
Hello, I hope this is the right section for posting this, being my first post it's a little confusing.

I recently installed ubuntu on my laptop, which is a Satellite Pro 4200, and everything works fine, except for playing video files. And I would like to clarify that I downloaded and installed ubuntu about a week or two ago, so I believe I'm running 5.10(?) and not 6.06. I don't think updating would solve my problem though.

I downloaded mplayer and installed it from source, from the start I couldn't get much video output at all, so I've gone over the man a few times and have reached some results, using fbdev and appending vga=792 video=vesa:mtrr to the kernel. My gfx card is a S3 Inc. 86C270-294 Savage/IX-MV.

I have a couple of screenshots illustrating the problem, note that the video is played directly on the desktop.
[Screenshot 1]("http://deesine.grafikfel.org/linux/MPLAYER3.jpg") - using no additional parameters.
[Screenshot 2]("http://deesine.grafikfel.org/linux/MPLAYER2.jpg") - with -bpp 16 parameter.

And here's some text files with output from mplayer.
[Output from running 'mplayer -bpp 16 movie.avi']("http://deesine.grafikfel.org/linux/MPLAYER.BPP.txt")
[Output from running 'mplayer movie.avi']("http://deesine.grafikfel.org/linux/MPLAYER.DEE.txt")
[Output from running 'mplayer -msglevel all=9 movie.avi']("http://deesine.grafikfel.org/linux/MPLAYER.MSG.txt")

Please note that I don't have internet connected to the laptop and moving large amounts of files are kind of a hassle.

Any help, thoughts and suggestions are welcome.

---

### Post by croak77 on 2006-09-28
Did any -vo options make a difference? Do you want mplayer to run without X? Or in X?

---

### Post by deesine on 2006-09-29
I've tried all the -vo options, none of them worked, seems fbdev is the only one that works when appending the above stated line to the kernel.

When I had gentoo installed I ran mplayer (not gmplayer) from the term and a small window with just the video in it would show up, that's what I'd ideally want. But running directly on the desktop is fine, if I could smack those two image-streams together somehow.

---

### Post by croak77 on 2006-09-29
What --configure options did you use to compile mplayer? Did you use --enable-gui --enable-x11 --enable-gl --enable-sdl as well as enabling various codecs? What does 'mplayer -vo help' show?

---

