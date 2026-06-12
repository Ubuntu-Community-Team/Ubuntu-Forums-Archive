---
title: "For everybody having trouble with flash being slow..."
date: 2010-02-28
forum: Multimedia Software
---

### Post by Nerdon on 2010-02-28
Switch to Opera. I had some saved .swfs that ran very choppy on firefox. I switched to opera and the change was unbelievable. The sound syncs perfectly, and there is no lag. And this is on an Aspire One! I dunno how good streaming is, but I would guess it is also improved.

---

### Post by n0dix on 2010-02-28
Good for you ;)
Are you trying with Google-chrome?

---

### Post by lidex on 2010-03-01
> **Nerdon said:**
> Switch to Opera. I had some saved [COLOR="Red"].swfs[/COLOR] that ran very choppy on firefox. I switched to opera and the change was unbelievable. The sound syncs perfectly, and there is no lag. And this is on an Aspire One! I dunno how good streaming is, but I would guess it is also improved.

swf or flv?

---

### Post by johnjohn2 on 2010-03-01
Would make a very welcomed change from firefox and the inability to play anything without being dog slow!

---

### Post by pjizz on 2010-03-01
I tried to watch this video 

[http://www.goducks.com/mediaPortal/player.dbml?&db_oem_id=500&id=693134&DB_MENU_ID=&SPSID=94831&SPID=11401&DB_OEM_ID=500](http://www.goducks.com/mediaPortal/player.dbml?&db_oem_id=500&id=693134&DB_MENU_ID=&SPSID=94831&SPID=11401&DB_OEM_ID=500)

in Chrome on Ubuntu ...very choppy, video lagged audio by a lot.  booted up into Win7 and watched same video in chrome no problems.

any suggestions?

---

### Post by rifter on 2010-03-02
> **pjizz said:**
> I tried to watch this video 

[http://www.goducks.com/mediaPortal/player.dbml?&db_oem_id=500&id=693134&DB_MENU_ID=&SPSID=94831&SPID=11401&DB_OEM_ID=500](http://www.goducks.com/mediaPortal/player.dbml?&db_oem_id=500&id=693134&DB_MENU_ID=&SPSID=94831&SPID=11401&DB_OEM_ID=500)

in Chrome on Ubuntu ...very choppy, video lagged audio by a lot.  booted up into Win7 and watched same video in chrome no problems.

any suggestions?


I think you might have better luck with Opera, as the OP suggests.  However, that site is pretty intense for my computer; even in Opera it was choppy for me, and I tried to make sure it had all the resources I could give it.

HOWEVER ...

Thank you for this thread, because switching to Opera fixed numerous issues I was having with flash playing sites.  The instructions for installing Opera on Ubuntu are _[color=blue][here](https://help.ubuntu.com/community/OperaBrowser)[/color]_.  Please note that in Karmic (Ubuntu 9.10) the "canonical" repository seems no longer to provide Opera. You'll have to use the Opera repository:

```

deb http://deb.opera.com/opera/ stable non-free

```

The instructions are _[color=blue][on that site I linked above](https://help.ubuntu.com/community/OperaBrowser)[/color]_, both for adding that repository and for installing Opera.

I got some great performance from Opera.

For instance on Hulu, this is what Opera did for me:

[list]
[*] I can now watch shows full-screen in HD **smoothly**.  I could do that in windows on this computer before with chrome, and now I can do it in linux, even with seti@home and a bunch of applications running.  This is huge.  Under firefox or chrome in Ubuntu 9.10, the same computer could barely show windowed normal res hulu with only one browser running and minimal cpu utilization by anything else ... seti@home was right out, and there were still choppy bits.
[*] I can now switch from full screen to small screen without losing the controls.  This is also huge because sometimes I get an im or an alert I need to handle and I need to be able to pause and check them out.  Using firefox or chrome, if I switched to windowed mode from fullscreen the video would blank out.  If I had not paused it before switching, the sound would keep going but the video was blank.  And there were no controls.  Guess what that means?  Yep I had to reload every time, which re-ups the commercials.  Very annoying, and now it is fixed!
[*] Switching from full screen to windowed is fast and smooth.  Under Firefox and Chrome it was not only choppy, not only slow, but it was a risky proposition that might not always work.
[*] The mouse doesn't mess up the video anymore.  Granted, the mouse pointer should hide in fullscreen and doesn't with any browser, but even if it hid it would come back when you moved it (which you'd want, because you moved it to do something).  When I moved the mouse **at all** in Chrome or Firefox, it cause an immediate pause and cascade of dropped frames, a significant increase in cpu usage, and for a good long while after the video would continue to be very choppy as the thing adjusted itself.  Pausing sometimes helped, at least in that you could wait out this period with the video paused, but because things were so unresponsive it took awhile to get the pause button to work.  Installed Opera, boom, done, this is no longer a problem.
[*] GUI responsiveness has increased tremendously (I'm talking about the flash video player's gui).  On Firefox and Chrome, this is a serious issue. There's a big lag in response from buttons, and it's iffy whether they respond at all. That means you click, then wait a good while, then if it doesn't work, click again, only to find tat it finally responded to your first click, and is going to undo that in a few more seconds since you clicked again.  Very annoying, and not a problem at all with Opera.
[/list]

In Facebook, unfortunately, I am having some problems with the flash games.  They load faster than on chrome or firefox, but I am having them freeze up.  I am having much better luck on that, thanks to _[color=blue][this post](http://www.linuxforums.org/forum/gaming-games-multimedia-entertainment/154331-solved-facebook-flash-games-linux-anybody-had-good-performance.html)[/color]_, with _[color=blue][Midori](http://www.twotoasts.de/index.php?/pages/midori_summary.html)[/color]_, which you can install from the _[color=blue][Universe](https://help.ubuntu.com/community/Repositories/Ubuntu)[/color]_ repository:

```

sudo apt-get install midori

```

Universe is enabled by default in Karmic (9.10), so you should be able to just install it without messing with repositories.

Midori provided all the benefits that Opera did for me with Hulu; it actually seemed to be even faster.

Midori not only made the Facebook games faster, but it fixed some bugs I was having in one of them (Zynga Poker) under Linux.  Unfortunately it did not squash all of them.  I have been playing that particular game with firefox under wine for awhile, which fixes most of the issues.  I will continue to look for a solution there.

Unfortunately, Midori did not properly load the goducks sports page you referenced, and midori under wine crashed when trying to use flash pages of any kind.  Midori is not even in the wine appdb as far as I can tell, so I have no guidance on that.

Because the same computer with the same browser was not able to do the same things, I thought it was the fault of Adobe's Linux port of flash.  It may still have problems (at least you can do fullscreen video again -- I hated when they broke that), but it looks like in Opera functionality is good enough that I am wondering if the problem is more in the implementation of firefox and chrome on Linux.  Or maybe it's just firefox and chrome being what they are, because on windows and linux both those browsers have a tendency to start eating all the cpu on the system, especially if you dare to have a page open somewhere that uses flash or java (even if it's not really doing anything).



There is one further solution that those of you with flash woes might look into.  HTML5 is replacing flash on some sites, and it's wicked smooth, fast an lean.  Check out _[color=blue][the html5 version of youtube](http://www.youtube.com/html5)[/color]_ to see what I am talking about.

---

### Post by tilixibr on 2010-03-22
I dont know why, but I installed a Kubuntu session along with my GNOME session, and flash runs better on KDE:???:
Does anyone have any idea why?
~EDIT

I used firefox, and Flash still has those flashy moments, but it doesn't slow down as much
~

---

