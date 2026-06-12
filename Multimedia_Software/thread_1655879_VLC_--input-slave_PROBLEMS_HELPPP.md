---
title: "VLC --input-slave PROBLEMS HELPPP"
date: 2010-12-30
forum: Multimedia Software
---

### Post by Ark0 on 2010-12-30
alright im trying to stream Audio and Video from different sources
The web cam its on usb and the audio in the line in plug
im using that command line
```
 % vlc v4l2:// --input-slave=alsa://
```  

BUT it doesn't work it only plays the first one, and it only streams the first one

if i use 

```
% vlc alsa:// --input-slave=v4l2://
```

i only get the audio so what i figure ive tested with ```
:input-slave=
``` aslo and its the same result
ive tried with the device too
```
 vlc v4l2:///dev/video0 --input-slave=alsa://hw:0,0
``` 

(but it doesnt matter i only got 1 device of each and it auto-detects)

and almost every other syntax that you can imagine and ive always get the same thing the first one plays the slaved doesnt, it actually turns on the device because i can see the camera to turn the light on but it doest actually plays 

i tried 

```
% vlc --input-slave=alsa:// v4l2://  
``` and like this it plays the video, this tells me that the slaved its the one that gets screwed 

Another vry important thing is when i use the mic of the webcam it does play as slave so it seems that the --input-slave its to use the source coming on the same source? 

```
%vlc v4l2:// --input-slave=alsa://hw:1
```

Like that it works but doesnt when i use the hw:0,0 wich is my line in, the one i need to stream!!

HEEEEEEEELLLLLPPPPPPPPPPPPPPPPPPPPPPPP am i dealing with a bug herE?


I use ubuntu maverick 10.10 with vlc 1.1.5 , Logitech c270 HD

---

### Post by Ark0 on 2011-01-11
allright after much fighting and reinstalling and everything i made it work like this

Im not using alsa im using OSS
im using now Ubuntu Lucid 10.04
VLC 1.1.5

I didnt installed anything extra

the command i used was

```
    cvlc -vvv v4l2:// :input-slave=oss:// --sout="#transcode{vcodec=theo,vb=96,fps=25,width=240,height=180,acodec=vorb,ab=64,channels=1,samplerate=44000}:std{access=shout,mux=ogg,dst=source:pasante@192.168.1.44:8000//videomundial}"
```i would like to refine this comand line to have a perfect 24/7 feed of the Stream suggestions would be nice!!

Plz mark this as solved

---

