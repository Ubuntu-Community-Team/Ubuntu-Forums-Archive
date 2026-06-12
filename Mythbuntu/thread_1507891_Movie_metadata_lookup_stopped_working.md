---
title: "Movie metadata lookup stopped working"
date: 2010-06-12
forum: Mythbuntu
---

### Post by NautiusMaximus on 2010-06-12
I had my system nicely set up so that I could download metadata for my videos by selecting "download metadata" from the information menu for a video.

Today, it didn't work. I checked that the computer is connected to the internet and that the movie (The Sting) exists in TMDB.

Here is the relevant extract from the frontend log:


```
2010-06-12 11:49:46.102 Video Search: Executing "'/usr/share/mythtv/mythvideo/scripts/tmdb.pl' -M tv=no;video=no The Sting"
2010-06-12 11:49:46.721 Unable to contact themoviedb.org while retrieving movie list, stopped at /usr/share/mythtv/mythvideo/scripts/tmdb.pl line 329.

2010-06-12 11:49:46.727 GetVideoList returned 0 possible matches

```

Any idea what could be going wrong here?

I'm using Mythbuntu 9.10.

Thanks
NM

---

### Post by radfae on 2010-06-12
Hi, I'm using debian and I get the same error when trying to retrieve metadata.

I dug through the tmdb.pl script (not sure if mythbuntu uses the same script) and found the following URL:

