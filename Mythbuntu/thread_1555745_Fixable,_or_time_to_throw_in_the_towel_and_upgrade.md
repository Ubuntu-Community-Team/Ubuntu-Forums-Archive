---
title: "Fixable, or time to throw in the towel and upgrade the hardware?"
date: 2010-08-18
forum: Mythbuntu
---

### Post by Weidbrewer on 2010-08-18
I've been migrating my machines to 10.04, and I just upgraded the frontend I use on the living room TV.  Please don't laugh at the hardware:

766Mhz Intel
524MB RAM
ATI Radeon 9200
40GB HDD
Standard 3COM ethernet card

I've been using it for a couple of years, and playback of stuff streamed from my Master Backend has been just fine.  FFW/RW, not so much - but I don't need those much.

Now that I moved to the latest version of Mythbuntu (and MythTV, by extention), it isn't really working.  The menu screen of MythTV is not very clear - best way to describe it is that the colors look like old-school 24-color videogame graphics.  The desktop and such are not like this, and videos play normally.

Also, when I tested on a regular monitor, I was able to navigate menus and play a stored video.  When I moved it down and hooked it up to the TV, it froze loading the Videos menu.


Do the above sound like just factors of the out-dated equipment, or some kind of software issue?  Thanks in advance!

---

### Post by LowSky on 2010-08-18
Well its kinda both. The graphic card is not really supported anymore and the newest version of MythTV is trying to use more graphically pleasing options.

You are only using this for a frontend so it being a bit light is not that bad. But if you want to watch or record High Definition you will need to upgrade.

---

### Post by Weidbrewer on 2010-08-18
Thank you for the response.  I suppose I should be a bit more specific:  I know that the hardware can be light - as stated, I've been using this frontend for a couple of years - what I am looking for is if there is a software fix for it not being able to display the Myth menu and why it might be locking up on it.

If the only answer is "because the gfx card is not longer supported,"  then that's that, I guess.  Given that it's an AGP card, it's not work trying to upgrade that - it would probably be easier and not much more expensive to just upgrade the whole system.

On the other hand, if there is some setting that I don't know about that isn't on by default, or some plugin I can download that's not in the install, then that would be awesome.

The system is currently *exactly* what is installed by default on the disk, plus all updates.  I haven't changed any other setting on the system thus far.  Just install, update, test.  Therefore, I'm a pretty blank slate trouble-shooting wise.

---

### Post by LowSky on 2010-08-18
the only thing i can think of is to go into appearance option under the front end and make sure pen gl isnt used and see if that helps. like you said the desktop look fine when not using mythtv so that might help.

---

### Post by Weidbrewer on 2010-08-18
That actually makes perfect sense, and something I wouldn't have thought of.

Funny thing is, I had another issue recently on another computer in regards to a legacy game not working.  The fix?  Make sure Open GL *is* turned on.  :D

I'll give that a whack when I get home.  I'd very much like to continue using this frontend.

---

### Post by tgalati4 on 2010-08-18
Or, you could create an /etc/X11/xorg.conf file with the correct settings for your ATI Radeon 9200 card.  If it worked previously, then it should continue to work, however you will need to give it some help.  Search the forums for appropriate xorg settings for your card.  You can start with:

gtf 1600 1200 60

Choose values that match your display.

---

### Post by Weidbrewer on 2010-08-18
Now, there's an idea that might work as well...are those files effected by OS version?  If not, I was smart enough to dual boot this machine, so my xorg file should still be on the other partition.  If I can just copy it over...


EDIT:  Also, during setup, I selected the generic driver, as on 8.04 the ATI driver caused problems.  Not sure if I should give that a try again as well.

---

### Post by newlinux on 2010-08-18
Just a shot in the dark, but you could also try a few different mythtv themes and see if one works better.

---

### Post by Weidbrewer on 2010-08-18
...and once again, newlinux finds one of my dumb-*** question threads.:D

It's a good thought, and the first thing I tried.  Same for all of them.

Well..by "all," I mean the, what, 5 themes the new version has (all widescreen...)?  But, alas, that's a gripe for another time.

---

### Post by LowSky on 2010-08-18
> **Weidbrewer said:**
> Well..by "all," I mean the, what, 5 themes the new version has (all widescreen...)?  But, alas, that's a gripe for another time.

The world has moved on to High Definition, those not there yet are going to feel the pinch.

---

### Post by Weidbrewer on 2010-08-18
Well, we'll see how it looks on my TV once I get it set up there.  Old version, I actually still used a standard format, as the widescreen ones didn't look very good on it (and yes, it is a wide screen, plasma TV.)  As for right now, I wouldn't mind a non-WS theme for the computers that are used in the rest of the house.  Everything is all crammed into that real estate.

Wow...I think I managed to thread-jack myself.

---

