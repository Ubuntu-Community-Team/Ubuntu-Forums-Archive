---
title: "deinterlacing issues"
date: 2008-05-04
forum: Mythbuntu
---

### Post by milhouse on 2008-05-04
I'm running mythbuntu 7.1/ myth 0.21.20080304-1.  Ever since the 0.21 upgrade I have been having issues with playback/deinterlacing SD content.  I am displaying on a 720p HDTV running at 1360x768.

Specifically, the deinterlacing seems to come and go.  Also with certain programs I get vertical "jitter" that comes and goes.  This is most apparent on a station that seems to letterbox it's SD signal so it appears to be closer to 16:9 but it doesn't fill the screen.  With this signal you readily see the top and bottom edge of the video and the whole frame jumps up and down by a pixel or so for short stretches.  It does this on and off all of the time.

I ran with verbose playback logging and with a problem show I see a lot of this:

```
2008-05-03 19:39:39.994 NVP: progressive frame seen after 40 interlaced  frames
2008-05-03 19:39:40.027 NVP: interlaced frame seen after 1 progressive frames
2008-05-03 19:39:40.194 NVP: progressive frame seen after 7 interlaced  frames
2008-05-03 19:39:40.227 NVP: interlaced frame seen after 1 progressive frames
2008-05-03 19:39:40.394 NVP: progressive frame seen after 7 interlaced  frames
2008-05-03 19:39:40.427 NVP: interlaced frame seen after 1 progressive frames
2008-05-03 19:39:41.794 NVP: progressive frame seen after 43 interlaced  frames
2008-05-03 19:39:41.827 NVP: interlaced frame seen after 1 progressive frames
2008-05-03 19:39:41.994 NVP: progressive frame seen after 7 interlaced  frames
2008-05-03 19:39:42.060 Disabled deinterlacing
'video_output' mean = '39641.30', std. dev. = '13316.17', fps = '25.23'
2008-05-03 19:39:42.160 NVP: interlaced frame seen after 5 progressive frames
2008-05-03 19:39:42.160 Enabled deinterlacing
2008-05-03 19:39:42.193 NVP: progressive frame seen after 3 interlaced  frames
2008-05-03 19:39:42.260 NVP: interlaced frame seen after 2 progressive frames
2008-05-03 19:39:42.360 NVP: progressive frame seen after 5 interlaced  frames
2008-05-03 19:39:42.427 Disabled deinterlacing
2008-05-03 19:39:42.660 NVP: interlaced frame seen after 9 progressive frames
2008-05-03 19:39:42.660 Enabled deinterlacing

```

While myth thinks that the show is on again/off again interlaced, I can see that it is clearly interlaced.I have tried numerous playback profiles.  I have also tried every deinterlacer available.  The 2x deinterlacers show another weird effect where they will almost display a double image of moving objects on and off.  

I have no problems with HD content.

Any ideas?  Is there a way I can force deinterlace on?

---

### Post by Chuckels550 on 2008-05-06
Why would you want deinterlacing with 720p?  The picture is using a progressive scan - operating more like a monitor than a analog TV.  I would deactivate the deinterlacing.

---

### Post by milhouse on 2008-05-06
Exactly, and many sources are interlaced which is why you want to deinterlace for display on a progressive scan monitor :)  Or in my case, sometimes interlaced, and sometimes not.  When myth turns off the deinterlacer and then a batch of interlaced frames is displayed (but not enough to cause myth to turn the deinterlacer back on, it looks like crap.

I found [this thread]("http://www.nabble.com/Jitterometer%3A-Mixed-progressive---interlaced-frames--td13953948.html") which covers what I am seeing.  It seems that currently myth doesn't handle these mixed streams very well and there was a bit of a discussion on how to handle this but it is hard to say if this has gone anywhere.  The fix seems simple enough, 'You should manually force "interlaced" from playback menu for this type of channels/broadcasts'.

Only problem is that I can't seem to find that option :confused:  It isn't in what I think is the playback menu (the menu that comes up when I right arrow from a selected show in the "recordings" menu).

Anyone know of this playback menu he is speaking of?

---

### Post by milhouse on 2008-05-08
I found it.

You can force deinterlacing by hitting "m" when playing back a recording.  This bring up the playback menu.  Then you can select video scan -> interlaced.

---

