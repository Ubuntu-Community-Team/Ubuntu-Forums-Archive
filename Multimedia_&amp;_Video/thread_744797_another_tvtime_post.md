---
title: "another tvtime post"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by Daverobb on 2008-04-03
another problem getting tvtime up although somehow in my last gutsy machine it started working fine one day - once i realized that it would pick up the webcam as /dv/video0 instead of the tv tuner ... anyhow ... this time it doesn't work with what i thought was the same set up:

Hauppauge wintv bt878 tuner 

tv time flashes a black screen quickly and immediately disappears

help?

---

### Post by Uhospaghetto on 2008-04-04
welcome to the club, i still cant get my sound to work

---

### Post by wolfen69 on 2008-04-04
I have a Hauppauge pvr card running on my gutsy box, and I get  tv by: 

sudo apt-get install ivtv-utils 

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

ivtv-tune -c25 (25 is channel number)

which changes the channel.

ivtv-tune -h

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

---

### Post by saedelaere on 2008-04-23
Hi,

You could also try to use this [URL="http://ubuntuforums.org/showthread.php?t=763698"]one
[/URL]
regards
Saedelaere

---

