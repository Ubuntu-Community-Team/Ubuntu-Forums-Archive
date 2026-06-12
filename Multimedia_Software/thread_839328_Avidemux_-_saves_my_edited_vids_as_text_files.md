---
title: "Avidemux - saves my edited vids as text files?"
date: 2008-06-24
forum: Multimedia Software
---

### Post by mbellek on 2008-06-24
Anyone know what I'm doing wrong? 

At first Avidemux wouldn't open the audio file, I figured that part out, so now I can edit videos, but when I save, they are text files. 

The text file is as follows:

> //AD  <- Needed to identify//
//--automatically built--
//--Project: /home/joshua/Desktop/BudAthEdit1

var app = new Avidemux();

//** Video **
// 01 videos source 
app.load("/home/joshua/Desktop/BudAth1.AVI");
//02 segments
app.clearSegments();
app.addSegment(0,0,18000);
app.addSegment(0,22760,9);
app.markerA=0;
app.markerB=18008;
app.rebuildIndex();

//** Postproc **
app.video.setPostProc(3,3,0);

app.video.setFps1000(30000);

//** Filters **

//** Video Codec conf **
app.video.codec("Copy","CQ=4","0 ");

//** Audio **
app.audio.reset();
app.audio.codec("vorbis",128,8,"01 00 00 00 00 00 40 40 ");
app.audio.normalizeMode=0;
app.audio.normalizeValue=0;
app.audio.delay=0;
app.audio.mixer("NONE");
app.setContainer("AVI");
setSuccess(1);
//app.Exit();

//End of script


---

### Post by unoodles on 2008-06-24
Looks to me like you are use the "Save Project" button. To save your video, click File->Save->Video.

---

### Post by mbellek on 2008-06-24
> **unoodles said:**
> Looks to me like you are use the "Save Project" button. To save your video, click File->Save->Video.

That is what I was doing. 

Though, now, after saving it as described above, it still won't open with movie player it says "could not decode stream".

Also, Avidemux can't play the audio on most of my videos.

---

