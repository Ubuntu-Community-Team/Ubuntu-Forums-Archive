---
title: "Is there a howto stream flash video for MythTV 0.24?"
date: 2011-02-21
forum: Mythbuntu
---

### Post by nhtrader on 2011-02-21
I understand MythTV is in the process of incorporating flash video. Is this in v0.24?

If not, just wondering if someone is willing to share instructions so that  a beginner could: 

1. use MythTV to convert recordings to flash video
2. enable mythweb to use flash video rather than ASX
3. enable mythtv to stream flash video to remote FE (outside of home network)


4. Should I wait for v0.25?

---

### Post by nickrout on 2011-02-21
Simply turn it on in mythweb settings!

[http://backendip/mythweb/settings/mythweb/flvplayer](http://backendip/mythweb/settings/mythweb/flvplayer)

---

### Post by nhtrader on 2011-02-21
> **nickrout said:**
> Simply turn it on in mythweb settings!

[http://backendip/mythweb/settings/mythweb/flvplayer](http://backendip/mythweb/settings/mythweb/flvplayer)


That was the easy part. Now on to getting MythWeb some flash videos to play.

What about using MythTV FE over internet? How do I play flash videos in this case?



For future newbies,

If your accessing mythweb from the same PC as your backend, then use
[http://localhost/mythweb/settings/mythweb/flvplayer](http://localhost/mythweb/settings/mythweb/flvplayer)

from other PC on home network:
[http://LAN-BackEnd-IP/mythweb/settings/mythweb/flvplayer](http://LAN-BackEnd-IP/mythweb/settings/mythweb/flvplayer)

from PC outside of home network:
[http://home-network-WAN-ip/mythweb/settings/mythweb/flvplayer](http://home-network-WAN-ip/mythweb/settings/mythweb/flvplayer)

---

### Post by nickrout on 2011-02-21
It converts to flash on the fly. Go to recorded programs in mythweb. Click the preview picture and another screen should open with the flash movie player embedded.

---

### Post by nhtrader on 2011-02-22
> **nickrout said:**
> It converts to flash on the fly. Go to recorded programs in mythweb. Click the preview picture and another screen should open with the flash movie player embedded.

This is fantastic. I just got a chance to try this out. And it works amazingly well. I can't believe that my meager dual core can handle this flash conversion on the fly and serve it up over a 90Kb/s connection.

On the other hand, I suppose that I'm using ideal conditions b/c I'm watching the recording while nothing else is being recorded. I'll have to try this when I'm recording 5 programs simultaneously. Secondly, I'm watching this program late at night on the eastern seaboard, so internet traffic is lower than it would be at other times. 

I still can't believe it was this easy b/c I spent hours googling and reading about many complicated procedures to transcode; write scripts; and tweak MythTV into do tricks to get it to play flash video.

What am I missing? Why are so many people employing scripts when this works so well?


PS - thanks for your help. This is awesome.

---

### Post by jlipoth on 2011-09-23
I have it working; however, it seems to ignore the settings portion.  I've tried setting a lower audio and video bitrate, but nothing seems to change.  It's unusable to wait 2-3 seconds for buffer time to watch 1 second of video!  Is there a config file I can edit to change this or an extra package I need to install?

---

### Post by nickrout on 2011-09-24
> **jlipoth said:**
> I have it working; however, it seems to ignore the settings portion.  I've tried setting a lower audio and video bitrate, but nothing seems to change.  It's unusable to wait 2-3 seconds for buffer time to watch 1 second of video!  Is there a config file I can edit to change this or an extra package I need to install?

I think you need to alter the source code in mythweb. There is a pretty easy to find function that prescribes the parameters passed to ffmpeg for the conversion.

EDIT: wow I see my last post here was 22 February. Must have been before 12:51 NZ time. How weird.

---

### Post by jlipoth on 2011-09-26
It works using by enabling and configuring the "settings" section on Mythweb!  I was confusing flash with the .asx streaming.  I am curious if it would be possible to adjust the .asx resolution/bitrate etc. as well.  

Also, if I want to watch a specific show LIVE through the internet (ie. a football game!)I have to do the following: 

1. VNC in the backend.

2. set the show to record in MythTV and make sure it is set to record extra long (imagine getting cut off as your favorite team goes into overtime :S).  

3. Open up VLC and open a "stream" window.

4. Track down the file that is used for recording.  This is a bit of a pain because all the recordings are named by channel and date and I have a lot of recordings!  I can get to the right channel and then look for the file that is growing fairly quick. I use this file as the source for the VLC stream.

5. Set the destination to and port that is accessible through HTTP (I've got my router forwarding this port).

6. Set it to trans-code down to a fairly small small (VLC trans-codes on the the fly)

7. Start the VLC stream and shut down VNC

8. Open up VLC on my local computer (laptop at the in-laws for example...)

9. Open a network stream and enter home IP address:port

10. Watch!

It's doable, but it's really cumbersome to set up!  Using myweb flash for this isn't an option at this point because I have to wait until the recording is done to be able to watch the ENTIRE recording.

Does anyone have a simpler way of streaming live TV?

---

### Post by nickrout on 2011-09-26
> **jlipoth said:**
> It works using by enabling and configuring the "settings" section on Mythweb!  I was confusing flash with the .asx streaming.  I am curious if it would be possible to adjust the .asx resolution/bitrate etc. as well.  

Also, if I want to watch a specific show LIVE through the internet (ie. a football game!)I have to do the following: 

1. VNC in the backend.

what is vnc for in this context?> 

2. set the show to record in MythTV and make sure it is set to record extra long (imagine getting cut off as your favorite team goes into overtime :S).  

3. Open up VLC and open a "stream" window.

4. Track down the file that is used for recording.  This is a bit of a pain because all the recordings are named by channel and date and I have a lot of recordings!  I can get to the right channel and then look for the file that is growing fairly quick. I use this file as the source for the VLC stream.

the file name is channel_starttime.mpg where start time is in the format YYYYMMDDHHMM00.mpg - so pretty easy to find when you know the start time.> 

5. Set the destination to and port that is accessible through HTTP (I've got my router forwarding this port).

6. Set it to trans-code down to a fairly small small (VLC trans-codes on the the fly)

7. Start the VLC stream and shut down VNC

8. Open up VLC on my local computer (laptop at the in-laws for example...)

9. Open a network stream and enter home IP address:port

10. Watch!

It's doable, but it's really cumbersome to set up!  Using myweb flash for this isn't an option at this point because I have to wait until the recording is done to be able to watch the ENTIRE recording.

Does anyone have a simpler way of streaming live TV?

Watch it on a TV wherever you are?

---

### Post by jlipoth on 2011-09-26
nickrout: I like the end of your post - very funny!  My inlaw's live in the middle of nowhere with basically 1 TV (unless I want to hang out in my father/mother in law's bedroom...creepy) It's quite common for main TV to be in use for other shows/videos games etc. 

I use VNC first to get into my MythTV backend which is located over 200Km away, in order to set up the VLC stream.

As for the filename, I am aware of the file name structure and I find it every time, it's just cumbersome compared to the Mythtv Guide. This is why all show listings in MythTV and Mythweb use different format, but that's pretty obvious..


Again, my question is:

Does anyone have a simpler way of streaming live TV?

---

### Post by nickrout on 2011-09-26
> **jlipoth said:**
> nickrout: I like the end of your post - very funny!  My inlaw's live in the middle of nowhere with basically 1 TV (unless I want to hang out in my father/mother in law's bedroom...creepy) It's quite common for main TV to be in use for other shows/videos games etc. 

I use VNC first to get into my MythTV backend which is located over 200Km away, in order to set up the VLC stream.

As for the filename, I am aware of the file name structure and I find it every time, it's just cumbersome compared to the Mythtv Guide. This is why all show listings in MythTV and Mythweb use different format, but that's pretty obvious..


Again, my question is:

Does anyone have a simpler way of streaming live TV?

OK I see the problem with needing vnc to use the gui of vlc. 

If I was serious about this I would set up a script that does it all, using vlc command line, and then use it as a post processing script in mythtv. However I am not sure if you can run jobs on an unfinished recording?

You can, however, commflag a recording in progress, so you could call your script as a commflag script and set commflag to work as the recording is in progress.

Or getting mythweb flash streaming to work on an unfinished recording may not be too hard.

Or give your in-laws a mythtv setup for Xmas...?

Or [http://www.slingbox.com/go/slingbox](http://www.slingbox.com/go/slingbox) ?

---

