---
title: "Backing up Sony Handycam DVDs"
date: 2010-12-07
forum: Multimedia Software
---

### Post by gecka on 2010-12-07
Hello,

My girlfriend offered me a Sony Handycam DVD. I know it is not the best choice, a HDD cam would have been a much better choice but ...

The Sony's Windows software extracts each DVD's chapter into a mpeg2 file having the recording date has the filename. I want to reproduce that behavior with my Ubuntu.

When I plug the camera to my computer using the USB cable, it is seen as a DVD player. So I can access the DVD content. ([sample here]("http://dl.dropbox.com/u/4812171/Content.tar.bz2"))

I have managed to make a bash script that extracts each chapter as a file. That script is attached and needs mplayer & dvdxchap programs.

Now I need to have those extracted chapters to have the recording date/time as their filename. How can I achieve that?

One idea is to use the subtitles: there is a subtitle in each extracted chapter that has the date/time for each frame. It seems it is a text subtitle as it appears differently in each player. So how could I extract each chapter's first frame's subtitle?

Any other idea is welcomed.

---

