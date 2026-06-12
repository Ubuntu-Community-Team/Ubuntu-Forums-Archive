---
title: "Cant save or open edited video files"
date: 2011-07-15
forum: Multimedia Software
---

### Post by MrRoadRace on 2011-07-15
Hi Guys, 

I am using Avidemux video editor. I can upload a video and it plays fine on the Movie Player. Once I upload it to Avidemux and save the edited video it saves as a text file and will not open with any player whatsoever. When It saves it saves like this:

Please help, thanks in advance!


//AD  <- Needed to identify//
//--automatically built--
//--Project: /home/maynor/Desktop/Savetest

var app = new Avidemux();

//** Video **
// 01 videos source 
app.load("/home/maynor/Desktop/mariogt5.2.AVI");
//01 segments
app.clearSegments();
app.addSegment(0,0,3772);
app.markerA=0;
app.markerB=3771;

//** Postproc **
app.video.setPostProc(3,3,0);

app.video.fps1000 = 20000;

//** Filters **

//** Video Codec conf **
app.video.codec("Copy", "CQ=4", "0 ");

//** Audio **
app.audio.reset();
app.audio.codec("copy",0,0,"");
app.audio.normalizeMode=0;
app.audio.normalizeValue=0;
app.audio.delay=0;
app.audio.mixer="NONE";
app.setContainer("AVI");
setSuccess(1);
//app.Exit();

//End of script

---

### Post by varunendra on 2011-07-16
Hi MrRoadRace, and welcome to the forums!

You are saving the 'Project' instead of saving the video (File > Save > Save Video...).

---

