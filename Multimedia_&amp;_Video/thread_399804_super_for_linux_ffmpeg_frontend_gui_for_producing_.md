---
title: "super for linux ffmpeg frontend gui for producing h264 and 3g9 files"
date: 2007-04-02
forum: Multimedia &amp; Video
---

### Post by koshari on 2007-04-02
after 3 attempts to install ffmpeg with 3gp support from guides on these forums failing in my scenario i decided to simply install erightsoft super (Simplified Universal Player Encoder & Renderer).

it installed fine and worked as expected in the virtual machine and i must say i was pleasently suprised with its simplicity and quality (no doubt the quality is just as good for other linux users who have ffmpeg installed properly and can use it). so i finally had a solution to encode content for my nokia 6131 phone.

because i only have a virtual machine installed on one of my machines i figured the next step was to try and install it through wine, unfortinately it failed where it was trying to register the vorbis plugin and wine barfed with a prompt stating it needed a mozilla active x plugin, upon a bit of googling i found others had various other problems installing it.

so for me it looks live either i set up virtual server on the other machines, or persist with only using it from the one.

the interface looks like a java style interface and is a little stuffy and if the producers were to use a nice dev kit like qt4 i beleave it could come up looking pretty snazzy indeed.

infact looking at the way it simply calls from the functions of ffmpeg, MEncoder, mplayer, x264, mppenc,  ffmpeg2theora & the theora/vorbis RealProducer plugIn i was suprised theres not a frontend written for linux, 

i have seen some criticism that erightsoft wont release the code of the frontend, however i can hardly mock them as there little app has gotten me out of the pickle i was in but it does beg the question of just how complex it would be given its written to operate on the top of what is essentually gpl code. the way i see it the open source comunity has the bulk of the work done in this application and its only the icing on the cake thats missins, 

i would be interested in hearing other peoples thaughts on this project, and also if i may have missed a gpl,ed project of creating a frontend for these tools already.

---

### Post by FakeOutdoorsman on 2007-04-08
Did you check out [Vive]("http://vive.sourceforge.net/"), [Sive]("http://sive.sourceforge.net/"), or [thinliquidfilm]("http://thinliquidfilm.org/")?  They are all GUIs for ffmpeg.  See the Ubuntu wiki for more info: [Encoding Video for the iPod Video]("https://help.ubuntu.com/community/iPodVideoEncoding")

---

