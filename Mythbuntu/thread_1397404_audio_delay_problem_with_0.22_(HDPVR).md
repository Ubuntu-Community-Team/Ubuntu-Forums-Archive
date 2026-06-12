---
title: "audio delay problem with 0.22 (HDPVR)"
date: 2010-02-03
forum: Mythbuntu
---

### Post by davidstoll on 2010-02-03
Before 0.22, I used a custom script to dump video from my HDPVR1212 as a mp4 and mythtv played the files without any problem.
[http://github.com/jettero/videodump-pl](http://github.com/jettero/videodump-pl)

Now that 0.22 supports the HDPVR, it's nice for the program guide and searching functions rather than an external script, but there are serious audio delay problems and they get worse as the recording goes on.  Adjusting the audio sync does not help, it is more severe than what the audio sync can compensate for...but you would have to keep changing it (as it gets worse) anyway.

Is there anything I can do to help this?

---

### Post by nickrout on 2010-02-04
> **davidstoll said:**
> Before 0.22, I used a custom script to dump video from my HDPVR1212 as a mp4 and mythtv played the files without any problem.
[http://github.com/jettero/videodump-pl](http://github.com/jettero/videodump-pl)

Now that 0.22 supports the HDPVR, it's nice for the program guide and searching functions rather than an external script, but there are serious audio delay problems and they get worse as the recording goes on.  Adjusting the audio sync does not help, it is more severe than what the audio sync can compensate for...but you would have to keep changing it (as it gets worse) anyway.

Is there anything I can do to help this?

I understand there are various options in terms of bitrate, audio codec etc. What options are you using?

---

### Post by davidstoll on 2010-02-04
> **nickrout said:**
> I understand there are various options in terms of bitrate, audio codec etc. What options are you using?

I don't believe there are options for bitrate and codecs.

---

### Post by nickrout on 2010-02-04
Not according to this:

[http://www.mythtv.org/wiki/HDPVR](http://www.mythtv.org/wiki/HDPVR)

You can control the overall bitrate and whether you are capturing spdif or analogue.

I can't see anything on that page about audio sync, but you might like to search the mailing list archives, there has been a lot about these beasties on there:

[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

---

### Post by davidstoll on 2010-02-04
> **nickrout said:**
> Not according to this:

[http://www.mythtv.org/wiki/HDPVR](http://www.mythtv.org/wiki/HDPVR)

You can control the overall bitrate and whether you are capturing spdif or analogue.

I can't see anything on that page about audio sync, but you might like to search the mailing list archives, there has been a lot about these beasties on there:

[http://www.gossamer-threads.com/lists/mythtv/users/](http://www.gossamer-threads.com/lists/mythtv/users/)

That was primarily targeted for people manually installing the driver before 0.22 supported it....as I did.  But it worked before 0.22...and I never changed any sort of bitrate setting.

---

### Post by nickrout on 2010-02-04
Have you searched the mailing list as I suggested? I guess not.

I have never used a hdpvr, I am merely trying to help. I thought I had seen mention of specific bitrate and codec issues on the mailing list, and a search there reveals that I am right.

But clearly I have to do the search for you. Sorry to go on but it is pretty typical of people on this forum that they do not know how to access the primary source of help for mythtv - the mailing list. Even when pointed there they don't look.

The first entry in a search for > hdpvr audio sync is this thread:

[http://www.gossamer-threads.com/lists/mythtv/users/399665](http://www.gossamer-threads.com/lists/mythtv/users/399665)

Surprise surprise it includes this post:

> **Re: HDPVR audio out of sync in 5.1 AC-3 mode **
The problem is solved.

I had to reduce the video bit rate. ether by changing the TV to 720p or by reducing the bit rate from 13500000 to 1300000 in the recording profile.
Since I did not know which recording profile is the correct I reduced it on all of them.  

Whether this will solve the problem for you I do not know, but at least you now know where and how to look.

---

### Post by davidstoll on 2010-02-05
> **nickrout said:**
> Have you searched the mailing list as I suggested? I guess not.

I have never used a hdpvr, I am merely trying to help. I thought I had seen mention of specific bitrate and codec issues on the mailing list, and a search there reveals that I am right.

But clearly I have to do the search for you. Sorry to go on but it is pretty typical of people on this forum that they do not know how to access the primary source of help for mythtv - the mailing list. Even when pointed there they don't look.

The first entry in a search for  is this thread:

[http://www.gossamer-threads.com/lists/mythtv/users/399665](http://www.gossamer-threads.com/lists/mythtv/users/399665)

Surprise surprise it includes this post:

 

Whether this will solve the problem for you I do not know, but at least you now know where and how to look.

No, it doesn't, but read further and the answer will probably hit you.

I've seen that post before, read further and you will see that it didn't fix the guys problem, he spoke too soon.  I've seen this post before.  It is sort of funny that you yell at me for not reading.  It's easy to find a solution if you really are only in it to prove an unrelated point.

I forgive you for jumping down my throat.  Why, because I know that people DO ask repetitive questions and (by and large) most people hear are friendly.  I could be unique in my exact issue, but more likely someone out there has had this issue.  I just haven't found it yet.  Many times, I find that there is some buzz word (technical phrase) that people don't use when searching for something (especially for a unique problem).  I am also guilty of that.  But if I don't know the buzz word, how can I use it to search.

I have my external device plugged set as 720p because anything higher 1080i or p doesn't really work well...if at all.

By the way, I also have the latest firmware 1.5.6.1 (at least it's the newest as far as I can tell).

Reducing the bitrate is NOT the problem.  I have an HDHomerun that records at 1080p and has a much higher bitrate.  No problems there.  It must be the way the file is packed or maybe some sort of audio buffer issue (maybe ALSA?).

On with my testing...and searching ;)

---

### Post by davidstoll on 2010-02-08
The audio delay actually gets worse as time goes on.  At the beginning, it seems ok and then after a few minutes, you start to notice a change...or **drift**.  So, using that key word, I searched around and found some people were also referring to this as "drift".  Using the right word makes all the difference in your searching.

People were noticing that the video was recording at 60fps rather than 59.94 (like the audio).  Sure enough, so was mine.  Using MediaInfo, I was able to easily confirm this.

I had installed the most recent driver/firmware (in windows).  Hauppauge calls it a driver, but it is actually both.  This was supposed to fix the problem, but obviously had not.  I called Hauppauge to inquire about it.  I asked if there was a way to confirm that the firmware actually "took".  They said no.  How dumb is that?  So, I re-installed the firmware/driver in windows.  It said that everything went fine.  I put it back on my Myth box and it still had the same problem.

Next, I hunted down an old driver/firmware and installed that.  Blammo, it worked.  My videos were 59.94fps!  I went back (just for giggles) and re-installed (for the 3rd time) the newest firmware/driver and it continued to record videos at 59.94fps.

So, either the new firmware simply won't take on my unit and I'm on the old firmware....or putting an old firmware on the box and then trying the new firmware again worked...?

But, there is NO WAY to tell what firmware you have on the box.  Dumb dumb dumb.

I do know that older firmware can be a little problematic.  The box can freeze up and Linux can even sometimes loose the device...i.e. you need to unplug the USB and plug it back in.

So far, I have not had that problem, so I suspect that the new firmware did take.

:)

---

### Post by nickrout on 2010-02-08
I'm glad you got it fixed, and I apologise for being a bit too sarcastic. I knew I had seem stuff that might have bene relevant to you and which involved bitrates and codecs. Sorry if it took you up the garden path somewhat.

Good to know you have it sorted anyway.

You REALLY should add something about this to the wiki page.

---

### Post by davidstoll on 2010-02-18
I added something to the discussions part of the HDPVR wiki, but it looks like I am "not authorized" to edit the main page even though I have an account.

This is more an experience rather than the norm (or a fact).  Even if I had the ability to edit the main page, I'm not sure if it would be appropriate.

[http://www.mythtv.org/wiki/Hauppauge_HD-PVR](http://www.mythtv.org/wiki/Hauppauge_HD-PVR)
click on "discussions" tab at the top

Here is what I added...

**Firmware issue**
At this time, the only way to load firmware on the unit is to use a Windows machine. The download from the Hauppauge web site calls it a "driver", however, this is actually a Windows driver and HDPVR firmware combination upgrade. There is no way to tell what firmware is on your unit (Hauppauge has confirmed this). So, if you are having trouble with your HDPVR (i.e. audio drift or recording at 60fps rather than 59.94), the best thing to do is try to upgrade the firmware. If the stated firmware clams a particular fix and the update does not fix it, try again. Another thing to try is to find an older version of the firmware and "downgrade" to that and then try the newer firmware again. After upgrading the firmware, be sure to let Windows reboot. I believe there is further updating that occurs as Windows reboots after the firmware update (I can't confirm this, but it's better to be safe than sorry).



> **nickrout said:**
> I'm glad you got it fixed, and I apologise for being a bit too sarcastic. I knew I had seem stuff that might have bene relevant to you and which involved bitrates and codecs. Sorry if it took you up the garden path somewhat.

Good to know you have it sorted anyway.

You REALLY should add something about this to the wiki page.

---

### Post by davidstoll on 2010-03-20
Bad news...
It's back to recording at 60fps.

:(

re-flashed with (the same) latest driver/firmware (in Windows)...again...and now it's working...again...

not working again...

After re-flashing, it only seems to work by recording at 59.94fps for a day and then reverts back to 60fps.

weird

---

