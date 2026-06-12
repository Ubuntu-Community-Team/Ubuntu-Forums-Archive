---
title: "No DVD playback + no realplayer = frustration"
date: 2007-11-07
forum: Multimedia &amp; Video
---

### Post by Talon2 on 2007-11-07
I´ve been running Ubuntu since Dapper.  I appreciate the work and try to support the community.  There are many good things going on here.  However, there are two areas of Ubuntu that have caused me untold amounts of frustration:

- DVD playback.  I have, at times, been able to get DVD playback working poorly on a couple of systems.  With the advent of Gutsy DVD playback is dead, a total no-go.  I´ve hunted down and tried guides, advice and guesswork.  This is truly insane.  I´d like to convince my employer to give Ubuntu a trial run but we must have rock solid DVD playback.  

- Real player.  My wife´s system still runs Win2000 to this day because I cannot get decent performance for playing real player streams.  Before anyone suggests going to alternatives I must point out that real player format is the only format supported by the radio station my wife listens to.  This is her link to the country she grew up in.  No real player format support = no Ubuntu.  Once again, I have tried all guides and tips I could find over the last 2 years.  Nothing has led to acceptable performance.

The performance of the above with windows on the same computers gives outstanding performance.

My concern is not using free software.  I don´t care if I have to pay.  All that matters is whether these capabilities work and work well.

---

### Post by trak87 on 2007-11-07
These may be helpful for both of your questions:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Realplayer formats are generally loathed across the Internet, but there are discussions about getting it working in Gutsy. Just do a search.

You can also use mplayer to play real formats:

```
mplayer -playlist http://www.url.ram
```

You can also install smplayer which is a graphical interface for mplayer. You could then instruct your system to send all .ram files to smplayer.

Just remember, if you install the right codecs mplayer can play virtually anything. And there are more possibilities for codec installation than just the Ubuntu repositories. For example,

[http://www3.mplayerhq.hu/MPlayer/releases/codecs/](http://www3.mplayerhq.hu/MPlayer/releases/codecs/)

and grab the file all-20071007.tar.bz2 

It's a collection of codecs that mplayer will utilize. Unpack the contents to /usr/lib/win32 and you'll be able to play virtually anything.

---

### Post by Talon2 on 2007-11-08
> **trak87 said:**
> These may be helpful for both of your questions:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)


Thanks for the suggestions but I´ve been there, done those.

> 
Realplayer formats are generally loathed across the Internet, but there are discussions about getting it working in Gutsy. Just do a search.


Wife doesn´t care what is loathed.  What works is all that matters.  Windows works, Ubuntu doesn´t.

I have searched.  There are problems to one degree or another with all solutions.  My message was more of a rant than a plea for help.  

Thanks for the reply.  Hopefully someday the situation will improve.  

Cheers.

---

### Post by drakazz on 2007-11-08
Are you sure? [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

How about [http://en.wikipedia.org/wiki/Helix_project](http://en.wikipedia.org/wiki/Helix_project) ?

---

### Post by Talon2 on 2007-11-08
> **drakazz said:**
> Are you sure? [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

How about [http://en.wikipedia.org/wiki/Helix_project](http://en.wikipedia.org/wiki/Helix_project) ?

I´ll go ahead and do a fresh install of Gusty then follow the advice on these two sites while keeping a log.  I&#314;l post the report here when finished.

---

### Post by voided3 on 2007-11-11
As for the DVD playback, mplayer should work after installing "libdvdcss2" in the synaptic package manager or by looking in "add/remove programs" by searching for "dvd" (should be something mentioning restricted codecs and plugins). And there is a version of RealPlayer for Linux; get it here:

[http://www.real.com/linux](http://www.real.com/linux)

Just download it to your desktop, then right click on it and go to permissions and make it executable. Then open the terminal and enter this:

cd ~/Desktop
sudo ./RealPlayer10GOLD.bin

When it asks you where you want it installed, just put it where ever you want it (I put it in "/home/(username)/RealPlayer" ) You also can install the real media codecs for other media players, too, as mentioned. Good luck!

---

### Post by DaleFarrell on 2007-11-28
Voided3, I thank you. Changing the permissions on the downloaded .bin was missing from the other help posts. Dale, in Seattle.

---

### Post by mdpalow on 2007-11-28
I see a lot of people having problems with this. I think somewhere in the translation, something is going wrong during the installation of required dvd/codecs files.

Assuming there is no other problem, this is typically the one and only area that needs to be addressed to get DVDs to play.

I wrote a script that I use during a fresh install to help me get up and running very quickly. One of the options in the script is to install the proper dvd / codecs files. It's option 15. People have used it before and it seems to do the trick for them as well..

You can find the script by clicking link below in my signature...

---

