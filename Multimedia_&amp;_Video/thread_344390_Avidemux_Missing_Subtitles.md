---
title: "Avidemux Missing Subtitles"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by PurplePenguin on 2007-01-22
I have used avidemux to add subtitles to dozens of .avi movies and it worked perfectly each and every time (this was back when I was still using OpenSUSE).

I've long since moved to Ubuntu Edgy and thought I knew my way around avidemux, but now I can't seem to get the subtitler working.

I am doing everything exactly the same way as I used to, as far as I can tell.  I open the program, open a video file, select lame for audio, xvid for video, add a subtitler filter (I use .srt for the subtitles) **and make sure that I actually have a path to a .ttf font in the subtitler filter** (I know that this is what usually causes sub problems with avidemux), preview the filtered movie in the main menu and can see the subs in the preview. 

When I watch my final product, though, no subs.

I'm going crazy trying to figure out where I'm going wrong.  I've tried picking different fonts (ones that I know work), but nothing.  

If anybody has any hints or ideas, hit me! :)

EDIT: Yes, I've searched this forum and googled it.  As far as I know, it *should* work how I'm doing it!

---

### Post by PurplePenguin on 2007-01-22
Sorry for replying to my own post, but I did find another way to put my subs into my .avi's. 

Of course, knowing Linux, it's on the command line. :)  (This reminds me of when I wanted to batch resize a directory of photos and spent days trying to find a program to do it... sure enough, mogrify -resize ??x?? will do it in seconds on the command line!)

Anyway, I now know that mencoder is very, very easy to use.  At first, I was a bit frightened by the millions of different options and switches available.  But there's a good [Gentoo wiki]("http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide") that explains it all quite simply.

---

### Post by paparappa on 2008-01-10
I have  the exact same problem, but i tested Mencoder out with this code

[HTML]mencoder -oac copy -ovc raw -sub /path/to/subtitle.srt -sub-bg-alpha 150 -utf8 -o  nameofthenewfile.avi /path/to/originalfilm.avi[/HTML]

However an 350mb large file went to be 18.8 GB and the subtitles covered half of the vide. So isn't there any solution to the avidemux problem?

---

### Post by Mud.Knee.Havoc on 2008-01-12
You don't want "-ovc raw" in there.  Replace that with -ovc xvid and you'll be all set.

---

### Post by Bartje on 2008-07-20
What I have found, was that you have to use a codec to convert to. Using "copy" video, results in having no subtitles. Once using a codec to convert to (can be the same one as the original) you can render the subtitles into the video. It really seems to work for me.

---

