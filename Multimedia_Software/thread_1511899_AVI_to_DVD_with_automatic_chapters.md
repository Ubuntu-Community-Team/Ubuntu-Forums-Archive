---
title: "AVI to DVD with automatic chapters?"
date: 2010-06-17
forum: Multimedia Software
---

### Post by maphew on 2010-06-17
Hello,

I'm in the process of converting old VHS tapes to DVD discs and am looking for a simple program for the last step: converting .avi to DVD. I've found a number of good programs for doing this, but none that will automatically create chapters every X minutes (perhaps better said as: I can't locate the option for this if it does exist).

thanks

---

### Post by vfiz on 2010-06-17
If you're using DeVeDe, then there's a chapters option when you add a file.  When the file properties window comes up, click on "Advanced Options" toward the bottom.  You can then specify the minute-incremented chapters for that file.

If you're using Todisc, then you can set your chapters in two different ways.  You can specify a number and have Todisc chop up your video into that number of chapters, or you can specify the exact times (HH:MM:SS) that you want Todisc to put chapters in.  I don't really use Todisc (or Tovid), and the GUI's always given me problems, but on the command line, it looks something like this:

```
todisc -files input.avi -chapters 5 -titles "My Movie" -submenu-titles "Submenu" -out path/to/folder
```

That would split up input.avi into 5 equal chapters.

Check out [http://tovid.wikia.com/wiki/DVD_Chapters]("http://tovid.wikia.com/wiki/DVD_Chapters")

---

### Post by nothingspecial on 2010-06-17
Check out dvdauthor, you create a small config that it reads in which you can specify chapter length.

[[COLOR="Magenta"]This[/COLOR]]("http://www.linux.com/archive/feed/53702") explains it far better than I could.

---

### Post by maphew on 2010-06-19
Thanks vfiz, that solves it. I was/am using Devede but missed the fact there were advanced options on each file as well as on the project.

---

