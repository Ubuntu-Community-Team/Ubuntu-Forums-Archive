---
title: "Converting wmv to flv"
date: 2008-06-08
forum: Multimedia Software
---

### Post by getmeoutofhere on 2008-06-08
This is driving me crazy.  Nothing seems to work - I'm using Linux Mint, based on Gutsy.

The much regarded Fuoco tools won't do anything.  Whatever I try to convert, the terminal pops up, and I'm told 'Xterm: Can't execvp TO: No such file or directory'.  

ffmpeg is just as bad.  I paste in what I read on on the various posts I browse to, and invariably I get the message 'Unsupported codec (id=0) for input stream #0.0'

Is there any simple method of making the conversation?  Or is it best to just switch to Windows, and pay for a conversion program?

Thanks.

---

### Post by Thanoulis on 2008-06-08
Did you try to use mencoder?
I use it to convert flv's and wmv's to Divx and is working fine.
I'm using Hardy 64bit.

---

### Post by foo on 2008-06-08
Avidemux is capable to make this kind of conversion.
I made some test and seems to work very well.

Open the wmv file, then choose:

Video: FLV1 (lavc)
Audio: MP3
Format: FLV
(a different way is to choose Auto -> FLV)

and then "Save" the file.

---

### Post by Creative2 on 2008-06-08
fuoco tools----> you have to select the command line and not the tag

see this 

[http://fuocotools.byethost13.com/index.php?topic=45.0](http://fuocotools.byethost13.com/index.php?topic=45.0)

or this

[http://fuocotools.byethost13.com/index.php?topic=63.0](http://fuocotools.byethost13.com/index.php?topic=63.0)


for ffmpeg you have to download and install this (ffmepg's medibuntu debian package---i have saved on mediafire but you can find out on medibuntu repository... [http://www.mediafire.com/download.php?lthasyvh1ix](http://www.mediafire.com/download.php?lthasyvh1ix))

if you prefer mencoder you can find out the commnand line here ------->[http://fuocotools.byethost13.com/index.php?topic=114.0](http://fuocotools.byethost13.com/index.php?topic=114.0)

anyway why you don't write about your problems in Mint's forums?

---

### Post by netyire on 2008-06-09
+1 for mencoder but if you want a really easy way to do it, you can make use of the free online zamzar website at [http://www.zamzar.com](http://www.zamzar.com) to convert all sorts of stuff (including flvs I think) to other formats.

---

