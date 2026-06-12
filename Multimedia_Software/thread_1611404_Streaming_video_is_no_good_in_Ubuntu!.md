---
title: "Streaming video is no good in Ubuntu!"
date: 2010-11-01
forum: Multimedia Software
---

### Post by Tiddens on 2010-11-01
I am elevating this thread up a level from [http://ubuntuforums.org/showthread.php?t=1598403&highlight=Tiddens&page=2](http://ubuntuforums.org/showthread.php?t=1598403&highlight=Tiddens&page=2) . Ubuntu 9.10 no longer streams without the screen pausing and going black every 2 minutes! Our product was just going into production and now we need to hopefully find a version of Ubuntu that streams video! We couldn't go with Unbuntu 10.04 because the video streaming was 30% slower than 9.10. Any help appreciated! We are really trying to use and promote Ubuntu, but this is alarming!

---

### Post by Tiddens on 2010-11-02
We found a solution to the glitching streaming video problem!  It is Ubuntu 8.04.4 LTS (Hardy Heron), which an engineer tipped us off was the last, least buggy, version of Ubuntu.  Very frustrating that newer versons of Ubuntu recently picked up the streaming glitch.  

All versions of Ubuntu should be promoted equally on the Ubuntu website (since later versions are not neccessarily better, unlike most any other software).  The website just promotes Ubuntu 10, which has the streaming glitch (and other problems, including slow streaming speed & therefore bad picture quality, we can't get it to play sound on our system, some icons must have the file extentions in their titles, etc.).  
 
It wasn't easy to find the previous versions to download.  On the download page it says "Take a look at a full list of our previous versions and alternative downloads", but clicking on that only takes you to more Ubuntu 10 downloads...

---

### Post by Chronon on 2010-11-02
Is there an open bug report you can point us to?  I haven't experienced anything like you are describing.

---

### Post by Tiddens on 2010-11-02
I haven't taken the time to figure out bug reports yet.  Just trying to use Ubuntu and get a product to market is taking all of my time.

---

### Post by Chronon on 2010-11-03
Okay.  

May I suggest that the problem may not be Ubuntu per se.  Maybe your video card is not well supported or some other peculiarity of your setup.  I stream video just fine on both my desktop and my netbook.  I am currently running 10.10 on both but my desktop has run each release since Hardy (8.04) without any pronounced problems with streaming media.

At the very least, it doesn't seem like it's a simple case of 9.10=bad, 8.04=good.

---

### Post by Tiddens on 2010-11-19
Thanks, but our system worked just fine with 9.10 in the last two years, up until a couple months ago.  It is based on a netbook motherboard with an Intel Atom processor.  We tried back-ups from different periods in the past, but all started exhibiting the problem when they were upgraded.
 
Booting up for the first time in 2 weeks, I just did a system upgrade and now the streaming is even worse:  It still glitches every 2 minutes, but now often glitches so bad that it goes back to the beginning of the video (Hulu), and sometimes goes to pause mode.  
 
We have spent thousands of dollars on developing our product with Ubuntu, and it looks like we have no choice but to move to Windows.  I will however, boot up and update our Ubuntu versions once and a while to see if this is ever fixed...

---

### Post by Tiddens on 2010-11-19
Two side questions:
1.  Is there a way to get this forum to send me an e-mail notice when someone replies?
2.  It seems to me that there should be some special/corporate service/membership/priority for companies like ours that are trying to develop products with Ubuntu...

---

### Post by Chronon on 2010-11-19
1. Yes.  As with most forums you can set this in your user settings in your profile.
2. [http://www.canonical.com/enterprise-services/ubuntu-advantage/support](http://www.canonical.com/enterprise-services/ubuntu-advantage/support)

---

### Post by VcDeveloper on 2010-11-20
> **Chronon said:**
> Is there an open bug report you can point us to?  I haven't experienced anything like you are describing.

About to begin setting up my 10.10 for live streaming and wanted to know how you began setting up your server.  Did you follow the prep & install direction as the Sticky: [B]Comprehensive Multimedia & Video Howt?

[/B]...And is there anything else you can recommend?

---

### Post by Tiddens on 2010-11-24
Thanks Chronon! I figured out how to subscribe to threads (it's at the top of the thread pages, not in the profile).
 
I will pursue the Ubuntu Advantage business support per the link you sent. In addition to the nominal fee, we would be will to pay hourly. We would like to send a Wave unit to an Ubuntu expert and/or Adobe Flash person for reference, evaluation, and optimization. It's based on a typical Atom netbook motherboard.  For more info on The Wave, see [www.CatchTheWaveTV.com]("http://www.CatchTheWaveTV.com") .  We have done this with Scott Davilla for the Broadcom video acceleration daughter board and XMBC, and he has been great!
 
Some news: We have found (as might be expected) that the problem Ubuntu update is the "flashplugin-installer". If we install it, it causes video streaming in Firefox to freeze, pause, & go blank every 2 minutes (and sometimes kicks the video onto pause or to the beginning).

---

### Post by sofasurfer on 2010-11-24
Streaming video is awesome on 10.04. I have graduated from watching tv to watching pc. 
Now that I have done my part to support Ubuntu please take a trip to my latest thread and help me get my sound recorder going.

---

### Post by pinak.nubs on 2010-11-24
I am not sure if my issue is on similar lines or not. But I have issue with streaming video on my ubuntu 10.10.
I am new to Ubuntu itself and enjoying it. However, I am having issues with streaming videos online. 
youtube, NDTV news channel, etc play fine as long as the video is being played in regular size.  But when I maximise the video to full screen it freezes. Interestingly the sound doesn't stop  same video works fine with windows vista. can anyone help?

---

### Post by sofasurfer on 2010-11-24
I have had that problem although it has not reared its ugly head in some time. I suspect it is either an inadequete video card or more likely a slow processor or a memory issue. More work must be done faster to run on a full screen than a half screen. I'd like to know for sure also but I don't want to bring it up for fear of jinxing myself.

---

### Post by pinak.nubs on 2010-11-24
I am using Dell Inspiron 1525.
Intel core 2 duo 2.0 ghz, 2 gb ram. 
I doubt if its a slow processor or a memory issue as it works fine with windows vista.

---

### Post by no2498 on 2010-11-25
buy ubuntu and its drivers 
or tell the manufactures that make the cards you need help
this is free they the manufactures do not support linux/ubuntu 
or write your own fix 
we all need help at times
buy a card ubuntu supports $100.00
or go back to windows $150.00
plus the anti virus program $50/100
and the program to do your videos 

ok off the soap box

---

