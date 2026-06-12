---
title: "cdrdao freezes when copying audio cd's"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by bebop_tango on 2007-10-31
Hello,

I've recently changed my cd-r/rw drive to a HL-DT-ST DVD-RAM GSA-H55N dvd-r/rw one. There's one problem with it - I cannot copy audio cds with a simple "cdrdao copy" on the command line. 

The bug is rather strange - cdrdao STARTS to READ the data on the cd but soon it freezes completely. Needless to say, brasero and nautilus-cd-burner, which use cdrdao as a backend for this job, also freeze. And when I try to copy a data cd it works just fine...

The hardware seems ok - I sucessfully copied one audio cd with K3b (since it automatically chose cdrecord to do the job).

Any ideas...?

---

### Post by andrew.46 on 2008-04-17
Hi,

 Your post is a little old now but I have a similar drive:  HL-DT-ST, DVDRAM GSA-H42N. Can I ask:

[LIST=1]
[*]What is the result of $ cdrdao scanbus ?
[*]What command line did you use?
[*]What is the contents of /etc/cdrdao.conf?
[/LIST]

     Andrew

---

### Post by vanadium on 2008-04-17
You might be lucky that it does not work, because what you attempt is a very bad way to copy audio CDs. Data CDs have error checking mechanisms. When data is read, it is compared with the checksum which is also stored on the disk. If the checksum fails, the data is read again, and if the data cannot be read correctly anymore, you get an error. This ensures that the data is  read correctly.

An audio CD does not have such a correction. There, the data are read from the CD without any means of checking what is read is correct.

For this reason, you should use the dedicated tools to copu an audio CD. Originally, there was cdda2wav to do the job, but this is superseded by cdparanoia which includes more robust data verification features.

This is how you could create a wav/cue sheet from the command line:

cdparanoia 1- image.wav
cdrdao read-toc --device 1,0,0 --with-cddb image.toc
cueconvert image.toc > image.cue

---

### Post by andrew.46 on 2008-04-17
Hi,

 I have to codially disagree with me vanadium. Try the following method which works for me (it is my guide):

[http://www.andrews-corner.org/burning.html#audio](http://www.andrews-corner.org/burning.html#audio)

               Andrew

---

### Post by vanadium on 2008-04-17
Nice indeed. I was not aware that cdrdao has build-in cdparanoia support, and the nice thing is that you have your toc in the same run. Gone updating my howto ... ;)

---

