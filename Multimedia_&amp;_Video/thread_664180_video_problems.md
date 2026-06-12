---
title: "video problems"
date: 2008-01-10
forum: Multimedia &amp; Video
---

### Post by wilkinnh on 2008-01-10
I was previously using fedora with mythtv, but i decided to give mythbuntu a try. everything looks really simplified and great, however my video is working from my capture card. what's strange is that i can run a test by doing:

cat /dev/video0 > /tmp/test.mpg
(wait a couple seconds then ctrl-c)
mplayer /tmp/test.mpg

and it works just fine. there's video that's actually captured to the mpg format. so that has to mean that the ivtv side of things is working fine. however, in mythbuntu, the card shows up just fine and the input is set correctly to /dev/video0, but no video shows up. i already looked into the frequency that's being used and us-cable should be right.

any ideas as to what the problem could be? it doesn't make sense to me that the /dev/video0 is working outside of mythbuntu, but inside the program there's no video. not even the live tv works...

---

### Post by wolfen69 on 2008-01-10
i have the ***exact*** same problem. i gave up a long time ago. however, i will keep an eye on this thread to see where it goes. if all you want is TV and dont care about Myth, read on.

sudo apt-get install ivtv-utils (drivers)

open VLC 

File -> open Capture Device -> PVR -> OK

then you can do

ivtv-tune -h

to see the options which control the card. The interesting ones are

ivtv-tune -d(input number)

which changes the card's input from composite to s-video, and

ivtv-tune -c25(25 is channel number)

which changes the channel.

for a cool desktop tv remote, go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click(tv remote) open with java.

---

### Post by wilkinnh on 2008-01-10
thanks for the reply, i installed the ivtv utils and everything seems to be working just fine through VLC. i am looking to hook my pc up to my tv like i previously did and record tv shows and such. i don't really watch live tv through it much, i usually just use my tv for that. but i do want to record shows and such.

is there an error log i can check to see what could be going wrong? when i try to go to the live tv option, i get a black screen for about 20 seconds and then it goes back to the menu. it'd seem like there should be some kind of error output being sent somewhere, i just have no idea where...

---

### Post by wilkinnh on 2008-01-10
actually, i think i fixed the problem! i found there is an error log which you can look at by going to the terminal and running:

tail -f /var/log/mythtv/mythbackend.log

i noticed that it said:

2008-01-10 22:49:17.819 TVRec(1): HW Tuner: 1->1
2008-01-10 22:49:18.040 Unknown video codec
2008-01-10 22:49:18.044 Please go into the TV Settings, Recording Profiles and
2008-01-10 22:49:18.045 setup the four 'Software Encoders' profiles.
2008-01-10 22:49:18.045 Assuming RTjpeg for now.
2008-01-10 22:49:18.046 NVR: Error, unknown audio codec
2008-01-10 22:49:18.070 NVR: Won't work with the streaming interface, falling back
VIDIOCGMBUF:: Invalid argument
2008-01-10 22:49:58.079 TVRec(1): Changing from WatchingLiveTV to None
2008-01-10 22:49:58.187 Finished recording Friends "The One With the Race Car Bed": channel 1002

the "Unknown video codec" is what caught my attention, and i did a quick search and figured out that mythtv had automatically associated my capture card with the V4L (video4linux i believe...), but it's actually an MPEG2 card with built-in hardware MPEG2 compression. so, i redid the mythtvsetup (the backend) and made sure when i selected my capture card that i selected it as MPEG2. once i did that and saved it, everything started working!

now i just have to get the right frequency table...

---

