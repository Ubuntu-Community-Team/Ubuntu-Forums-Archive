---
title: "Mass video encoder with a GUI - is there one?"
date: 2010-06-28
forum: Multimedia Software
---

### Post by infinitejones on 2010-06-28
I've got a bunch of wmv files that I'd like to re-encode to avi - about 50 of them. Is there a straightforward GUI application that does the same thing as Sound Converter does with audio files? As in, add a folder full of files, select the output format and output filename/folder, click "convert", and come back a few hours later.

Yes I know I can convert video files with mencoder and ffmpeg, but doing it file by file at the command line means I can't leave it running overnight or something.

I found something called Arista but the only output options are designed for specific hardware, ie. iPods and PSPs. I just want to convert the wmv's to avi's, not mess around with resolution etc. Also, with Arista you still need to add the files one at a time.

Any ideas?

---

### Post by ron999 on 2010-06-28
Hi
WinFF will do the job.
It's a GUI for ffmpeg.
So select the required 'pre-set', such as AVI or WMV.
Then load the folder and 'Convert'.
There is an 'Options' button that lets you tweak the pre-sets if you wish.
WinFF might be in the repository, if not, go to the website and add the ppa.
This is the website:-[http://winff.org/html_new/]("http://winff.org/html_new/")
:guitar:

---

### Post by infinitejones on 2010-06-29
Looks like it's working well!

Thanks v much.

---

### Post by manthony121 on 2010-09-22
If you ever have need to do the same thing to a bunch of files, it is good to learn this simple idiom:

$ for i in *; do <command $i>; done

where <command $i> is whatever commmand(s) need executing.

In this case:

$ for i in *wmv; do ffmpeg -i $i -f avi -vcodec mpeg4 -o $i.avi; done

---

### Post by ron999 on 2010-09-23
> **manthony121 said:**
> If you ever have need to do the same thing to a bunch of files, it is good to learn this simple idiom:

$ for i in *; do <command $i>; done

where <command $i> is whatever commmand(s) need executing.

In this case:

$ for i in *wmv; do ffmpeg -i $i -f avi -vcodec mpeg4 **[COLOR="Red"]-o[/COLOR]** $i.avi; done

No need for **[COLOR="Red"]-o[/COLOR]**

---

