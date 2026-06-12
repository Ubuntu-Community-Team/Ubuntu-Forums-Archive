---
title: "MP3 ripping/Grip"
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by esl1885 on 2007-08-13
Hi,

Could someone tell me the correct info to enter in the encoding section to succesfully rip MP3's with Grip.
I think I have the correct encoder installed (mpg321), I have no problem ripping the wav files, but cannot encode them to MP3.
What I have is:
Encoder executable.........../usr/bin/mpg321
Encoder commandline.......~/mp3 %n %
Encode file extension.........mp3
Encode file format..............~/mp3/%A/%d/%n.mp3

Obviously, some of this wrong, but I have no idea what the correct info to enter is.

Thanks for any help in advance.

Sam

---

### Post by praet on 2007-08-13
I suggest you take another look at the documentation pages:
[http://nostatic.org/grip/doc/ar01s04.html#mp3config](http://nostatic.org/grip/doc/ar01s04.html#mp3config)

I don't think mpg321 can be used as an mp3 encoder.  
For mp3 I highly recommend LAME 

Encoder executable: /usr/bin/lame
Encoder command line: -h -b %b %w %m
Encode file extension: mp3
Encode file format: ~/mp3/%A/%d/%n.%x 

.praet

---

### Post by esl1885 on 2007-08-13
Thanks,

I have installed Lame and it is working great.

Sam

---

