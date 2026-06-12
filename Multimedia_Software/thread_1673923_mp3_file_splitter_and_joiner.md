---
title: "mp3 file splitter and joiner"
date: 2011-01-23
forum: Multimedia Software
---

### Post by mahmoodkamal on 2011-01-23
Hi guys,

What is the best software for splitting and joining mp3 files?:popcorn:

---

### Post by vanadium on 2011-01-23
Lossless mp3 splitting can be achieved using mp3splt.

To join mp3 files without corrupting them and without quality loss, you can use mp3wrap. These can be splitted again to the original files by mp3splt.

---

### Post by MartyBuntu on 2011-01-23
I've used mp3splt-gtk...It gets the job done with aid of a GUI.

Also, Audacity works perfectly for me.

---

### Post by vanadium on 2011-01-23
Working with Audacity involves decoding and compressing again, i.e., quality loss. Not the proper approach if you just want to combine or split mp3 files. Very useful, though, for more complex audio editing needs.

---

### Post by JRV on 2011-01-23
I use lxsplit, a command line file splitter/joiner compatible with Windows HJSplit.

To install "sudo apt-get install lxsplit".

> 
LXSplit v0.2.4 by Richard Stellingwerff, O. Sezer.
Home page: [http://lxsplit.sourceforge.net/](http://lxsplit.sourceforge.net/)

Usage: lxsplit [OPTION] [FILE] [SPLITSIZE]

Available options:
 -j : join the files beginning with the given name
 -s : split the given file.  requires a valid size
Splitsize examples: 15M, 100m, 5000k, 30000000b

Examples:
	lxsplit -s hugefile.bin 15M
	lxsplit -j hugefile.bin.001



---

### Post by vanadium on 2011-01-23
> **JRV said:**
> I use lxsplit, a command line file splitter/joiner compatible with Windows HJSplit.
This will probably not result in smaller mp3 files that you still can play.

For your information: the utility "split" does just that and is already part of your default Ubuntu install.

---

### Post by mahmoodkamal on 2011-01-27
Thanks you guys. I used HJsplit on windoze before. it just breaks the files at given point and all splitted files are still playable after changing their extensions to 'mp3'

---

### Post by vanadium on 2011-01-27
...yet you end up with corrupt mp3 files.

---

### Post by linuxcss on 2012-01-12
i have a file called results.mp3

results.mp3 is 7 seconds long

mp3wrap results-3x.mp3 results.mp3 results.mp3 results.mp3

while it plays the entire 21 seconds of results-3x.mp3 parole player lists length is only 1/3 or 7 seconds of the actual size, how can one get the header information correct in the created file so player reflects the correct size?

---

