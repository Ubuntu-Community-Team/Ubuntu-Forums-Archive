---
title: "Editing .vob files"
date: 2009-07-27
forum: Multimedia Software
---

### Post by zorblek on 2009-07-27
I just received a camcorder as a gift. Unfortunately, it only saves files in .vob format. What Linux programs are available to edit .vob files? Or, barring that, what would be the best way to convert them to a more common format, such as .avi or .mpg?

---

### Post by alphacrucis2 on 2009-07-27
> **zorblek said:**
> I just received a camcorder as a gift. Unfortunately, it only saves files in .vob format. What Linux programs are available to edit .vob files? Or, barring that, what would be the best way to convert them to a more common format, such as .avi or .mpg?

For simple cutting and joining you could try avidemux. It does conversion too.

---

### Post by amoeba801 on 2009-07-27
zorbek,

Welcome to the wonderful world of linux video production. You are about to embark on a journey with many trials and tribulations. Fortunately, vob is a well recognised video container that most applications can work with.

For simple editing (mainly cutting), I use and recommend **Avidemux**. It will read in vob's and save the resulting video in a format of your choosing - mpeg2, mpeg4, avi's, (assuming you have installed the relevant codecs).

For more advanced editing (adding titles, music, etc) I use **kdenliv**e, which can also handle vob as an input. I would expect the other video editing suites such as **cinelerra**, **kino**, and **pivitvi** to be similar.  Again, these can save our output in a variety of formats. A word of warning: these more advanced video editing suites (known as non-linear editors) are all somewhat problematic and take a while to learn. 

For converting vob's to other formats, you can use** handbrake**, or **Avidemux**, or from the command line with tools such as** mencoder** or **ffmpeg**.

If you want to end up with a DVD that can be played on a standalone DVD recorder then kdenlive can do this although I've not use it, so I do not know well it works. Otherwise I use **DeVeDe**, and **DVDAuthor** from the command line.

---

