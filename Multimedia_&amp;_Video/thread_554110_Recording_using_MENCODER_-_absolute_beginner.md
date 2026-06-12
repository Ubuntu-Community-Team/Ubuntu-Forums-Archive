---
title: "Recording using MENCODER - absolute beginner"
date: 2007-09-18
forum: Multimedia &amp; Video
---

### Post by gheywood on 2007-09-18
Hello, 

I have a PVR-150 card with two inputs, one from the arial (rf) and one from the Sky box (s-video and audio cables).

I know that if I do:

cat /dev/video0 > file.mpeg

Then it records fine from the Sky box, and I can play back the file.

I would like to do a few things:

1) Create a bash file to use mencoder to record for, say 2 hours from the Sky box.
1) Create a bash file to use mencoder to record for, say 2 hours from the arial (RF input).

I know that I have mencoder installed, but don't understand what options I need to configure, or how I can tell it to record only for a few hours...

I think I know how to create a SH file on the desktop, but am a bit stuck apart from that. I am not even sure how to create the MENCODER.CONF file in the /etc/mplayer folder (permissions I presume), or what I should have in it.

Also, is this the best way to record if I want to record onto DVD at a later date?

Thanks heaps for any help.

---

### Post by gheywood on 2007-09-19
Anyone? 

Or if memcoder is not the way to go, can anyone suggest a better way?

---

### Post by eye208 on 2007-09-19
MEncoder's -endpos option is what you are looking for. See the manpage for details.

---

### Post by gheywood on 2007-09-20
Thanks, but I tried that without any success. 

I created a record.sh file and it contains

memcoder /dev/video0 -of mpeg -o encoded.mpg -endpos 20


It doesn't look like it does anything when I run it (I just get a $ prompt). 

I am finding it really hard to find information that tells me what I need to do. The mencoder help here: 
[http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-selecting-input.html](http://www.mplayerhq.hu/DOCS/HTML/en/menc-feat-selecting-input.html)

Unfortunately they talk about a -tv//channelnumber but my PC is completely unaware of the different channels as far as I know. 

If a cat command works with /dev/video0, I thought I would be able to use that with mencoder. Is that not correct?

---

