---
title: "Tuning Hauppauge PVR-150"
date: 2008-12-26
forum: Multimedia Software
---

### Post by reams on 2008-12-26
I have just installed a new Hauppauge PVR-150 TV tuner card on x86_64 Hardy Heron. I believe the hardware is functioning roughly correctly because, if I do

cat /dev/video0 > ~/test.mpg

then it produces something which looks very much like TV static. My suspicion is that the card is not tuned correctly. I have plugged in an aerial and tried

ivtv-tune -f 767

and many other frequencies which ought to correspond to TV stations in my region, and have also tried plugging in a games console with a known frequency (594MHz), but the result is always static.

Please could someone give me a few pointers on getting this thing to work?

---

### Post by wolfen69 on 2008-12-26
I have a Hauppauge pvr150 card running on my box, and I get  tv by: 

```
sudo apt-get install ivtv-utils 
```

open VLC player

File -> Open Capture Device -> PVR -> OK

then you can do (in terminal)

```
ivtv-tune -c25
``` (25 is channel number)

which changes the channel.

```
ivtv-tune -h
```

to see the options which control the card. 


for a cool desktop tv remote,(so you dont have to use terminal to change channels) go to: [http://tvremote.sourceforge.net/](http://tvremote.sourceforge.net/)

remember to have java installed first. then you can right click: open with java.

to record tv:

```
cat /dev/video0 > /tmp/name_of_file.mpg
```

it will record whatever channel you are on. then ctrl-c to stop.

but i have cable tv, not over there air. but it should work.

---

### Post by saedelaere on 2008-12-30
> **reams said:**
> I have just installed a new Hauppauge PVR-150 TV tuner card on x86_64 Hardy Heron. I believe the hardware is functioning roughly correctly because, if I do

cat /dev/video0 > ~/test.mpg

then it produces something which looks very much like TV static. My suspicion is that the card is not tuned correctly. I have plugged in an aerial and tried

ivtv-tune -f 767

and many other frequencies which ought to correspond to TV stations in my region, and have also tried plugging in a games console with a known frequency (594MHz), but the result is always static.

Please could someone give me a few pointers on getting this thing to work?

You could also use [this one]("http://ubuntuforums.org/showthread.php?t=763698").

---

