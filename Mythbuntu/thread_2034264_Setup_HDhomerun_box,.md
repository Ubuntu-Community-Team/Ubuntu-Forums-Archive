---
title: "Setup HDhomerun box,"
date: 2012-07-27
forum: Mythbuntu
---

### Post by valem on 2012-07-27
I tried and tried to start a new post but I give up.

I put together this machine with Z77 mobo i7-2600 etc. and decided I would only run Linux.
So far so good.
Then I bought this HDhomerun box, which is supposed to be linux friendly running with mythtv.
After going through 40 minutes of setup tutorials on youtube and an hour of channel scanning for the FIFTH TIME THIS WEEK I nearly destroyed my desk, and keyboard with furious punches.

I can't see any channel, nothing either I get a black screen, or an error of some sort, but nothing is consistent.
I like challenges and I enjoy troubleshooting but this is getting retarded.
Just for comparison, with a laptop running windows xp, I could watch all TV channels via VLC player nearly instantly.  I am going insane here.
I can't figure out what is going on and I can't understand why the mythtv tutorial takes over 40 minutes and still I get no results.
I have never been through anything more frustrating than this setup!!!!

---

### Post by howefield on 2012-07-28
Post moved to its own thread.

---

### Post by valem on 2012-07-28
How do I start a new thread? I need to start one about L2TP Ipsec VPN locking up my machine every time I attempt a VPN connection.

Anyway, my main concern here is HDhomerun and mythtv.
I think it has to be a codec issue of some sort, because with neither myth live TV or VLC I can see anything.
However with mythbrowser I am able to record and then watch it in movie player.
The first time I installed mythtv I was able to watch live tv, but then somehow something changed and as I flip through the channels all I see is a blank screen.
Any thoughts on what I should try?
TIA

---

### Post by valem on 2012-07-28
Well, I just tried to change the video source HDHR Channel frequency table from us-cable to try-all and now I can watch live TV again.
Apparently that was it?
I hope so :-)

---

### Post by valem on 2012-07-29
Well, that wasn't it. Didn't change a thing and today I get a black screen. Still set to try-all but today it does not work. Nice.
I'm talking to myself here, great!

---

### Post by ijumpship on 2012-07-31
Ok let me chime in here.

First test to see if your hD is seen by myth.The easiest way to me is to use the HD HomeRun Gui (Application-->multimedia-->homerun config gui) this is similar to the one found in windows.

Then do the same scan for channel as you would in windows

Then go to your Backend (system--->backend setup) and do steps 2,3,4 5(optional) chose finished on each change.
when you exit (the system will ask to fill the database) chose yes then enter your password and save the settings

I found that when these settings are not saved in the database the front-end behaves erratic.

consider this though
1.Make sure your backend and the turner are on the same network segment
2.Make sure you scan for the channels.

Let us know the version of mythtv and ubuntu you are using 
 
Home you are on track

---

### Post by valem on 2012-08-02
Thanks for the advice [@ijumpship]("http://ubuntuforums.org/member.php?u=1227697").
What has been frustrating has been the lack of consistency, sometimes it worked and sometimes it didn't.
What I actually found out was that the HD HomeRun Gui was keeping the  tuner busy (or so I think) and the mythtv backend could not use the  tuner and would just give me a blank screen.
Even if I closed or xkill the HD HomeRun Gui would still somehow keep the tuner lights on.

So I removed the HD HomeRun Gui package and I'm able to watch the live channels.

However, when I first start mythtv backend it doesn't work unless I run the mythtv-setup first.
What I have to do every time is enter mythtv-setup and exit  mythtv-setup, fill the database, then I can start mythtv backend and  watch live TV.

Would you happen to know why I have to do that?
Thanks again!

---

### Post by lisati on 2012-08-02
> **valem said:**
> How do I start a new thread? 

Take a look here: [http://ubuntuforums.org/showthread.php?t=2026724](http://ubuntuforums.org/showthread.php?t=2026724)

---

### Post by ijumpship on 2012-08-02
> **valem said:**
> Thanks for the advice [@ijumpship]("http://ubuntuforums.org/member.php?u=1227697").

However, when I first start mythtv backend it doesn't work unless I run the mythtv-setup first.

Thanks again!

Mythtv 0.25 required you to set up a turner,If you do not have one then you are required to setup a dummy turner

> **valem said:**
> Thanks for the advice [@ijumpship]("http://ubuntuforums.org/member.php?u=1227697").

What I have to do every time is enter mythtv-setup and exit  mythtv-setup, fill the database, then I can start mythtv backend and  watch live TV.

Would you happen to know why I have to do that?
Thanks again!
my only thought on this is to make sure you go to MCC chose Mysql and enable internet interface for remote frontend and backend

---

