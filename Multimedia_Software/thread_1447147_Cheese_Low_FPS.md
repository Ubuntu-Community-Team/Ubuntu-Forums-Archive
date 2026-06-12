---
title: "Cheese: Low FPS"
date: 2010-04-05
forum: Multimedia Software
---

### Post by Jazusa03 on 2010-04-05
hello, I'm on Ubuntu 10.04 Lucid. I have a Logitech C250 WebCam im recording on.
My Sound is being recorded through my microphone port on the back of my computer. I am recording my own music on my guitar via a Digitech RP250 Effects pedal. which is connected to the mic port. Every time I try to record anything even without my guitar. the video's always have PAINFULLY slow Frames per sec, most of the time it will pause on 1 frame for about 10 seconds then go to the next one. I'm recording in 640x480 resolution. Using Alsa as my main sound mixer. the sound is fine and plays like it should, but the video is terrable. 

I realy don't know what other information to put in here so if you need more you may need to tell me what commands to put in the terminal and such. I have tried to describe the situation as best I could. 

Please help me solve this problem. I've tried alot of diffrent things such as changing the recording resolution to a lower one but I cannot seem to get my webcam up to a descent fps rate.

:confused: :confused: :confused: :confused:  ](*,)  ](*,)  ](*,)  ](*,)

---

### Post by Jazusa03 on 2010-04-05
One Work around is to use GTKRecordMyDesktop and have Cheese Open. Maximize Cheese but dont record with it. use GTKRMD to record the Cheese Window With.

i would much prefer to use cheese entirely due to GTKRMD's Very Slow Encoding proccess....
I'm still looking for a "cure" for the low fps while recording with cheese though.

---

### Post by loell on 2010-04-05
does it only drop when you are recording?

---

### Post by Jazusa03 on 2010-04-05
> **loell said:**
> does it only drop when you are recording?

yes it only drops while recording. its fine when im just viewing from the cam.

---

### Post by littlepeon on 2010-04-05
k researched your camera a little
$40 camera that is on sale for $20...
that makes it a lower end web cam---not criticizing just stating a fact. i have tried the higher end logitec cams ($100) and have noticed that they tweak their drivers for windows....so whatever quality you get from windows..it will only be about 80 percent of that in linux....that being said..you can try these command line tricks...
also if your 'puter isn't fast..its gonna drop frames as usb uses computing cycles to function
i really recommend the one tip someone gave you about using gtk-recordmydesktop. you can use mplayer to create a window on your desktop with this command line function:
```
mplayer tv:// -vf mirror
```
your camera will be working at top speed...then you could then use GRMD to capture its feed....
mplayer has some workarounds for slower computers....

```
mplayer -framedrop -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all
```

work this into the first code and my usb2 camera will now work on a usb 1 device:

```
mplayer -framedrop -vfm ffmpeg -lavdopts lowres=1:fast:skiploopfilter=all tv:// -vf mirror
```



you can try to use ffmpeg to record:

```
ffmpeg -f alsa -r 16000 -i hw:2,0 -f video4linux2 -s 800x600 -i /dev/video0 -r 30 -f avi -vcodec mpeg4 -vtag xvid -sameq -acodec libmp3lame -ab 96k output.avi
```

that will probably be all around better for your system....

try thes out and report back to us on how they work for you

-Peon

---

### Post by Jazusa03 on 2010-04-08
This problem is still not solved: But after downgrading my distribution from 10.04 back to 9.10 cheese will record at normal frame speeds like it should, the 10.04 distribution will not. 

my conclusion is that it is not my hardware that is the problem, it is my version of Ubuntu or Cheese that is effecting my camera. 

in short i will be staying on 9.10 from now on untill they distribute the full long term support final release, after they have worked out all the bugs with cheese.

The quality i get in windows is slightly better but it is full speed and pretty much perfect. the quality i get in Ubuntu 9.10 is pretty descent, full speed, but lower resolution due to not having the drivers.
the quality i get in 10.04 is completely terrible, the first 2 sec are fine, but the rest of the time it is paused on 1 frame but the sound still plays normal.
in Short, and i know this is rather redundant due to it still being in beta for atleast 21 days. is that Lucid is still having bugs.

I have not solved the problem, but rather found a workaround to satisfy me for now.

---

### Post by no2498 on 2010-04-08
and cheese has all the webcam setting now days ubuntu give em to them

try wxcam
[http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)
you can get it from getdeb also

---

### Post by no2498 on 2010-04-08
pin it to the top panel comes on/up in like 2to3 seconds click record 

hope this helps

---

### Post by katja on 2010-04-30
Same problem here - I'm using an ASUS UL20A-A1 laptop with an integrated webcam.  Cheese worked (consistently) fine in 9.10, now video is (consistently) very choppy in 10.04.  The fps only drops after I start recording.  It improves somewhat if I lower the recording resolution - recording using the higher resolution, however, caused no problems in 9.10.

---

### Post by maphilli14 on 2010-05-18
Same issues here.  New system, lenovo W500.

To be honest, I've never had much success with cheese!  :(

Love to see it work flawlessly, but it just has never been consistent.  This is a built-in webcam in this one too.

Mike

---

### Post by valley1967 on 2010-06-06
I was having the same problem but have tried wxcam and it works great:P

---

### Post by hawthornso23 on 2010-12-25
Open "System>Preferences>Multimedia Systems Selector" and change the audio input from default to your sound card input. Try cheese again.

This fixed my problem.

Hypothesis = when you have a webcam with mic, cheese ends up fighting the audio system for access to the hardware unless you explictly tell the sound system not to go there.

---

### Post by niceguy123 on 2010-12-27
> **valley1967 said:**
> I was having the same problem but have tried wxcam and it works great:P

I tried downloading wxcam and was disappointed to learn that it doesn't work on 64 bit. I have cheese installed but it is not recording video, gets slow and stuck when I try. 


I would love to hear about another option for recoding video using my built in webcam.

BTW - Any ideas for recoding skype sessions? 

Thanks

---

### Post by no2498 on 2010-12-27
try using vlc media player open vlc click media, open capture device, play,record

hope it works for you

---

### Post by h2sammo on 2011-02-05
> **hawthornso23 said:**
> Open "System>Preferences>Multimedia Systems Selector" and change the audio input from default to your sound card input. Try cheese again.

This fixed my problem.

Hypothesis = when you have a webcam with mic, cheese ends up fighting the audio system for access to the hardware unless you explictly tell the sound system not to go there.

how do i achieve this in 10.10 netbook edition? i dont have that menu path

---

### Post by no2498 on 2011-02-05
open a terminal type gstreamer-properties click enter


that has the same things in it
first window is audio

---

### Post by tyler.hill100 on 2011-11-16
i also have the same problem with the internal webcam on my lenovo g555. i have found while testing the audio input in gstreamer-properties i have great fps with cheese. must be an audio problem as stated before. hope this helps somehow.

---

