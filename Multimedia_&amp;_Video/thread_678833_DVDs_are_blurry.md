---
title: "DVDs are blurry"
date: 2008-01-26
forum: Multimedia &amp; Video
---

### Post by Mramius on 2008-01-26
When I watch DVDs using totem or vlc or whatever, the movies are very blurry during scenes with lots of movement.  This happens whether they are DVDs playing off of the DVD-ROM or if I make them into .iso files and run them from my harddrive.

I have 4GB of ram so I don't think it's a memory issue.

I don't know much about video settings and whatnot so I'm not sure where to look on how to tweak for optimum quality.

Any pointers?

---

### Post by ron999 on 2008-01-26
Hi
When you say 'blurry', do you mean that there are ragged edges like in the attachment below?

---

### Post by Mramius on 2008-01-26
Yes exactly that!

---

### Post by ron999 on 2008-01-26
> **Mramius said:**
> Yes exactly that!
OK
That's because the DVDs use 'interlaced' video files.
Interlaced scanning is fine for TV sets, but computer monitors don't like it. They prefer 'progressive' instead.

When I make DVDs now, I use a 'deinterlace' option with ffmpeg program to make the file progressive before I convert it.

Maybe someone will suggest other ways to overcome it.

There's lots to read about interlacing on Wikipedia, here :-[http://en.wikipedia.org/wiki/Interlace]("http://en.wikipedia.org/wiki/Interlace")
8)8)

---

### Post by Mramius on 2008-01-26
Will using ffmpeg decrease the quality?  It seems to convert them to mpg or divx or something.

---

### Post by ron999 on 2008-01-26
Well, there may be a decrease, but it's not noticeable (to me).
The files used in a DVD need to be mpg.

So the command that I use to put my file into the correct format is:-

**ffmpeg -deinterlace -i <name of file here> -target pal-dvd movie.mpg**

Which gives me a progressive file named 'movie.mpg'. Then I author it into a DVD using 'tovid'.
For USA you need to use '-target ntsc-dvd' instead of '-target pal-dvd' in the command. Or maybe just '-target dvd'.

(I'm assuming that you are in Boston, Massachusetts - not Boston, Lincolnshire)

---

### Post by Mramius on 2008-01-26
Do I lose menus and such with this method?  Or does using tovid recreate the menus?

---

### Post by shad0w_walker on 2008-01-26
I am assuming that having 4Gb of RAM your system is fairly beefy all around. Don't bother ripping the discs and converting them to a deinterlaced format. That is not needed. Most programs have deinterlacing options in them somewhere. I use VLC and it has a option in Video > Deinterlace. Try out some of these options in whatever program you use to play videos. If your system is anywhere near reasonably balanced you can do it on the fly and ignore the whole hassle of ripping to a file.

---

### Post by ron999 on 2008-01-26
Thanks for that, I didn't know about those 'deinterlace' options with VLC.

---

