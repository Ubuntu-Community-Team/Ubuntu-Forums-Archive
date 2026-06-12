---
title: "mythtv - no display for atsc signals"
date: 2006-11-11
forum: Multimedia &amp; Video
---

### Post by Vincent_Lin on 2006-11-11
I have a situation about mythtv 0.20.  I need help to figure out what happened.

mythtv 0.20 running under edgy on P4 machine with Intel GPU running i810 xserver.  I used synaptic to install mythtv with some help in mysql book so that mysql user setup has no issues.

TV tuner card is Kworld atsc-110 with over the air atsc/hd signals.

The problems I have are:

1. mythfrontend does not display any video signals on screen.  Audio is there. Recording appears successful with mpeg file created.  I can use vlc or mplayer to play these recorded mpeg files with audio.  mythfrontend just does not display video signals.  

2. Everytime I click on Watch TV, recording starts.  How can I set it not to record signals while just watching?  Scheduling appears successful, as well.

Thanks in advance.

Vincent Lin

---

### Post by superm1 on 2006-11-11
> **Vincent_Lin said:**
> I have a situation about mythtv 0.20.  I need help to figure out what happened.

mythtv 0.20 running under edgy on P4 machine with Intel GPU running i810 xserver.  I used synaptic to install mythtv with some help in mysql book so that mysql user setup has no issues.

TV tuner card is Kworld atsc-110 with over the air atsc/hd signals.

The problems I have are:

1. mythfrontend does not display any video signals on screen.  Audio is there. Recording appears successful with mpeg file created.  I can use vlc or mplayer to play these recorded mpeg files with audio.  mythfrontend just does not display video signals.  

2. Everytime I click on Watch TV, recording starts.  How can I set it not to record signals while just watching?  Scheduling appears successful, as well.

Thanks in advance.

Vincent Lin

For the first problem, make sure that you have no other media players running at the same time.  Myth uses xv to play back content, but most video cards can only accelerate one stream via xv at a time.  Also, what video card driver are using?

Well this is the way that mythtv works.  Live tv will record to files.  These will be automatically expired before other recordings as space as needed.

---

### Post by Vincent_Lin on 2006-11-13
Thanks for the response.

So point 2 is no point.  I just have to know how mythtv is working.  Thanks.

As to point 1.  It is still puzzling me.  I am sure that I don't have any other media player running, not to mention using xv as output.  I know that I setup mplayer to use GL output, for it gives me better color.  Xv output gives me sort of washout color, which I don't like at all.  Unfortunately, I did not find enough time over the weekend to work on it.  I did try this:
I installed mythtv forntend on my T42 laptop.  I already assigned static ip for all my machines while at home.  And then I added the same mythtv user at my T42's ip to mysql server running on THE troubled machine.  You know what?  It works.  I can see the footbll game playing at HD.  Though the screen freezes 2 seconds every 3 seconds.  I guess the bandwidth of 802.11g is simply not enough.  (BTW, do you think 10 mbps is enough for this purpose?  Or I have to go up to 100 mbps?)  At least, I know that mythtv server + mysql server setup is correct, since I can add another mythtv client on a nother machine and still get live tv.

The machine with trouble is running i810 driver and with direct rendering enabled.  mythtv frontend, I set it to run, with OpenGL rendering and mouse enabled.  I hope this has nothing to do with the problem I have, since T42 is using ATI mobility and with Beryl enabled.  But, anyway, the thing I did not/have not tried, is to use vesa driver for xserver, and use Qt for mythtv frontend rendering.

I am going to have a one day business trip to NYC, and so I could not play with it more.  Hope there are more options I can try, if I know them, then.

Thanks again.

Vincent Lin

---

### Post by Vincent_Lin on 2006-11-13
Sorry for the duplicate post.

Deleted.

---

### Post by superm1 on 2006-11-17
> **Vincent_Lin said:**
> 
I installed mythtv forntend on my T42 laptop.  I already assigned static ip for all my machines while at home.  And then I added the same mythtv user at my T42's ip to mysql server running on THE troubled machine.  You know what?  It works.  I can see the footbll game playing at HD.  Though the screen freezes 2 seconds every 3 seconds.  I guess the bandwidth of 802.11g is simply not enough.  (BTW, do you think 10 mbps is enough for this purpose?  Or I have to go up to 100 mbps?)  


10mbps should be adequate for most HD stuff, but you can verify by using an ethernet connection.  I know my r50p can handle watching HD wirelessly, but will drop out every so often when it can't hold a sustained speed long enough.  Not as frequent as 2-3 seconds.  This is more likely due to it having to scaled the picture instead of running at native res, as well as your settings for the mpeg2 decoder and the audio buffering.  Getting HD working is always fun :)

> **Vincent_Lin said:**
> 
At least, I know that mythtv server + mysql server setup is correct, since I can add another mythtv client on a nother machine and still get live tv.

The machine with trouble is running i810 driver and with direct rendering enabled.  mythtv frontend, I set it to run, with OpenGL rendering and mouse enabled.  I hope this has nothing to do with the problem I have, since T42 is using ATI mobility and with Beryl enabled.  But, anyway, the thing I did not/have not tried, is to use vesa driver for xserver, and use Qt for mythtv frontend rendering.

I am going to have a one day business trip to NYC, and so I could not play with it more.  Hope there are more options I can try, if I know them, then.

Thanks again.

Vincent Lin
There was a bug opened at one point for the 810 chipset related to XV playback I know, but I don't think it was ever resolved.  Are you using beryl on the computer with the 810?  If so, can you temporarily just switch to metacity, to make sure that there are no Xv related problems with having beryl on?  I have read about some people with these problems.  Also, are you trying to play hidef stuff?  Some integrated cards don't have enough vram to handle playing hidef.

Alternatively,
If you really want to run without Xv acceleration, this can be achieved by:
NO_XV="1" mythfrontend

---

### Post by Vincent_Lin on 2006-11-18
Wow!  Thanks again for the reply and detail possibilities.

I just tried vesa driver for X and the display of high-def proadcating came out (instead of a band of blue across left-to-right in the middle about 2-thirds of the hight), but very very VERY slow, even slower than using T42 to view highdef stuff via wireless.  As I said before, the recording and replay outside mythtv is always fine.

I don't use beryl when I am trying this mythtv+highdef stuff.  But, Beryl on this specific machine works fine - P4 2.66 + Intel 915.

When I enabled beryl and ran mythfrontend, I encountered the "taskbar on top of mythfronrend" behaviour, which I can live with.  Still, the highdef broadcasting is a blue band about 2-thirds of the screen hight in the middle.

Do you know of any possible xorg.conf tweak that can help to work around the i810 bug you mentioned in your mail?

Thanks.

Vincent Lin
PS. NO_XV="1" mythfrontend did bring back the display of highdef broadcasting.   Except it was so slow that I was like watching a slideshow of the images, not video.

Really, are there any tweaks in xorg.conf that can work around i810 xv bug?

Thank you very much.

---

### Post by superm1 on 2006-11-19
If this is just happening for hidef, I'd be willing to be its related to not enough vram on the graphics card.  Considering its integrated, can you dedicate more ram in the bios to it?  Running under NO_XV is usually a bad idea since that takes away all your graphics acceleration provided by the card.

I can relate something similar to this and proving that its graphics memory related.  I have a girlfriend who I can't convince to use linux yet...  She has a 810 chipset, and i'll bring over some HD recordings and try to play them on her windows box.  The machine will play audio, but the screen very ungracefully goes blank.  I went into the bios and assigned more ram to 810, and suddenly it was able to work :)

---

