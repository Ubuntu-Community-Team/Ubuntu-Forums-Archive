---
title: "Question about Adobe Flash Player and libdvdcss2"
date: 2009-02-22
forum: Multimedia Software
---

### Post by wolfman1221 on 2009-02-22
Okay, I am trying to install the two items I mentioned above. 


When I try to install adobe, I recieve a message that says wrong architecture 'i386'. 


I believe I have installed libdvdcss2, however when I play a dvd I recieve the following message. 

 "The source seems encrypted, and can't be read. Are you trying to play an encrypted DVD without libdvdcss".


If anyone could help me with these two things, it would be much appreciated.

---

### Post by alexandari on 2009-02-22
How are you trying to install adobe? from the packages or you download a .deb from the adobe webpage?
And with what are you opening your DVD files?

---

### Post by wolfman1221 on 2009-02-22
I am  trying to download a .deb from the adobe webpage.

I am using movie player xine. Do you know a better one?

---

### Post by wolfman1221 on 2009-02-22
I am not really sure why it is giving me these messages, but if you or anyone else could help me that would be great.

---

### Post by hansdown on 2009-02-22
Hi wolfman1221.

You also need libdvdread3. 

The easiet way to set everything up after an install, is, go to

[http://www.stchman.com/](http://www.stchman.com/)

You can click on any topic and copy and paste the commands into a terminal.

Click applications> accessories> terminal.

---

### Post by graysky on 2009-02-22
For the libdvdcss2:
```
$ sudo aptitude install libdvdread3
$ sudo /usr/share/doc/libdvdread3/install-css.sh
```

For adobe flash player for 64-bit:
Download the file from [adobe labs](http://labs.adobe.com/downloads/flashplayer10.html) and untar it (filename is libflashplayer.so).  Then:
```
$ sudo cp libflashplayer.so /usr/lib/mozilla/plugins/
```

---

