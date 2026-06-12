---
title: "Looking for a Linux program to convert sfw files to jpg."
date: 2020-04-27
forum: Multimedia Software
---

### Post by irv on 2020-04-27
I have a bunch of Seattle Film Works files (sfw) on floppies. I know how to get them off the floppies, but I am looking for a Linux program to convert them to a jpg file format.
I found an extension for chrome browser but it is just a link to a website to convert them but it requires I subscribe to their site for a fee. Any ideas?

---

### Post by slickymaster on 2020-04-27
*Thread moved to **Multimedia Software**.*

---

### Post by irv on 2020-04-27
Thank you wasn't sure where to post this. I found a program called "Image Magick" but is going to take a long time to convert them one at a time. And it has its own file manager and hard to use. Hoping there is a better way.

---

### Post by speartip on 2020-04-27
I found this which might be useful. It's batch converting from png to jpg using Imagemagick, but the principle should be the same.
Sorry  I never posted the Link':confused:
[https://superuser.com/questions/71028/batch-converting-png-to-jpg-in-linux](https://superuser.com/questions/71028/batch-converting-png-to-jpg-in-linux)

---

### Post by Holger_Gehrke on 2020-04-27
ImageMagick is just what i was going to suggest. Its GUI is admittedly useless, but there's always the command line. Something like 'for i in *sfw; do convert "$i" "${i%.sfw}.jpg";done' would convert all SFW-files in the current directory to JPEG.

Holger

---

### Post by irv on 2020-04-27
I install imagemagick but it will not work for the command line only the GUI

---

### Post by speartip on 2020-04-27
The convert command is part of the imagemagick program to be used in a terminal.
 [https://www.lifewire.com/convert-linux-command-unix-command-4097060](https://www.lifewire.com/convert-linux-command-unix-command-4097060)

---

### Post by irv on 2020-04-27
I got it done.
I put all the .sfw files in one directory cd to that place and did a command:
> convert input *.SFW output *.jpg
and it converted all the files to jpg files. I will mark it solved.

---

### Post by irv on 2020-04-27
I forgot to say thank you. After all this looking it tuned out to be a simple thing to do.

---

