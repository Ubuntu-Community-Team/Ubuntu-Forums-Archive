---
title: "Transcode Errored: (exit status 255, job status was &quot;Errored&quot;)"
date: 2009-03-01
forum: Mythbuntu
---

### Post by Markus72 on 2009-03-01
Hi folx,

I googled like hell but didn't find any solution.
I use MythBuntu 8.04 and have 2 DVBT cards.
Everything works fine... recording, flagging commercials...

But no transcoding... I have to admit that I don't understand the setup completely. 

(I use German so maybe my translations don't fit exactly...)

When I try to configure my recording profiles, I see two standard entries:

* Hardware DVB Encoders
* Transcoders
* (create new profile group)

When choosing "Hardware DVB Encoders" the selection shows
* Default
* Live TV
* High Quality
* Low Quality

When choosing "Transcoders" the selection shows
* automatic detection from RTjpeg/MPEG4
* automatic detection from MPEG2
* High Quality
* Medium Quality
* Low Quality

What are both settings about? When I try to change the general TV settings I can choose a standard transcoding profile from the following:
* Auto detect
* High Quality
* Low Quality 
* Medium Quality

As you can see, the options don't match the profiles from above.
How are they related?

I ask all these questions because I'm really confused how to set up transcoding correctly...

When trying to transcode, my log shows:

```

2009-03-01 18:10:28.297 Transcoding from /media/data/mtv/1002_20090301171800.mpg to /media/data/mtv/1002_20090301171800.mpg.tmp                                            
2009-03-01 18:10:28.314 Connecting to backend server: 127.0.0.1:6543 (try 1 of 5)                                                                                          
2009-03-01 18:10:28.316 Using protocol version 40                                                                                                                          
2009-03-01 18:10:28.317 MainServer::HandleAnnounce Monitor                                                                                                                 
2009-03-01 18:10:28.320 adding: barebone as a client (events: 0)                                                                                                           
2009-03-01 18:10:28.321 MainServer::HandleAnnounce Monitor                                                                                                                 
2009-03-01 18:10:28.322 adding: barebone as a client (events: 1)                                                                                                           
2009-03-01 18:10:28.487 AFD: Opened codec 0x81ed040, id(MPEG2VIDEO) type(Video)                                                                                            
2009-03-01 18:10:28.488 AFD: codec MP3 has 2 channels                                                                                                                      
2009-03-01 18:10:28.489 AFD: Opened codec 0x81ed630, id(MP3) type(Audio)                                                                                                   
2009-03-01 18:10:28.489 AFD: codec MP3 has 2 channels                                                                                                                      
2009-03-01 18:10:28.490 AFD: Opened codec 0x81edc20, id(MP3) type(Audio)                                                                                                   
2009-03-01 18:10:28.509 No video information found!                                                                                                                        
2009-03-01 18:10:28.510 Please ensure that recording profiles for the transcoder are set                                                                                   
2009-03-01 18:10:28.511 Transcoding /media/data/mtv/1002_20090301171800.mpg failed                                                                                         
2009-03-01 18:10:28.516 Deleting /media/data/mtv/1002_20090301171800.mpg.tmp                                                                                               
2009-03-01 18:10:28.528 JobQueue: Transcode Errored: Das erstaunliche Schicksal des Generals Grant "Dokumentation USA 2002": High Quality (exit status 255, job status was "Errored")                                                                                                                    

```

Can someone help me?

Thaaaaaaanks a lot!

Markus

---

### Post by Markus72 on 2009-03-02
no idea?

---

### Post by Markus72 on 2009-03-02
please help!!!

---

### Post by erotomanic on 2009-03-02
I was wondering the same thing.  I don't get what the automatic detection does..  Maybe if the stream is RTjpeg/MPEG4 it uses one profile, if it is MPEG2 it uses another.

The only way I got transcoding to work was to edit the settings for High, Medium, Low to NOT use RTjpeg - use the other option instead (sorry, can't remember the exact steps).  After that it would seem to transcode and the file sizes would be reduced, although not by much.

---

### Post by pcooley on 2009-03-28
Another user suggested this:
 "go into Utilities / Setup -> Setup -> TV Settings -> Recording
profiles -> Transcoders -> Autodetect from MPEG2

opened the settings and saved them, and now it works. Looks like a bug in myth that you have to open and save a profile before it can be used ( maybe something to do with upgrading from older releases compared to a clean install ) "

It worked for me.

---

### Post by AboveTheLogic on 2009-04-07
Markus72, you ever get it working?

pcooley, I think your suggestion may have helped correct the problem I was experiencing (I think the same problem as Markus72).

---

### Post by davidstoll on 2009-08-24
pcooley,
your suggestion worked for me too.  I didn't actually change anything, I just went into the profile and hit "next" several times until I saw each page.

I recently upgraded to 9.04, so maybe that had something to do with it.

Nice find...how the heck could anyone have guessed that was the problem?

Has it been reported as a bug?



> **pcooley said:**
> Another user suggested this:
 "go into Utilities / Setup -> Setup -> TV Settings -> Recording
profiles -> Transcoders -> Autodetect from MPEG2

opened the settings and saved them, and now it works. Looks like a bug in myth that you have to open and save a profile before it can be used ( maybe something to do with upgrading from older releases compared to a clean install ) "

It worked for me.

---

### Post by wayover13 on 2011-01-26
> **pcooley said:**
> Another user suggested this:
 "go into Utilities / Setup -> Setup -> TV Settings -> Recording
profiles -> Transcoders -> Autodetect from MPEG2

opened the settings and saved them, and now it works. Looks like a bug in myth that you have to open and save a profile before it can be used ( maybe something to do with upgrading from older releases compared to a clean install ) "

It worked for me.

This is rather weird. I've had the same problem of transcode jobs erroring out on a newly-set-up 10.04.1 mythbuntu system to which I'm migrating. I tried what's suggested in this post--sort of; there's no "save" option when you follow Utilities / Setup -> Setup -> TV Settings -> Recording profiles -> Transcoders -> Autodetect from MPEG2, just "next" and "finish" buttons. So I hit "next," "next," "finish." And after having done that, the transcoding now completes.

This is exceptionally strange in my case since I just recently spent a lot of time rooting through menus trying to find a certain setting, and I'm sure I already did that "next," "next," "finish" thing under Utilities / Setup -> Setup -> TV Settings -> Recording profiles -> Transcoders -> Autodetect from MPEG2--probably more than once. I'll need to see now if the successful transcoding persists after reboots or other system events.

James

---

