---
title: "Rip a Clip from DVD"
date: 2007-07-16
forum: Multimedia &amp; Video
---

### Post by Jamie Jackson on 2007-07-16
I'd like to rip a minute-long clip from a specified section of a DVD. What's the best app with which to browse and rip the clip I want?

Thanks,
Jamie

---

### Post by vanadium on 2007-07-16
Avidemux. If the DVD is encrypted, though, you will need to rip it to the hd first.

vobcopy -l

will copy the most important feature of the DVD to the harddisk. You can open the resulting VOB, select the clip and save it in any video format supported by Avidemux.

Take care for audio synchronisation: after loading your VOB, select "Audio - Main audio track". This will show you the delay of the audio track if there is any. You will need to specify this delay ("Shift" on the main screen) so that it is carried on to the destination file and audio remains synched.

---

### Post by warcriminal on 2007-07-16
Check out the article at;

[http://www.goitexpert.com/entry.cfm?entry=Rip-DVDs-and-CDs-In-Linux-Easily](http://www.goitexpert.com/entry.cfm?entry=Rip-DVDs-and-CDs-In-Linux-Easily)

This is probably the easiest way you are going to rip dvd's and cds.  You may need to install Mencoder though.

sudo apt-get install mencoder

---

### Post by Jamie Jackson on 2007-07-17
I couldn't readily figure out how to browse to my clip in acidrip.

However, I had my clip in about 10 minutes with avidemux.

Thanks for the replies!

Jamie

---

