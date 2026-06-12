---
title: "MPlayer hangs when trying to play a DVD."
date: 2007-05-19
forum: Multimedia &amp; Video
---

### Post by nick1 on 2007-05-19
Greetings,

First, some background information...

_System Specs:_
-Dell Latitude D820
-Intel Core 2 Duo
-Ubuntu 6.06 LTS Dapper Drake
-Kernel version 2.6.15-28-686
-MPlayer version 2:0.99+1.0pre7try2+cvs20060117-0ubuntu8


_How I installed MPlayer:_
1.) I added the following two lines to /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper universe multiverse

2.) I then installed MPlayer through Synaptic using the search term "mplayer".


_What I'm trying to do:_
I am trying to play an official copy of The Lady Killers DVD in MPlayer.
The process I am using to try to play the DVD is...

1.) Insert DVD
2.) Totem auto-starts and complains it can't read the DVD
3.) I close Totem and then start MPlayer (Applications > sound & video > MPlayer Movie Player)
4.) I then right-click on the MPlayer Video window and select DVD > Open Disc
I have also tried: Open > Play DVD
5.) MPlayer freezes and cannot be closed

Before I go switching to another video application, I would like to figure out why
MPlayer is crashing when I try to play a DVD.
This is a legit, readable DVD which I have played many times in the past on other operating systems.

Please let me know if I should provide anymore information to aid in troubleshooting this problem.

Thank you for your time,

---

### Post by taurus on 2007-05-19
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by nick1 on 2007-05-20
I followed the information located at the above article and I can now play my DVD in MPlayer.
I already had the libdvdread3 package installed however I did not have libdvdcss2 installed.
After installing the libdvdcss2 package, MPlayer played my DVD.

I could see this portion of Ubuntu being a big frustration for someone who is using Ubuntu for the very first time.  Hopefully this functionality will become standard in Ubuntu.

Now I need to figure out why the sound seems low even when the volume is all the way up.

Thank you for your help,

---

### Post by andrew.46 on 2007-05-20
Hi,

 As a fellow Dapper user I read your post with great interest:

> **nick1 said:**
> I followed the information located at the above article and I can now play my DVD in MPlayer.
I already had the libdvdread3 package installed however I did not have libdvdcss2 installed.
After installing the libdvdcss2 package, MPlayer played my DVD.

I could see this portion of Ubuntu being a big frustration for someone who is using Ubuntu for the very first time.  Hopefully this functionality will become standard in Ubuntu.

Now I need to figure out why the sound seems low even when the volume is all the way up.

Thank you for your help,

 I could not agree more with your sentiments about the multiple steps involved in playing DVDs. I believe that while these steps are perhaps not all that complex they really should not be required in a modern OS, many disagree with this idea though!!

 I had the same odd problem with sound and Mplayer/DVDs and could not solve it. However I then installed Gxine and this both played DVDs better as well as having decent volume. Have not tried VLC which is supposed to be better than both.

                Andrew

---

### Post by nick1 on 2007-05-20
Hi Andrew,

> I believe that while these steps are perhaps not all that complex they really should not be required in a modern OS

I agree.  Although it didn't take me long to install the necessary software to play my DVD, most users probably aren't as patient or tech savy as us.  These are the type of people that just want things to work, and sometimes I fall into that category.

As for other multimedia players, as I write this I've installed and played around with the following players:

-MPlayer: have yet to find a fix for the low volume issue. I don't like how it bypasses the DVD menu options and goes straight into the movie itself.  I'm not sure if this is configurable. I like how MPlayer auto-fits the movie to my screen.

-Xine: DVD volume is louder then when using MPlayer.  However I don't like how Xine does not auto-fit the movie to my screen.

-VLC: In order to play a DVD, I need to manually enter the device name.  An end user isn't going to know what this means.

-Songbird: very nice GUI.  I don't think it plays DVD's yet.

*sigh*  Right now I'm pretty frustrated and wish I could settle on a single multimedia player.
The troubleshooting continues...

---

### Post by andrew.46 on 2007-05-21
Hi Nick,

 You appear to have done a lot of experimentation on this issue!! Have you also tried totem-xine? The default Dapper Totem Movie Player uses Gstreamer but a version using Xine can be installed. My apologies if you already are aware of this / have already experimented with this :) 

              Andrew

---

