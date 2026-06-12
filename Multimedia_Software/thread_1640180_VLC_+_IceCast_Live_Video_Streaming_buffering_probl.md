---
title: "VLC + IceCast Live Video Streaming buffering problem"
date: 2010-12-07
forum: Multimedia Software
---

### Post by Ark0 on 2010-12-07
Hello Guys

Im trying to set up a Live Video Streaming thats gonna run 24/7 im using

VLC 1.1.4
Icecast 2.3.2
Logitech HD webcam c270
Using Theora/Vorbis transcoding so far
Bandwidth 1400kb down 400kb up   (This is only for test so far)

all this on Ubuntu Maverick (10.10)

Problems im having.

Im only on testing stage, im testing this on LAN first and even on LAN im getting an excess of buffering, the video freez and loads and then resumes and its anoying and wont work like this.

Ive been trying to find the way to set up the VLC to send lower video quality or something to see if there lays the problemand i dont seem to find the rigt options, i have no clue  how to set up properly i dont know if it has to be on the transcoding options or what; id like some advices on where i have to beging configuring in order to mess with the stream quality and bandwidth or something!!

ALSO i tried to use the command line to stream but its so confusing i never manage to do it properly... i would like an exaple of using the comand line since i have been reading a lot of guides how to use the comand line and they are all very confusing.


PD: Im no hardcore programer nor experienced Linux user but im looking foward to learn a lot!

---

### Post by Ark0 on 2010-12-09
Allright i managed to make it work trough console! but i still cant  manage to configure the frame rate when i try to set some fps on the GI  it wont play anything the camera wont even open 

the comand line im using is 

```
$ vlc v4l2:// --sout "#transcode{vcodec=theo,vb=48,scale=1,width=320,height=240,acodec=none}:std{access=shout,mux=ogg,dst  =source:assword@127.0.0.1:8000//videomundial}"
```$ vlc v4l2:// --sout  "#transcode{vcodec=theo,vb=48,scale=1,width=320,height=240,acodec=none}:std{access=shout,mux=ogg,dst   =source:assword@127.0.0.1:8000//videomundial}"

---

### Post by Ark0 on 2010-12-29
Hello people!

alright i figure a lot of stuff, at the end its easier than i though problem is documentation its rly outdated

for the initial problem that was the execs of buffering i solved by setting the fps as i intended in the first place

in the transcode part of the command line its possible to include this without any more trouble

like #transcode{vcodec=theo,vb=48,fps=15,scale=1,width=480,height=320}

that was an example, normally if you use width and height you wouldn't need to use scale

also there are lots of options for the capture/input part, ive been trying and some work some dont on but its good to know they exist here is a site that describe some of them 
[http://wiki.videolan.org/Documentation:Modules/v4l2](http://wiki.videolan.org/Documentation:Modules/v4l2)
in there there is an option :v4l2-fps=   but it doesn't seem to be working for me, the vlc wont recognize so no idea there
the syntax its not very clear but it gives you a clue and im sure if you got some experience not like when i started it should be easier to figure

the line im using is 

```
vlc v4l2:///dev/video0:v4l2-fps=10 :v4l2-adev=hw:0,0 
--input-slave=alsa://hw:0,0 --sout "#transcode{vcodec=theo,vb=48,fps=5,scale=1,width=480,height=320,acodec=vorb,ab=32,channels=1,samplerate=44100}:std{access=shout,mux=ogg,dst=source:pasante@127.0.0.1:8000//videomundial}"
```and to use with ssh you would need to use cvlc instead of vlc unless you wanna use gui in which i thin you would need to activate server X (i think its just to type vlc -X)

the --input-slave seems very cool but im not really sure of its functionality first because its not working for me hehe and second because i never found documentation of that, i found about it in the #videolan channel @ irc.freenode and the GUI of the vlc uses it too

also the fact that there is an option of the v4l2 that calls the audio v4l2-adev=  but i think it only works when the audio its also been input by the v4l2 device or i don't know


and finally well i ran into another problem and i belive its a vlc bug

i cannot either play locally with vlc audio from the line in and video at the same time, nor offcourse stream them 

i use 

```
cvlc -v v4l2:// --input-slave=alsa://

```
and like that i only get Video

if i use 

```
cvlc -v   alsa:// --input-slave=v4l2://
```


I only get audio

Ive tried every syntax that i can imagine 
vlc, :input-slave= (which doesn't work) etc

so i believe its unbelievable that this is happening, how come i cannot play bot at the same time on vlc wen vlc its a program thats used to play media.... ? :s

well if i missed anything ill post!

---

