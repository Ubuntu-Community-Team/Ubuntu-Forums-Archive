---
title: "Rhythmbox + ipod == crippled?"
date: 2010-01-17
forum: Multimedia Software
---

### Post by thockin on 2010-01-17
From what I can tell by fiddling and reading, Rhythmbox, the default Ubuntu media player is fundamentally crippled for use with ipods.  It doesn't support ipod smart playlists on the ipod itself.

Sure, you can create an "automatic playlist" on the ubuntu side, but how on earth does that transfer to the ipod?  As far as I (and google) can tell - it doesn't.  Which makes rhythmbox basically useless for ipods.

Can that be right?  What am I doing wrong?

And to add insult to injury, banshee doesn't work for ipods at all because of automounting media (that's two apps that are broken due to this - gThumb and banshee).

Why does Ubuntu bundle such AWFUL apps for the out-of-the-box experience?  I've spent pretty much ALL DAY trying to figure out how to get my music onto the ipod while retaining playlists (required for my car integration).

Clue me in?  Frustrated...

Tim

---

### Post by fancypiper on 2010-01-17
Have you tried exaile with exaile-plugin-ipod?

---

### Post by thockin on 2010-01-17
I did try Exaile, but like Rhythmbox, I have no idea how to manage playlists ON the ipod.  Where do I see them listed?  How do I edit them?  How do I make new ones?

It's like everyone and their brother thinks they can/should write a media player app, but nobody ever considers this aspect.

I'm about 10 minutes away from installing iTunes under wine.  I f'ing HATE iTunes, but the GNOME world seems incapable of accomplishing this most ordinary of tasks - manage my ipod.

Rhythmbox - can't do smart playlists on the ipod
Banshee - can't find my ipod
Exaile - where are those playlists?
gtkPod - can't find the ipod

Ubuntu should actually test some of this crap...

---

### Post by thockin on 2010-01-17
Please pardon my rant.  I just can't believe that in 2009, now 2010, it is still this hard (impossible) to manage an iPod.

Approximately 94% of computer users have one.  And Linux people wonder why "regular" folks don't use Linux.

---

### Post by kelvin spratt on 2010-01-17
gtkpod does the job+before ranting Apple tries its hardest to make people use Itunes that you have to pay for so you should be complaining to them for making a over priced piece of kit or buy a mp4 player,That you can drag and drop files into this is the way in 2010.
Yes I have a Ipod and i keep it in the draw so it does not get damaged.

---

### Post by thockin on 2010-01-17
Unfortunately, for many / most cars - iPod is the only supported option for bulk MP3.

---

### Post by kelvin spratt on 2010-01-17
I drive a modern Ford my mp4/Ipod player plugs directly into the aux socket as does 95% of British cars in the last 10years.

---

### Post by warfacegod on 2010-01-17
> **thockin said:**
> From what I can tell by fiddling and reading, Rhythmbox, the default Ubuntu media player is fundamentally crippled for use with ipods.  It doesn't support ipod smart playlists on the ipod itself.

Sure, you can create an "automatic playlist" on the ubuntu side, but how on earth does that transfer to the ipod?  As far as I (and google) can tell - it doesn't.  Which makes rhythmbox basically useless for ipods.

Can that be right?  What am I doing wrong?

And to add insult to injury, banshee doesn't work for ipods at all because of automounting media (that's two apps that are broken due to this - gThumb and banshee).

Why does Ubuntu bundle such AWFUL apps for the out-of-the-box experience?  I've spent pretty much ALL DAY trying to figure out how to get my music onto the ipod while retaining playlists (required for my car integration).

Clue me in?  Frustrated...

Tim

Ubuntu comes with Rythbox because it is small.  They need to be able to get as much as possible on to CD after all. Install gtkpod from Synaptic.

---

