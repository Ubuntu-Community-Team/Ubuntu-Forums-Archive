---
title: "Hauppauge HVR-2250 Blue Screen for LiveTV and Recordings"
date: 2011-09-12
forum: Mythbuntu
---

### Post by bananagranola on 2011-09-12
I've searched and searched, and I can't find a solution to my problem. If anyone could help me out a little, I would be ever so grateful.

I have a MythBuntu fresh installation with a Hauppauge HVR-2250 card, and MythTV sees both its analog and digital sides; I used jorandal's [post ]("http://ubuntuforums.org/showthread.php?t=1567490&page=10")to do so. 

For both LiveTV and recordings, I get a blue screen; I have information about the channels from ScheduleDirect, but that's all that shows on the screen. 

I've seen people on the forums with blue screens for LiveTV but not recordings; however, my recordings are also blue.

I've gone through each input trying to use it, but they either segfault (aux) or bluescreen (svideo, composite, tuner). 

I'm trying to use svideo from my cable box.

Any help would be greatly appreciated.

---

### Post by nickrout on 2011-09-13
What do your logs tell you?

---

### Post by bananagranola on 2011-09-14
Wow, that was a fast reply.

All of my log files? Frontend and backend? Are these the ones in /var/log/mythtv, or are you referring to other ones?

---

### Post by nickrout on 2011-09-14
the frontend and backend logs. Look at around the time the recording starts.

---

### Post by LowSky on 2011-09-14
Sounds like you set the tuner up wrong on the backend maybe?

---

### Post by bananagranola on 2011-09-17
I've attached the text files of mythbackend.log and mythfrontend.log. There's error messages; I've tried to figure them out to the best of my ability on the backend settings, but I'm not sure what I'm doing wrong here...

Much thanks for any help you can give me!

Also, it's doing this thing right now where the frontend crashes with exit code 139. I'm not sure what I did to break it, but I broke it...

---

### Post by nickrout on 2011-09-18
Looks to me like you haven't finished the backend setup.

---

### Post by LowSky on 2011-09-18
I does look like the backend isn't setup completely.

---

### Post by bananagranola on 2011-09-18
Does anyone know more about what I'm setting up wrong? I have the cards set up on V4L as separate cards with vbi0 and vbi1, and the sources from SchedulesDirect (which is getting channels and info about the channels), and the inputs on svideo only (the rest have no sources). The save locations are the defaults.

---

### Post by bananagranola on 2011-09-18
Does anyone know more about what I'm setting up wrong? I have the cards set up on V4L as separate cards with vbi0 and vbi1, and the sources from SchedulesDirect (which is getting channels and info about the channels), and the inputs on svideo only (the rest have no sources). The save locations are the defaults.

For example, in mythbackend, what does it mean when it says 
> format_to_mode() does not recognize V4L1and 
> 2011-09-16 21:51:24.256 TVRec(10) Error: Problem finding starting channel, setting to default of '3'.
2011-09-16 21:51:24.575 ChannelBase(10) Error: InitializeInputs(): 
            Could not get inputs for the capturecard.
            Perhaps you have forgotten to bind video
            sources to your card's inputs?and in mythfrontend:
> 2011-09-16 21:49:27.343 LIRC, Error: Failed to connect to Unix socket '/dev/lircd'
            eno: No such file or directory (2)Some permissions problems came up, so I made /var/lib/mythtv and the folders inside it have all permissions. 

I also changed the analog cards from Analog V4L to IVTV MPEG-2 encoder card. Now it's not crashing; it's just bluescreening.

---

### Post by nickrout on 2011-09-18
What version of mythtv are you using?

```
dpkg -l mythtv-frontend
```

---

### Post by bananagranola on 2011-09-18
I'm running:
> mythtv-fronten 2:0.24.0+fixes A personal video recorder application (clien

---

### Post by LowSky on 2011-09-18
did you make sure to set the input device to svideo?

---

### Post by nickrout on 2011-09-18
> **bananagranola said:**
> I'm running:

the string should be longer than that. Maximise your terminal and you will get something like this:

> ii  mythtv-frontend                               2:0.24.1+fixes.20110911.8f865a6-0ubuntu0mythb A personal video recorder application (client)


Its the number after fixes that counts, this bit 20110911.8f865a6

Anyway make sure you have mythbuntu-repos enabled and updaste to the latest mythbuntu packages. It looks to me like the v4l1 bug that existed when 11.04 was issued.

---

### Post by nickrout on 2011-09-18
> **bananagranola said:**
>  

I also changed the analog cards from Analog V4L to IVTV MPEG-2 encoder card. Now it's not crashing; it's just bluescreening.

I am not sure, but these cards are said to have hardware encoders, so I am guessing ivtv mpeg-2 encoder is correct.

---

### Post by bananagranola on 2011-09-19
Man, I'm sorry that I'm taking so long to respond compared to all of you helping me. I'm in law school during the day, so I only have time at night to see these...

I've set s-video as the default input on both capture cards, and the s-video definitely has a video source. 

I'll check whether mythbuntu's repo is enabled; that sounds like it might be promising.

---

### Post by bananagranola on 2011-09-23
An update to everyone:

Today, I added the mythbuntu repo, and it worked! :)

Thanks for everyone's help!

---

