---
title: "Metadata stopped grabbing coverart  - possible update issue"
date: 2010-09-20
forum: Mythbuntu
---

### Post by Weidbrewer on 2010-09-20
Hey, all.  I posted a question on the main Mythtv forums, but haven't been able to nail down a solution yet.  

I recently upgraded my system to Mythbuntu 10.04, and with it, the included new version Myth. I have been going through my library updating the metadata. I love the new grabber, however, it stopped pulling coverart and I'm not sure why. At first, I thought that there just might not be a file available for it, until I realized two things:

1.) It stopped all at once. By sheer law of averages, with hundreds of files, there would have to be one or two that would have coverart available.
2.) There was nothing available for pretty popular files, such as movies like Tron and Twelve Monkeys, and TV shows like Dexter, Burn Notice and Breaking Bad (there were some for BB, but it stopped pulling while going through this series.)

For the most part, it is still pulling running times, release year, actors, plot info, etc - just not the cover files or fan art any longer. A possible fix that was suggested was to "enable the -fixes packages," but the person did not know how to do this in Ubuntu.

Does anyone have any idea if this would solve my problem, and how I would go about doing it?  Also, is Myth not getting any updates when I don't have this option enabled?

Thanks in advance for the help, and more than likely, apologies to Newlinux for bothering him with another silly question.

---

### Post by pu15e on 2010-09-20
Yup - I can confirm that updating to -fixes will definitely solve that problem, as it did for our Myth network.

I would move to .23.1 when the update installer offers the choice, but ensure you update all networked Myth machines simultaneously.

Edit: Oops. Shouldn't answer questions before finishing first cup of tea - too many questions *fail* to get answered like that :p

You can move to -fixes by visiting [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) - click on Activate auto builds, then on the big Activate icon that appears. When asked by FireFox (which I'll obnoxiously presume you're using), say to open the file with Debi (a package manager) and the rest should be self-evident. Have an appropriate amount of fun :-)

Cheers,
 Mattt.

---

### Post by Weidbrewer on 2010-09-20
> **pu15e said:**
> Yup - I can confirm that updating to -fixes will definitely solve that problem, as it did for our Myth network.

I would move to .23.1 when the update installer offers the choice, but ensure you update all networked Myth machines simultaneously.

Edit: Oops. Shouldn't answer questions before finishing first cup of tea - too many questions *fail* to get answered like that :p

You can move to -fixes by visiting [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds) - click on Activate auto builds, then on the big Activate icon that appears. When asked by FireFox (which I'll obnoxiously presume you're using), say to open the file with Debi (a package manager) and the rest should be self-evident.

Thanks - install was as easy as you said, and it DL'd a crapload of updates...however, coverart is still not pulling in.  Any other ideas?

>  Have an appropriate amount of fun :-)

I shall attempt to control myself. :)

---

### Post by pu15e on 2010-09-20
Hhhmmm...

Are you highlighting the relevant movie files in myth and pressing w (or whatever you have zoom (i think it is) set to)? That's meant to (and, for us, does) auto-pull the metadata and display it, sometimes asking you to identify which of several possible matches you're looking for.

That definitely does it for us. Particularly on remote fe's, we do find it takes quite a few seconds for the artwork to show up...

Also, as a precaution, have you rebooted affected machines to ensure all latest code is running? We've found recently that the be's will bounce during update installs but fe's don't.

Cheers,
 Mattt.

---

### Post by Weidbrewer on 2010-09-20
Yep, rebooted and everything.  As stated in the original post, I'm able to pull in all info except the cover art (using your method.)  It just stopped pulling it in at one point.  Just for giggles, I also reset the  meta data on a few and grabbed it over again.  Once again, it just pulled in the text info, no pictures.

I have a knack for finding the weird ones.

---

### Post by pu15e on 2010-09-20
Hhhmm... Yup, that's weird. Only other thing I can think of that I haven't specifically asked yet is did you upgrade to the .23.1 branch (noting the .1)? I'm not sure, but perhaps the patch is only applied to that branch...

Cheers,
 Mattt.

---

### Post by Weidbrewer on 2010-09-20
Since the installer for the fixes only allowed for 23, I'm guessing not.  A.) how do I look up the version, and B.) if it is not, how do I upgrade it?

---

### Post by tgm4883 on 2010-09-20
> **Weidbrewer said:**
> Since the installer for the fixes only allowed for 23, I'm guessing not.  A.) how do I look up the version, and B.) if it is not, how do I upgrade it?

What version of mythbuntu-repos do you have installed?

---

### Post by Weidbrewer on 2010-09-20
Again, not sure how to tell.

Everything is installed straight from the Mythbuntu install cd, plus the -fixes mentioned above, patched up to current.

---

