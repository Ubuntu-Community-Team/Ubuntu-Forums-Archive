---
title: "TV Tuner Application"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by jettapup on 2007-05-29
Have had Feisty installed for a week or two, & its running just about everything I've asked it to do.
.mpg & dvix video play well in totum. This after several abortive attempts over the years to get a distribution to work correctly, as far back as 1997 with a slackware distrabuition.

I have an ATI capture card( Tv Wonder pro) and am looking for an application to install that will allow me to use the card in Feisty.

Any suggestions and where/how do i install it?

I have checked Add/ remove software drop down menu, gxine makes a comment about watching tv, its check box is checked & installed, but it the error message says gxine engine failed to start. and the "channels listed are not anything I recognize, except C-Span, So I assume these are streaming video sources, not the OTA / cable channels.

Again, 7.0.4 is almost a 100%  keeper; the closer will be Tv Tuner card, & video capture running!!
Thanks

Jettapup

PS/ I tried sudo apt-get install tvtim, and got following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package tvtim

---

### Post by jettapup on 2007-05-29
OK, So I add e to the end of 
 sudo apt-get install tvtim
 and it started to install..
ok I'm a cut & paste junky..
if it does not work out, I'll be back.. 
Thanks,
jettapup

---

### Post by jettapup on 2007-05-29
Tvtime detected the card, and went through channel set up, COOL..

Had no audio, ( ATI card has audio output jack run into line in on sound blaster, pluged speakers into tuner card out put & had sound.
Now I'm looking for a mixer gui to tweek the I/O of the sound card.

ALMOST THERE !!!!!!!

---

### Post by jettapup on 2007-05-30
Ok, TV is running with sound...

Sound problem was aux input was turned all the way down.

Eventually found the level controls, the ALSA in sound recorder, under file, open Volume Control.

Probably an easier route to get there, but I'm still an n00b at all of this.

SO, I am now considering Feisty for the the main computer, Since it has Thunderbird and Firefox. the Wife acceptance factor should be rather high :razz::razz:
ITS A KEEPER !!
jettapup

---

