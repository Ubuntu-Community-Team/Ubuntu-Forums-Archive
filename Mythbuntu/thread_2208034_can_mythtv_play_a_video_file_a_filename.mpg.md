---
title: "can mythtv play a video file? a filename.mpg?"
date: 2014-02-26
forum: Mythbuntu
---

### Post by sdowney717 on 2014-02-26
I set the default directory from /var/lib/record whatever,

to 

/home/scott/Videos

it took it, it starts up, run mythtv front end, there are no videos listed.
I tell it to scan for changes, there are no videos listed, it says something have you added group whatever??

Why cant it see the video files in the default directory?
What am I doing wrong, do I need to change all the backend locations to /home/scott/Videos from /var/lib/....

ok, I see a video place for myth, it will play.

Can I set this video place for a second partition on another drive, it should work I think

---

### Post by larsolav on 2014-02-26
Have you added  /home/scott/Videos to the video storage group in the backend setup?

---

### Post by sdowney717 on 2014-02-26
yes, and I got it to play the one video I pasted into that folder.

I am still stuck.
I am trying to get mythtv to recognize 

/media/scott/0C3655E6635050E4 INSIDE of mythfrontend

in that folder which is on another hard drive are hundreds of video files.

the backend, i put that ' /media/scott/0C3655E6635050E4 ' instead of /home/scott/Videos

saved and it took without errors, and did mythfilldatabase yes to both questions.

When I start mythfrontend, all I ever see is the first videofile (101 Dalmations)

So how to force a rescan? 
Is that what is needed?

---

### Post by sdowney717 on 2014-02-26
[http://www.mythtv.org/wiki/Video_Library](http://www.mythtv.org/wiki/Video_Library)

told me to run in termnal

mythutil --scanvideos

then when you go back to watch videos, it does do a rescan.

it is on 7%, so it must be filling the mysql database up with new videos.

Do you have to rescan like this when you copy in a new video file to that folder?

---

### Post by sdowney717 on 2014-02-26
opps!!!!

It is scanning in every single file on the drive!!!

I had to control-c the process ( running mythfrontend from terminal)


```
/APE/source/aecompat/aeservic.cmp : 19728f7f58c6e60f
2014-02-26 09:54:51.869743 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aecompat/aeworker.cmp : e806c83a76e9f25d
2014-02-26 09:54:52.416226 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aecompat/aewrkpvd.cmp : bef6b7710eecba43
2014-02-26 09:54:53.050202 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/aeexpdtr.rc : eb80c5dfa1da239d
2014-02-26 09:54:53.716621 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/aeexpdtr.res : 418e63bc3a6d50ba
2014-02-26 09:54:54.310796 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/aeexpdtr.vbp : 713a71a0665dd19b
2014-02-26 09:54:54.932104 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/callbkrf.cls : 3d789ea6ddc69ed5
2014-02-26 09:54:55.504091 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/expeditr.cls : d0a0304024c55120
2014-02-26 09:54:56.072707 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/frmexpdt.frm : 71601e546cb57f99
2014-02-26 09:54:56.715522 I  Adding :  : vbstuff/VB6.0 SP5 install/COMMON/TOOLS/APE/source/aeexpdtr/frmexpdt.frx : 55df7ee9eb8c0926
2014-02-26 09:54:57.233123 I  Adding :  : vbstuff/VB6
```

I guess the videos can sit in the root of the drive, they will need to be in a subfolder.

---

### Post by larsolav on 2014-02-26
If I understand correctly, you have a backend machine, and on that machine you have the folder  /home/scott/Videos listed under the videos storage group. In addition you have a folder with videos on a frontend machine that you want to have access through mythtv on the frontend? Is this correct? 

I dont have access to my system from work, so I don't know if you can set up the frontend to also include the local folder on the frontend. Maybe others know?

---

### Post by sdowney717 on 2014-02-26
I moved the video files into their own unique folder.
So now it works

---