### Post by qyot27 on 2010-01-17
> **kelvin spratt said:**
> gtkpod does the job+before ranting Apple tries its hardest to make people use Itunes that you have to pay for so you should be complaining to them for making a over priced piece of kit or buy a mp4 player,That you can drag and drop files into this is the way in 2010.
Yes I have a Ipod and i keep it in the draw so it does not get damaged.
You don't have to pay to use iTunes.  The only thing you pay for in regard to iTunes is any media (music/movies/etc) you order through the iTunes Store, but you can encode your own stuff and manage your iPod with it for free.  Apple doesn't require you to buy Quicktime Pro in order to do that stuff.  The only assumption is that you're running Windows or OS X.

But anyway, gtkpod works fine with the Shuffle I have.  Rhythmbox and the other apps (if I could even get them to see the iPod, at least) apparently can't handle rewriting the database so the darn thing works properly on its own - the MP3s would play fine, but any AAC files weren't recognized until I used gtkpod to sync with it.  As far as I read, gtkpod is one of, or *the*, only app capable of doing that on Linux.

---

### Post by thockin on 2010-01-17
Regarding car integration : who wants to fiddle with the ipod while driving?  I want full dashboard control integration.  I get that to some degree, but it *only* works with iPod and it *only* works with playlists.

Thus, all of the dumb apps that forget about playlist control are useless.

Regarding small : I get that, but it seems to me like really good iPod integration should be something that works for a desktop OS install.

Regarding gtkpod : I did start in with gtkpod.  It's not exactly "robust".  It blew up in my face when I added 1 file too many.  it did not warn me, just blindly copied files until it started failing, and then left me with a full ipod that thought it had 0 media files on it.  Clever.

Also gtkpod is *DOG* *SLOW*.  I don't understand how apps like Listen (python) and Banshee (mono) can be faster than a native apps at doing things like displaying large amounts of data.  And somehow it is also really slow copying data to the device.

Sigh.  I guess this is the state of the art for Linux.

---

### Post by warfacegod on 2010-01-17
It is by no means "state of the art". Linux is a solid OS that is more than capable of competing with MS and Mac. The real draw back is that it has become more and more difficult to find the right apps for the users needs and decent assistance when the need arises.

---

### Post by thockin on 2010-01-18
Ubuntu (and other distros) have started the unenviable task of choosing the "one true" app for each functional area.  They HAVE TO.

They chose rhythmbox as the one true music player.  Sadly, they chose an app that is very over-simple (which holds with all the GNOME design ideas for the past 8 years) and does not work for ipods out-of-the-box.  I assert that ipod support is a must-have to bill yourself as a desktop OS today.  Just as is digital camera support and USB mass storage are must-have.

They chose F-Spot for digital cameras, which is (IMHO) another bad choice.  It doesn't do simple things like delete the images off the camera. The alternative, gThumb, doesn't work properly in Karmic.  Nice.

Joe Random desktop Ubuntu user *must* *not* be forced to make these decisions.  They are not equipped to install Rhythmbox, Banshee, Listen, Exaile, and Amarok and then decide between them.  Especially since they all half-work.  Some still use HAL.  Some use DevKit.  Some work with automount.  Some don't.

With GNOME changing its infrastructure yearly, an average user is just not equipped to figure out how to make things work.  Hell, *I* am not equipped to figure out how to make things work.  I have to Google the error messages I get to find out that other people can't delete photos or sync ipods.  Imagine a desktop OS that can't manage photos or sync ipods.  What if Apple of Microsoft shipped such an animal.

Ubuntu has to decide which is the one true well-integrated, well-tested, well-made application for each segment.  But they also need to make a realistic set of user experience metrics.  I think that digicams and ipods should be obvious ones.

And don't get me started on the COLLOSAL waste of time and energy and money that is KDE vs GNOME.  Microsoft could not have built a better trap.  It has consumed approximately half of the development resources available desktop development for the last 10 years.  Imagine where we could be if we had instead all spent our time on a single solution.

---

### Post by warfacegod on 2010-01-18
I mostly agree with you. Note I said "capable" not simply "is competing" in my last post. I had a bit of a rant on this of my own #18