[http://api.themoviedb.org/2.0](http://api.themoviedb.org/2.0)

That url no longer exists.

If you go to [http://api.themoviedb.org/](http://api.themoviedb.org/) it will redirect you to:
[http://api.themoviedb.org/2.1](http://api.themoviedb.org/2.1)

Unfortunately correcting the script to use 2.1 doesn't seem to fix the problem and I'm still stuck.  I'm hoping someone else will know how to fix this.

---

### Post by sakus on 2010-06-12
Ran into this same problem today on my Gentoo.. seems it's due to a too old version of MythTV / MythVideo - I'm upgrading to 0.23 as I'm typing this.

The script that stopped working (guessing themoviedb.org just pulled the cord on the older version API now after supporting it together with the newer one for a while) has been replaced with another one anyway, here's a snippet from 0.23 MythTV release notes:

> Add a new grabber script for version 2.1 of the TMDB API, tmdb.py
( [http://www.mythtv.org/wiki/Release_Notes_-_0.23](http://www.mythtv.org/wiki/Release_Notes_-_0.23) )

So.. update :)

edit
Upgraded to 0.23, and everything's working fine including the meta data grabbing.

---

### Post by usererror on 2010-06-12
How exactly do I Upgrade to .23?  I used SVN to download the .23 folders, but not sure what to do with it now.

What's the proper way to update to .23?  I don't see in Apt software updates. I'm running an install of Mythbuntu 9.10 with one Backend/Frontend combo box and then a seperate FE.  Thanks!!

EDIT:  After more googling, I found this page: [http://www.hackourlives.com/upgrade-mythtv-0-22-to-0-23-on-ubuntu-9-10/](http://www.hackourlives.com/upgrade-mythtv-0-22-to-0-23-on-ubuntu-9-10/)  there are repo's that you need to add to apt.  I'm using Mythbuntu so I went to [http://www.mythbuntu.org/](http://www.mythbuntu.org/) then clicked Download and the activate auto builds:

[http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds), then click Activate Auto Builds, then download the .deb package.  Reload your apt-get list, and then apply the changes.  Mine is downloading right now.

Applied the updates, then have to upgrade the database.

And then video look ups work again!

Note: If you have an ATI video card using FGLRX, make sure you do not update the kernel image, or else it'll break your video output.  I forgot this lil' tidbit. again.  ](*,)

---

### Post by SnafuFlux on 2010-06-14
TMDB's 2.0 api is currently down.  Travis is working on it.

[http://twitter.com/themoviedb](http://twitter.com/themoviedb)

[http://forums.themoviedb.org/topic/1180/20-and-21-apis-not-returning-any-results/](http://forums.themoviedb.org/topic/1180/20-and-21-apis-not-returning-any-results/)

---

### Post by nickrout on 2010-06-14
> **SnafuFlux said:**
> TMDB's 2.0 api is currently down.  Travis is working on it.

[http://twitter.com/themoviedb](http://twitter.com/themoviedb)

[http://forums.themoviedb.org/topic/1180/20-and-21-apis-not-returning-any-results/](http://forums.themoviedb.org/topic/1180/20-and-21-apis-not-returning-any-results/)

If you don't want to move to 0.23 there is a patch posted to the mailing list which will fix this in 0.22.

---

### Post by SnafuFlux on 2010-06-15
I'm to afraid to apply patches.  things tend to break on me hah.

---

### Post by nickrout on 2010-06-15
It only changes one file, the metadata grabber and it won't work without the patch so how broke can you make it?

---

### Post by usererror on 2010-06-15
> **SnafuFlux said:**
> I'm to afraid to apply patches.  things tend to break on me hah.

So I'm not the only one with a healthy fear of applying patches on a mythbuntu installation, ONCE you have everything running smoothly! :p

---

### Post by nickrout on 2010-06-15
> **usererror said:**
> So I'm not the only one with a healthy fear of applying patches on a mythbuntu installation, ONCE you have everything running smoothly! :p

Well it's simple. If you want the grabber to work apply the patch or upgrade to 0.23.

---

### Post by SnafuFlux on 2010-07-08
the gf has gone away for 2 weeks, so I upgraded instead.  but now I'm having issues with 10.04's version.  the tvdb lookup works fine.  the text scraping for the movies are working, but the images are not.

can anyone confirm that it's working for them currently?  obv I'm now using the new API version.  I like the fact that I can finally use the parental restrictions.

---

### Post by mdaitc on 2010-07-08
there's a bug  that just got fixed to solve this problem with downloading new images.

[http://svn.mythtv.org/trac/ticket/8634](http://svn.mythtv.org/trac/ticket/8634)

build 25299 or later will have this fix in (at time of writing,  mythbuntu were 25298 )...

---

### Post by SnafuFlux on 2010-07-08
thanks, sorry for the cross posting.  any idea when it'll happen?

---

### Post by mdaitc on 2010-07-08
i don't have a firm time (i'm not one of the developers) , but: it looks like builds happen typically once a day ( [https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=built]("https://launchpad.net/%7Emythbuntu/+archive/0.24/+builds?build_state=built") ) or are pushed as needed by the developers.

so i'd have thought worst case 24 hours (since some have just been built). Best case, a developer reads this, and pushes a new build, so an hour or so.

[https://launchpad.net/~mythbuntu/+archive/0.24/]("https://launchpad.net/%7Emythbuntu/+archive/0.24/") is also useful to watch for the status of the builds (dont be alarmed if sometimes stuff fails, that's the nature of development.)

---

### Post by SnafuFlux on 2010-07-08
excellent.  thanks for the information.  I just applied some more updates.  no real help as of yet.

I'll check again tomorrow.  Maybe I'll try and figure out how to work Jamu, in the mean time.  Have you tried/had luck with it?  I tried reading the wiki over at mythtv.org.  gotta say, not exactly user friendly.  difficult to follow.

---

### Post by SnafuFlux on 2010-07-08
I should note, I'm .23 not .24

---

### Post by nickrout on 2010-07-08
> **mdaitc said:**
> i don't have a firm time (i'm not one of the developers) , but: it looks like builds happen typically once a day ( [https://launchpad.net/~mythbuntu/+archive/0.24/+builds?build_state=built]("https://launchpad.net/%7Emythbuntu/+archive/0.24/+builds?build_state=built") ) or are pushed as needed by the developers.

so i'd have thought worst case 24 hours (since some have just been built). Best case, a developer reads this, and pushes a new build, so an hour or so.

[https://launchpad.net/~mythbuntu/+archive/0.24/]("https://launchpad.net/%7Emythbuntu/+archive/0.24/") is also useful to watch for the status of the builds (dont be alarmed if sometimes stuff fails, that's the nature of development.)

Are you sure you want to use trunk??

---

### Post by mdaitc on 2010-07-08
RE: jamu

i looked at it, and played with it a little, but it seems to me it's more for bulk operations - at the moment, i'm just needing to do individual lookups on tmdb.

i'd agree it's not too intuitive to use, and seems like it has the possibility of affecting more than just what you want.

---

### Post by mdaitc on 2010-07-08
re: the bug:

looking at  [http://svn.mythtv.org/trac/changeset/25287](http://svn.mythtv.org/trac/changeset/25287) 

it says "Metadata Classes: Add redirect support, don't know how I neglected to  add this in the first place, it was definitely on the list.  Refs [#8634]("http://svn.mythtv.org/trac/ticket/8634"),  and fixes it in trunk.  .23-fixes will need a different cure and while I  haven't looked closely at the patch on the ticket, it doesn't feel  right."

so the bug is fixed in trunk for 0.24

it looks like .23-fixes will need another different fix however - looks like it was a bug introduced recently into both .23 and .24, and has been easier to fix in .24

---

### Post by SnafuFlux on 2010-07-08
damnit, that's two things busted for me!

there's a fix for DTS not working in the internal player, and now this. lol.

I like 10.04, but 9.10 was smoother for me.

thanks agian for your help.  I'm a programmer (web dev/windows) and I'm just learning what branching/trunks are.  sad, I know.

---

### Post by mdaitc on 2010-07-08
> **SnafuFlux said:**
> damnit, that's two things busted for me!

there's a fix for DTS not working in the internal player, and now this. lol.

I like 10.04, but 9.10 was smoother for me.

thanks agian for your help.  I'm a programmer (web dev/windows) and I'm just learning what branching/trunks are.  sad, I know.

it takes time for a package as big/complex as mythtv to be perfectly refined. I've got a couple of small bugs that affect me in 10.04 too - but i'm thinking they will get fixed sooner rather than later.

By learning to read the bug reports and the SVN commits in trunk, I can see when things get solved - and figure when it's worth upgrading. One can use trunk without upgrading every day...

Don't worry about not knowing all the  terminology - a willingness to learn and an open mind to new things ss really the major hurdle to overcome - once you're there, then it's really just a case of trying to catch up to what's been happening in development.

---