### Post by tgm4883 on 2010-09-20
Do this in a terminal and paste the output here

```
dpkg -l mythbuntu-repos

```

Then do this and tell me if 0.23.1 is listed

```
dpkg-reconfigure mythbuntu-repos
```

---

### Post by Weidbrewer on 2010-09-20
...aaaaaaand, I just realized I never did re-setup remote access on that machine.  I'll have to catch that up later tonight.  Thanks for the things to try.

---

### Post by Weidbrewer on 2010-09-20
> **tgm4883 said:**
> Do this in a terminal and paste the output here

```
dpkg -l mythbuntu-repos

```

Then do this and tell me if 0.23.1 is listed

```
dpkg-reconfigure mythbuntu-repos
```

1. ```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.2-0ubuntu0+m Mythbuntu repos installer

```

2. Did that, changed it to 23.1, installed updates, rebooted, did #1 and got the same results.  Cover art still not pulling.

---

### Post by tgm4883 on 2010-09-21
> **Weidbrewer said:**
> 1. ```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  mythbuntu-repo 8.2-0ubuntu0+m Mythbuntu repos installer

```

2. Did that, changed it to 23.1, installed updates, rebooted, did #1 and got the same results.  Cover art still not pulling.

Any errors in the frontend or backend logs when you try to pull data?

---

### Post by Weidbrewer on 2010-09-21
Can you guess what I'm gonna ask? ;)

...how?

---

### Post by tgm4883 on 2010-09-21
logs are at 

```
/var/log/mythtv/mythfrontend.log
/var/log/mythtv/mythbackend.log
```


You will need to grab the backend log from your master backend. Your frontend log from the same machine you are trying to get the movie images on

You can open a terminal and do 

```
tail -f /path/to/log 
```

and this will show the log in real time.

You could also just try to pull the movie image from the frontend then attach both logs in a post

---

### Post by Weidbrewer on 2010-09-21
Ah-ha...now we're on to something:

```
010-09-21 00:34:31.514 Video Data Query: Executing "'/usr/share/mythtv/mythvideo/scripts/Movie/tmdb.py' -l en -D 63"
2010-09-21 00:34:32.058 Copying 'http://hwcdn.themoviedb.org/posters/530/4bc9020d017a3c57fe000530/twelve-monkeys-original.jpg' -> 'myth://Coverart@192.168.1.2:6543/63_coverart.jpg'...
2010-09-21 00:34:32.079 Copying 'http://hwcdn.themoviedb.org/backdrops/504/4bc90208017a3c57fe000504/twelve-monkeys-original.jpg' -> 'myth://Fanart@192.168.1.2:6543/63_fanart.jpg'...
2010-09-21 00:34:32.703 Coverart download finished: Error writing image to file myth://Coverart@192.168.1.2:6543/63_coverart.jpg. 1
2010-09-21 00:34:33.073 Fanart download finished: **Error writing image to file myth://Fanart@192.168.1.2:6543/63_fanart.jpg. 1**

```

So, it's pulling it, but can't write.  Makes sense why I'm not getting cover art any longer, but not why it suddenly starting having problems.  Next step?


EDIT:  Never mind.  Figured it out.  Big duh.  Chmod'd the folders.  Not sure how they got locked, but that did it.


Thanks for all the help!

---

### Post by pu15e on 2010-09-21
We had the same error... On the pre-updated version...

Cheers,
 Mattt.

---

### Post by se99paj on 2013-02-18
I know this thread is a few years old but I'm having a similar issue and wanted to try and get some advice.

Basically I've just completed a fresh install using the latest Mythbuntu version. I've also migrated a lot of content from my old system, there are 600+ videos and I would like to add the metadata for each one.

The first time I tried I only managed to get about 30 cover arts, I then renamed the files so they were consistent and they were only the title of the video, this provided some significant improvements, but I'm still missing 500+ cover arts for movies that are fairly well known.

I've checked the logs and I can see the tmdb.py script pulling metadata, but only a small percentage seem to pull cover art. I've run the script manually for specific movies and I can see the cover art URL but it doesn't seem to get downloaded.

I'm assuming that permissions can't be an issue as it works for some and not for others. Are there any other logs that I could be looking at?

---

### Post by Weidbrewer on 2013-02-18
Sorry, no - I'm not sure what would be causing that.

To be honest, I scrapped the whole MythTV thing on my system a while back.  Too many issues like this left me trouble-shooting more than I was watching stuff.  I ended up switching to a Linux Plex Media Server on the backend, and a Roku connected to my TV.  I've had one update go screwy, but other than that, it's been completely hands off for about a year now.

---

### Post by tgm4883 on 2013-02-18
Closing thread due to necromancy. Please open a new thread instead of posting to one that is a few years old.

---