[http://ubuntuforums.org/showthread.php?t=1380234&page=2]("http://ubuntuforums.org/showthread.php?t=1380234&page=2")

> What if Apple of Microsoft shipped such an animal.

I can't speak for Apple having never used it but MS has been shipping such animals from day one. (Vista?) Not necessarily iPod (although that was an issue for a long time) but anything. Windows isn't even compatible with itself. MS writes software that's shipped in Windows that refuses to work properly. Internet explorer when run in a Restricted user account comes to mind right away.

I still stand by my statement that Ubuntu is capable of competing but I also think that Cannonical really needs to get it together. I think one of the best things they could do for themselves and us is skip the release of 10.04 and concentrate getting everything working. It's also getting be time to do away with CD installs. We are entering the age of Blueray's 50 GB media so DVD ought to start being utilized for installs. It will give Cannonical allot more room to flex.

---

### Post by qyot27 on 2010-01-18
> **thockin said:**
> Imagine a desktop OS that can't manage photos or sync ipods.  What if Apple of Microsoft shipped such an animal.
Since when has Windows been able to magically sync iPods without the use of iTunes?  And iTunes is far from coming standard on Windows PCs, as far as I knew.  Best Buy or Staples or Office Depot, et al. preconfigured systems notwithstanding.  Still isn't Microsoft's job to put a major competitor's - or any competitor's - software in their OS.

What I'm about to say isn't directed at anyone in particular, just a mindset and dispute over direction that I think needs to be considered here.

Hey, call me old-fashioned, but 'media management' apps are by and large a total waste of time.  Sure, try to make the user experience as trim and streamlined and friendly as possible, but too much hand-holding is the worst thing that can happen.  It gets to the point where you don't know what the heck the OS is doing with your stuff under the hood.  This is exactly the reason why I refuse to use iTunes itself to sync my iPod (with all the reports of weirdness that arise from the library management, and especially the even-worse-than-before resource hogging that typifies iTunes 9).  All I need for enjoying my digital music collection is Winamp 2.95 and Audacious.  Period.  Library functions can go fly a kite for all I care - they're extraneous.

You wanna take the photos off your digital camera?  Go in through your file manager and cut and paste.  No extra crap that you think you need to install just because your camera or camcorder came with some software, no extra weird steps to follow, just regular old user-driven file management.  I don't trust my OS to know where I put things on my system - I trust ***me*** to know where I put things on my system.

I was like this even before I got into all the technical things about Linux, or video editing, or any of that stuff - for practically as long as I've used computers, I've stood on the point that you need to be organized and know where you put your own stuff, not rely on someone or something else to do that for you.  There's only so far before computers are no longer computers but merely digital butlers.  If you're not interested in doing any sort of traditional task and are the type that really doesn't care about keeping yourself organized, maybe you need a digital butler.  But I sure don't, nor do I want one.

---

### Post by warfacegod on 2010-01-18
qyot27:

  Cheers to that hoss!

---

### Post by kelvin spratt on 2010-01-18
There is not a problem gtkpod It is a good application if you take time to learn how to use it.
There is also a couple of others as well hipo, floola, amarok all sync with ipod.
For mp4 players Atunes, is outstanding.
 Most modern mp4 players use play lists, mine only cost £40 and does all my ipod does.
Also you might be able to use itunes, under wine, And certainly under vbox, with XP, or just duel boot, 
If its any consolation win7 does not find my mp4 player nor does windows media player but my humble Linux does , 
The great almighty MS has problems too and yes this is 2010.

---

### Post by warfacegod on 2010-01-18
> Also you might be able to use itunes, under wine, 

No, not so much.

---

### Post by redwoodguy on 2010-01-20
> **thockin said:**
> Please pardon my rant.  I just can't believe that in 2009, now 2010, it is still this hard (impossible) to manage an iPod.

Approximately 94% of computer users have one.  And Linux people wonder why "regular" folks don't use Linux.
I agree. As a newcomer to Linux and Ubuntu, I love the OS, but the multimedia apps are very poor. I tried four NLEs just to find one that even worked without crashing. It is plain foolish to try to compare these little homebrew apps to glossy commercial products like iTunes, PhotoShop, Final Cut,  iPhoto and so on. 

I love my Ubuntu though! I have two new PCs and one Mac running Ubuntu, and it is as cool as it gets. But I also am *not* throwing out my OS/X Snow Leopard box. Linux reminds me of building backyard hot-rods - tons of tinkering, a little race time, and then back in the shop for more twiddling. My wife is a lifetime Mac user and spends 8 hours a day working on her computer. She, for example, wouldn't put up with Linux for 2 minutes. 

Ya gotta remember, this stuff is ***free***. You can't compare your DIY backyard hotrod to a new BMW. You have to adjust your expectations, and enjoy it for what it is.

---

### Post by redwoodguy on 2010-01-20
I just downloaded gtkPod. Didn't recognise my iPOD. REMOVE.

---

### Post by warfacegod on 2010-01-20
> **redwoodguy said:**
> I agree. As a newcomer to Linux and Ubuntu, I love the OS, but the multimedia apps are very poor. I tried four NLEs just to find one that even worked without crashing. It is plain foolish to try to compare these little homebrew apps to glossy commercial products like iTunes, PhotoShop, Final Cut,  iPhoto and so on. 

I love my Ubuntu though! I have two new PCs and one Mac running Ubuntu, and it is as cool as it gets. But I also am *not* throwing out my OS/X Snow Leopard box. Linux reminds me of building backyard hot-rods - tons of tinkering, a little race time, and then back in the shop for more twiddling. My wife is a lifetime Mac user and spends 8 hours a day working on her computer. She, for example, wouldn't put up with Linux for 2 minutes. 

Ya gotta remember, this stuff is ***free***. You can't compare your DIY backyard hotrod to a new BMW. You have to adjust your expectations, and enjoy it for what it is.

Bear in mind that your "glossy commercial apps" are usually more prone to crashing, underhanded behavior (calling home without asking), doing what they want not what you tell them, locking up your stuff (DRM), and in many cases, forcing you give them money periodically. Now that I think about it, that sounds allot like a teenager too. 

As far as "home brew" goes, in many cases, that really just translates into a steeper learning curve. Users have been spoiled by the point click, point click mentality of Windows and Mac. That same attitude is what got MS the Tsunami of viruses and their ilk.

I put my wife (who thinks binary code is Morse Code with binoculars) in front of an Ubuntu machine last year. There are no Windows in my house (stop groaning, it's not a pun) any longer. Over the last year I have heard my wife say "I couldn't do that in *Windows*" countless times. Not once have I heard "Windows let me do this, why can't I do it here?".

Final argument on "glossy commercial" vs. "home brew". VLC Media Player is "home brew" and ***_CRUSHES_*** the competition.

(I don't use it so please don't try to accuse me of bias.)

---

### Post by redwoodguy on 2010-01-20
warfacegod--
It may depend on what apps you are really comparing. I've been making videos on Mac since 1999 or so. I can't recall any versions of iMovie, and I have had them all, which crashed or locked up or failed to produce useful output. I've made 100 movies on that platform. I am not saying it is the best editor, I am saying it works, has predicatable results, and doesn't do anything unexpected. Anyone could take a few minutes to learn it and produce a movie.  It's a finished, working, tested, reliable product.

My recent attempt to get that kind of "product" on Ubuntu was a test of patience. I installed several programs people recommended for video editing. Two of them would not even RUN - period. The third one ran in semi-useable state for a few minutes before crashing when a few buttons were pushed in an order it didn't like. There's simply no possible rationalisation to compare these barely working apps to iMovie, except to say, "well hey, they're free!" Ok, I get that. And, I can make that trade off. But I would never kid myself and pretend these are competitive offerings - they aren't.  

I get the idea of getting off the Microsoft and Apple bandwagon. No problem. I am enjoying the whole Linux experience and having a ball. But that doesn't mean I should delude myself into thinking all these crude little homebrew apps are "really just as good."

---

### Post by warfacegod on 2010-01-20
> **redwoodguy said:**
> warfacegod--
It may depend on what apps you are really comparing. I've been making videos on Mac since 1999 or so. I can't recall any versions of iMovie, and I have had them all, which crashed or locked up or failed to produce useful output. I've made 100 movies on that platform. I am not saying it is the best editor, I am saying it works, has predicatable results, and doesn't do anything unexpected. Anyone could take a few minutes to learn it and produce a movie.  It's a finished, working, tested, reliable product.

My recent attempt to get that kind of "product" on Ubuntu was a test of patience. I installed several programs people recommended for video editing. Two of them would not even RUN - period. The third one ran in semi-useable state for a few minutes before crashing when a few buttons were pushed in an order it didn't like. There's simply no possible rationalisation to compare these barely working apps to iMovie, except to say, "well hey, they're free!" Ok, I get that. And, I can make that trade off. But I would never kid myself and pretend these are competitive offerings - they aren't.  

I get the idea of getting off the Microsoft and Apple bandwagon. No problem. I am enjoying the whole Linux experience and having a ball. But that doesn't mean I should delude myself into thinking all these crude little homebrew apps are "really just as good."

VLC and Amarok 1.4 (I'm still pretending 2.2 never happened) are easily equal to their commercial counterparts, such as Windows Media Player or iTunes, if not superior. Of all three platforms, MythTV is considered by many to be the best Media Center available.

Bear in mind that historically Macs have almost always been preferred over PC for multimedia editing because of the hardware not just the software. I do no video editing so I cannot compare iMovie to anything.

I started with Ubuntu Linux three years ago. Two years ago, I completely dropped Windows. I have yet to find any Windows application that Linux can't equal. Leaving gaming out of it because that lays almost exclusively in the realm of the game developers. Macs get ignored on that one too. Open Office does things that MS Office can't do and will probably never do. Gimp is basically equal to Photoshop from what I've read here. 

A fractal generator I used in Windows froze my desktop and my laptop shutdown because the CPU started to overheat. In Linux, on the same machine, I got fractal images not a crashed OS and overheated processor.

If you have a DVR, it's probably a Linux OS running it. Many, if not the majority, of internet servers are Linux and they are able to stay up *much* longer than other OS based servers. Allot of Hollywood features are now being made with Linux, not Mac, not Windows.

[http://www.linuxjournal.com/node/8589/print]("http://www.linuxjournal.com/node/8589/print")

---

### Post by qyot27 on 2010-01-20
> **warfacegod said:**
> Bear in mind that historically Macs have almost always been preferred over PC for multimedia editing because of the hardware not just the software. I do no video editing so I cannot compare iMovie to anything.
iMovie is at the low end of the video editing scale, along with Windows Movie Maker.  Sadly, it seems most apps for NLE video editing on Linux are geared toward this segment rather than professional or prosumer areas.  It's a start, but it also seems like people forget that old Unix maxim - do one thing, do it well - and instead go for ten different things, sort of half-baked.  There's no uniformity of drive in the Linux video editing arena.

I experienced the heavy bias toward Mac when I was in the introductory class for my Digital Media certification (which I still haven't finished).  Truth is, even when I took that class, the field between PC and Mac was already even software-wise - but we were still told that if you don't use a Mac and Final Cut or Avid on either platform, the industry won't even look at you (not really true either - many primetime shows and movies are edited on Premiere, which is my preferred environment; at the time I took the class, the Intel switch hadn't happened, so the only versions of Premiere on Mac were pre-Pro - I use 6.5 on Windows, but the general impression is that until CS3 for Mac arrived, Premiere on Mac was a bad idea, and was partially the reason Adobe didn't release a version of Premiere on OS X from 6.5 to CS3).

But there is one area where Windows has an advantage over OS X - [[COLOR="Blue"]it's called AviSynth, and it's GPL[/COLOR]](http://en.wikipedia.org/wiki/AviSynth); it also has a lot of interactivity with projects like ffmpeg/mplayer/mencoder/x264, but only on Windows.  You can sort-of run it in Wine, but a couple of the source filters (those that rely on the Windows subsystem or VFW/DirectShow media frameworks like AviSource and DirectShowSource) don't work or have trouble.

When talking about Linux, though, the fact is that most media apps of high acclaim are A) based around libavcodec and other code from ffmpeg, and/or B) are crossplatform, so you'd already know them from using them under Windows or OS X.  It's just that the video editing apps are not currently mature enough to compete with the likes of Premiere, Final Cut, Avid, or Vegas (the only two near that level are Cinelerra, which is kind of love it or hate it, and Blender, which isn't really meant for NLE work primarily). The buzz around Lumiera and Saya is promising, though (except that Saya has now been pronounced dead, but given so with the option that someone else could take over; Lumiera is a rewrite of CinelerraCV, but seems to be more extensible towards growth in the right direction).

> Gimp is basically equal to Photoshop from what I've read here.
If memory serves, GIMP is actually used in Hollywood - notably by Dreamworks (although that was the old Film variant of GIMP, CinePaint).  And the Blender Foundation has the Open Movie Project which has produced two short films, and is currently working on a third.

---

### Post by CascadianPDX on 2010-01-25
> **thockin said:**
> Please pardon my rant.  I just can't believe that in 2009, now 2010, it is still this hard (impossible) to manage an iPod.

Approximately 94% of computer users have one.  And Linux people wonder why "regular" folks don't use Linux.

I'm really liking Karmic for a lot of reasons, but hardware issues are a real problem for me, and others too it seems. I couldn't recommend Ubuntu to any non-techy folks when EVERY music app either can't see the iPod or work playlists. That some folks can make it work doesn't help the open software cause if noobs are left on their own in frustration. Is there a checklist of how to diagnose iPod issues? This random 'try this, install that' just leads to frustration more often that a solution.

---

### Post by warfacegod on 2010-01-25
Maybe Launchpad has something like that. Tips & Tutorials is a good place to look as well.

---

### Post by warfacegod on 2010-01-25
This is the first thread that came up when Ityped "ipod" into the search bar in Tutorials & Tips:

[http://ubuntuforums.org/showthread.php?t=1355610&highlight=ipod]("http://ubuntuforums.org/showthread.php?t=1355610&highlight=ipod")

---

### Post by redwoodguy on 2010-01-25
> **warfacegod said:**
> This is the first thread that came up when Ityped "ipod" into the search bar in Tutorials & Tips:

[http://ubuntuforums.org/showthread.php?t=1355610&highlight=ipod](http://ubuntuforums.org/showthread.php?t=1355610&highlight=ipod)

From the tutorial:
"Make sure it’s not empty and whatnot; it should be a large-ish plist (XML file) with a bunch of info."

:D

---

### Post by astowe32 on 2010-11-05
So after all these rants... Does anyone have the playlists working?

I have 10.04 & 0.12.8 Rhythmbox and it doesn't work. I see that rev 13 is available from the Rhythmbox site. Anyone try it out before I spend time loading it up?

Release notes show that a lot of work is done on playlists. This one was of interest:
```
commit f487224746a591a56f49a7f14c2a7449e466ca57
Author: Christophe Fergeau <teuf@gnome.org>
Date:   Sat Oct 2 12:18:57 2010 +0200

    [ipod] fix addition/removal of playlist items (bug #601152)
    
    The code that was connecting the addition/removal callbacks to the
    playlist model wasn't connecting to the correct model, so the
    callbacks were never getting called, and thus rhythmbox was never
    actually telling libgpod to add new data items to the playlists.
    This is easily fixed by using the correct model, though we'd also need
    to handle notify::base-query-model since it can change.

```


  Allen...

---

