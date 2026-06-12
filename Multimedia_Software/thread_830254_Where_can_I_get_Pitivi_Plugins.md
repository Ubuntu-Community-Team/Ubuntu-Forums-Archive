---
title: "Where can I get Pitivi Plugins?"
date: 2008-06-15
forum: Multimedia Software
---

### Post by nachomania on 2008-06-15
Where can I get effects and transitions plugins for pitivi? Do they exist?

---

### Post by JS Lemming on 2008-06-19
I have been wondering this myself. It feels like no one wants to admit that they don't exist or something.

---

### Post by Gannon8 on 2008-10-15
Yeah, for some reason, it does not seem anyone has made any.

---

### Post by middlemilk on 2008-10-27
I've been looking around too, without any success...

---

### Post by 47_MasoN_47 on 2008-11-04
I'd like to know this as well, and also if there is any way to get more codecs supported by it.

Sorry to revive an old thread, but I thought it would be better than making a new one about the same thing.

---

### Post by altonbr on 2008-11-04
> **47_MasoN_47 said:**
> I'd like to know this as well, and also if there is any way to get more codecs supported by it.

Sorry to revive an old thread, but I thought it would be better than making a new one about the same thing.

It's okay, I'm looking for this too!

---

### Post by kiddo on 2008-11-05
Yeah. PiTiVi does not have any existing transitions/plugins at the moment. This is not about "no one wants to admit it", it's publicly known. I mean, this is the first time I see such a thread, I have followed the PiTiVi mailing list and I don't remember anyone asking about this before today. And this is not because they're being dishonest, it's because they are still concentrating on getting the **basic feature set** done. Until that is done, there are no transitions or stuff like that (but it looks like development should speed up soon, since Brandon [was hired]("http://blogs.gnome.org/uraeus/2008/10/09/supporting-pitivi/") (full-time maybe?) to give some serious love to PiTiVi now).

They still need as much help as they can get, so if you want to learn programming Python (which is pretty much the easiest language around), consider joining in the project, and they will gladly help you get started.

In the meantime though, PiTiVi is nowhere near being ready for general video editing. I speak as a former hobbyist video editor (doing [silly films]("http://studios.ecchi.ca") with Vegas Video).

---

### Post by altonbr on 2008-11-05
> **kiddo said:**
> Yeah. PiTiVi does not have any existing transitions/plugins at the moment. This is not about "no one wants to admit it", it's publicly known. I mean, this is the first time I see such a thread, I have followed the PiTiVi mailing list and I don't remember anyone asking about this before today. And this is not because they're being dishonest, it's because they are still concentrating on getting the **basic feature set** done. Until that is done, there are no transitions or stuff like that (but it looks like development should speed up soon, since Brandon [was hired]("http://blogs.gnome.org/uraeus/2008/10/09/supporting-pitivi/") (full-time maybe?) to give some serious love to PiTiVi now).

They still need as much help as they can get, so if you want to learn programming Python (which is pretty much the easiest language around), consider joining in the project, and they will gladly help you get started.

In the meantime though, PiTiVi is nowhere near being ready for general video editing. I speak as a former hobbyist video editor (doing [silly films]("http://studios.ecchi.ca") with Vegas Video).

I just don't understand how everyone can rant and rave about a video editor that can't even do transitions, effects, subtitles and text effects, color correcting, etc. I mean, what can it be used for? Editing the timeline is about it, right?

I had to edit a movie last night and ended up using Adobe Premiere Pro 2.0 (sadly) because I couldn't even do a transition in PiTivi!

That being said, I have *read* there they have extend-able, modular, open-source framework there for a great video editor and that good things will come from it soon. It just doesn't seem like soon enough because Kino, OpenMovieEditor, etc. are just garbage and the state of open-source video editing is almost completely unusable. 

I've been using purely and wholly open source software for years and I must say this is one area that needs catchup.

I offered to help PiTiVi with their website on their mailing list, but no one took me up on it. I'd help program in Python if I knew how, but I don't.

I look forward to PiTiVi in Ubuntu 9.10, but that just feels too far away.

---

### Post by kiddo on 2008-11-06
> **altonbr said:**
> I just don't understand how everyone can rant and rave about a video editor that can't even do transitions, effects, subtitles and text effects, color correcting, etc.

It is indeed fanboyism/vaporwarism; as the *authors* of pitivi don't actually say stuff like that. People "outside" of it look at the screenshots/read the blogs around and hype it up (that's what I think) without trying it for real. Or there is a fair amount of group thinking/denial in place.

However, PiTiVi has a special place in the hearts of many as being hailed as the "right way to do it", because it uses the gstreamer multimedia framework. I would like to think that it is the way of the future, too (but I am not certain).

Take a look at the [blog post I wrote a few months ago]("http://jeff.ecchi.ca/blog/?p=295") on the situation, which also references another blog post by Eugenia about the Elephant in the room.

> I mean, what can it be used for? Editing the timeline is about it, right?

You are right. It can do no more than stitching clips one after another and rendering the timeline at the moment (and it has been like this for a long time). I expect things to start changing, however, for three reasons:
[LIST=1]
[*]I have seen more and more interested contributors appearing (one of which was Brandon Lewis over a year ago)
[*]they *finally* followed my advice to ditch the "two timelines: simple and advanced" idea. It was a recipe for failure and I told them years ago that it would cause problems. Now they will concentrate on only one timeline, and that will make things simpler
[*]Brandon is now full-time on pitivi, as I understand it
[/LIST]

> I had to edit a movie last night and ended up using Adobe Premiere Pro 2.0 (sadly) because I couldn't even do a transition in PiTivi!

Sure. If I had to edit movies nowadays, I would still be falling back to Windows to use Vegas Video, or anything "mature". Or if I was overflowing with cash, I'd get a mac with iMovie, but the price tag is still giving me goosebumps. I'm somewhat glad I don't have time for making films nowadays.

> That being said, I have *read* there they have extend-able, modular, open-source framework there for a great video editor and that good things will come from it soon.

Personally, I'd keep my doubts on this. But that may be just me having waited for 4-5 years for this open source niche to be filled.

> I've been using purely and wholly open source software for years and I must say this is one area that needs catchup.

Agreed.

> I offered to help PiTiVi with their website on their mailing list, but no one took me up on it.

Hm, I don't see this in my archives, any link to it? Maybe I was not subscribed back then. In any case, PiTiVi *used* to have a website (I was the designer/webmaster, I still have it in my files, see the attached screenshot), but it has been replaced by the Wiki because the website was completely unmaintained. If you think you can maintain it in good/useful shape, maybe this could be done...

---

### Post by kiddo on 2008-11-06
[http://www.linux.com/feature/152464](http://www.linux.com/feature/152464)

I did not know/notice that they were really serious about getting something usable done by April. I guess things will get interesting.

---

### Post by carstanje on 2009-05-17
Too bad Pitivi isn't supported/developed anymore these days. I was trying kdenlive but it keeps crashing. Pitivi seems to be very simple and I like it's concept: Keeping it simple so it always works. With installing only the plugins you need it would remain simple. I guess without plugins it will remain too simple you can't use it...

---

### Post by carstanje on 2009-05-17
Too bad Pitivi isn't supported/developed anymore these days. I was trying kdenlive but it keeps crashing. Pitivi seems to be very simple and I like it's concept: Keeping it simple so it always works. With installing only the plugins you need it would remain simple. I guess without plugins it will remain too simple you can't use it...

---

### Post by Chrissss on 2009-05-17
> **carstanje said:**
> Too bad Pitivi isn't supported/developed anymore these days...

This is wrong. The development is quite active

[http://git.pitivi.org/?p=pitivi.git;a=shortlog](http://git.pitivi.org/?p=pitivi.git;a=shortlog)

---

### Post by carstanje on 2009-05-18
> **Chrissss said:**
> The development is quite active

Cool! This means there is still hope for this project! The development is made on the core of the project. I can't find anything about the plugins on this page. Hopefully there is some development on this part too.

---

### Post by DPic on 2009-07-01
People should help test the newest version in the PPA

> **nachomania said:**
> Where can I get effects and transitions plugins for pitivi? Do they exist?

Blending, compositing, capture, effects, transitions, and more will be done within the current 0.13.x development release series. More specifically, check out the roadmap: [http://www.pitivi.org/wiki/Roadmap](http://www.pitivi.org/wiki/Roadmap)

> **47_MasoN_47 said:**
> I'd like to know this as well, and also if there is any way to get more codecs supported by it.

Sorry to revive an old thread, but I thought it would be better than making a new one about the same thing.

PiTiVi supports every format supported by GStreamer. That's a LOT of formats. What format isn't supported?

---

### Post by matrix14 on 2009-07-19
@carstanje:

I also pitivi user with ubuntu 9.04, and also in real confusion that has "no dv grab to ieee1394 or raw1394" feature for pitivi althought I can capture directly from webcam on my laptop.

Something about KDENLIVE:
If you experienced crash with KDENLIVE, you may need to update your kernel. I have tried KDENLIVE with kubuntu 8.04 but with kernel 2.6.27-11 and no more crash (natively that kubuntu 8.04 uses kernel 2.6.24).

---

### Post by altonbr on 2009-07-21
I just noticed the PPA was listed recently, so anyone that is interested in running the latest and greatest, here's their PPA:

[https://launchpad.net/~gstreamer-developers/+archive/ppa](https://launchpad.net/~gstreamer-developers/+archive/ppa)

---

### Post by GMU_DodgyHodgy on 2009-07-22
I linked to the latest PPA sources for PiTiVi and installed the latest version of PiTiVi.  It is actually stable if not feature rich.  I was able to make a movie with photos and music files.  

I would love to have transitions and titling capabilities - HOWEVER, the basic features work and is stable. 

A big leap forward.

---

### Post by kiddo on 2009-08-04
Hey folks, long time no post :)

I just wanted to let you know that PiTiVi, as a project has been very, very healthy in the past few months (thanks to Collabora). It is developing faster than it ever did, and it is starting to become quite rock solid.

Still no transitions and effects, that will come sometime this autumn, if all things go well. In the meantime, it can still do basic editing. 

I will publish a brand new website sometime soon (been working on it during the summer), and also create a new release screencast (you can see the "old" release screencast for 0.13.1 [_here_]("http://people.freedesktop.org/~bilboed/0.13.1-final.ogv") to have an idea of what kind of features we had... 3 months ago! Now we have more than that.)

I am very happy about the way the project is progressing lately.
See also [_my presentation_]("http://river-valley.tv/pitivi-an-overview-of-a-foss-video-editors-history-and-design/") of PiTiVi (and why I like this project) in May at LGM 2009, if you are curious.

---

### Post by DPic on 2009-08-05
> **kiddo said:**
> Hey folks, long time no post :)

I just wanted to let you know that PiTiVi, as a project has been very, very healthy in the past few months (thanks to Collabora). It is developing faster than it ever did, and it is starting to become quite rock solid.

Still no transitions and effects, that will come sometime this autumn, if all things go well. In the meantime, it can still do basic editing. 

I will publish a brand new website sometime soon (been working on it during the summer), and also create a new release screencast (you can see the "old" release screencast for 0.13.1 [_here_]("http://people.freedesktop.org/~bilboed/0.13.1-final.ogv") to have an idea of what kind of features we had... 2 months ago! Now we have more than that.)

I am very happy about the way the project is progressing lately.
See also [_my presentation_]("http://river-valley.tv/pitivi-an-overview-of-a-foss-video-editors-history-and-design/") of PiTiVi (and why I like this project) in May 2009, if you are curious.

Awesome! Let us know when the new website and screencast is up

---

### Post by Tux118 on 2009-08-05
> **kiddo said:**
> Yeah. PiTiVi does not have any existing transitions/plugins at the moment. This is not about "no one wants to admit it", it's publicly known. I mean, this is the first time I see such a thread, I have followed the PiTiVi mailing list and I don't remember anyone asking about this before today. And this is not because they're being dishonest, it's because they are still concentrating on getting the **basic feature set** done. Until that is done, there are no transitions or stuff like that (but it looks like development should speed up soon, since Brandon [was hired]("http://blogs.gnome.org/uraeus/2008/10/09/supporting-pitivi/") (full-time maybe?) to give some serious love to PiTiVi now).

They still need as much help as they can get, so if you want to learn programming Python (which is pretty much the easiest language around), consider joining in the project, and they will gladly help you get started.

In the meantime though, PiTiVi is nowhere near being ready for general video editing. I speak as a former hobbyist video editor (doing [silly films]("http://studios.ecchi.ca") with Vegas Video).

I agree. What is the point of having pitvi? You can't import any clips and when you try to edit a video, it says it doesn't support files of that type even when I save it as nearly every video file that exists.

---

### Post by carstanje on 2009-08-05
> **Tux118 said:**
> I agree. What is the point of having pitvi? You can't import any clips and when you try to edit a video, it says it doesn't support files of that type even when I save it as nearly every video file that exists.
Did you install all the gstreamer plugins? Pitivi's possible codecs are based on the Gstreamer libraries.

The best way to go is to open synaptic package manager, search for gstreamer and select & install any necessary plugins you need.

---

### Post by kiddo on 2009-08-05
> **Tux118 said:**
> I agree. What is the point of having pitvi? You can't import any clips and when you try to edit a video, it says it doesn't support files of that type even when I save it as nearly every video file that exists.

Do not use anything older than 0.13.1. Apple and oranges. 

And make sure you have all the gstreamer plugins installed (and not the Fluendo plugins -- see the new 0.13.2 [experimental manual]("http://jeff.ecchi.ca/blog/?p=897") for a lengthy explanation on why)

---

### Post by SPARTAN-118 on 2009-09-07
Hi, I have also been looking for plugins for Pitivi, the fact that Pitivi (currently) has such an easy-to-use interface (as compared to LIVES and Cinelerra) makes it worth checking out and following its development.

I have the most recent version (0.13.2.3 from the PPA) on Ubuntu, but, sadly, still no transitions/effects.

I'm happy to say that all my formats are supported (WMV, all the mpeg(1-4), AVI, flv (a rarity, and IMO, necessary), and more!)
However, what's confusing to me is that, the only WMV file that works that I've tried so far is a rendered clip from my File Share on Bungie.net (Halo 3).
Anybody have any idea as to why?

---

### Post by carstanje on 2009-09-07
Too bad the development isn't going as planned. The pitivi website still gives no accurate planning of when the plugins for transition/effects will be given, only that it will come someday. I guess if plugin support is created we still will have to wait for the actual plugins themselves. 

In some version (0.13.x) on some day this will come...hopefully...

See the planning: [http://www.pitivi.org/wiki/Roadmap]("http://www.pitivi.org/wiki/Roadmap"). The scheduled date for version 0.13.2 is in the past so probably this website isn't updated very often.

I am using 0.13.2.3 from the PPA, but it's hard to test because you can't really do what you want to do without transitions/effects & titling. This is a musthave for modern video-editing.

I am hoping that all development as described on the roadmap will be quickly. Only then Pitivi has a nice bright shining future lying ahead!

---

### Post by kiddo on 2009-09-07
> However, what's confusing to me is that, the only WMV file that works that I've tried so far is a rendered clip from my File Share on Bungie.net (Halo 3).
Anybody have any idea as to why?

The answer is, "it depends". There are so many fscked up things about windows media video, not even starting with the fact that it's a closed/proprietary format from Microsoft, who were not so friendly in allowing open source software to (de)code wmvs.

Don't use that format unless you really have absolutely no choice. This is not a good format for editing.

> Too bad the development isn't going as planned.
Delays happen, especially when there's so much stuff to do and stabilize. Just look at the progress done in terms of stability and usability fixes in the past few months. I counted over 1200 commits in the master code branch in the past few months.

Development is proceeding steadily. They just need to get the basics done right and rock-solid before implementing stuff like effects and transitions (although yes, this has been pushed back several times already, from April to "sometime this fall"). One of the things that needs to be carefully implemented (and rigorously tested) in order to have transitions, compositing and effects, is "video mixing".

Edward [started implementing videomixing last week]("http://jeff.ecchi.ca/blog/2009/09/01/video-mixing/"), but it was judged too experimental at the time to be merged in the master branch (and so it will not be in the stable release that will come out in the next few days). I agree with him, I prefer something that is stable and tested than something that creates incorrect output.

PiTiVi has a lot going for it. Although it is less flashy than other editors because it doesn't yet have transitions/effects, it makes up in ease of use, stability and formats (my personal opinion, but also from the feedback I received from various users, [including Alan Pope]("http://popey.com/blog/2009/09/02/a-video-editor-that-just-works/")).

I'm still regularly poking Edward so that he prepares his server to allow me to upload a brand new website, but he's insanely busy with PiTiVi, as always. The new website is ready, but its publication has been delayed many times too. Delays happen, but progress is steady. I can live with that :)

> i guess if plugin support is created we still will have to wait for the actual plugins themselves. 
You are probably right. Unless the devs have enough free time to implement additional features as plugins. The plugin infrastructure will probably need some work before that's possible though, I am not sure. But then, when you think about it, the whole idea about a plugin architecture is that it's there to encourage third-party contributors to quickly write new features (instead of having the main devs do everything)...

> See the planning: [http://www.pitivi.org/wiki/Roadmap](http://www.pitivi.org/wiki/Roadmap). The scheduled date for version 0.13.2 is in the past so probably this website isn't updated very often.
The wiki roadmap/readmes/releases/etc. are updated when a release comes out, basically.

So, for effects and transitions: yeah, we know, and they are high on the priority list, just be patient. If they are not being implemented, it's because there are issues that are even more important to solve first (for stability, etc.)

---

### Post by SPARTAN-118 on 2009-09-08
I just hope that they get everything implemented before the end of this year. Right now I'm using Kdenlive for video editing, and while it itself is a great, relatively easy-to-use application, I don't like using KDE apps in GNOME (for the fact that 1.Their KDE colours don't look good with my Metacity theme and 2.IMO they don't work as well as native GNOME apps).

I just hope that Pitivi's interface doesn't change much, because I love it how it is, maybe they could implement a sidebar like in WMM, but I just don't want Pitivi to end up looking like LIVES or Cinelerra (I hate their UIs).

As for WMV files... I should have known they weren't open-sourced, Microsoft is very anti-open sourced about everything, that's why you have to patch Vista/XP to use themes with them instead of Microsoft just including a theme editor within the OS itself.

If not for the Xbox 360 and Games for Windows and other Windows-exclusive applications, I'd very much be anti-Microsoft right about now.

---

### Post by kiddo on 2009-09-08
> **SPARTAN-118 said:**
> I just hope that Pitivi's interface doesn't change much, because I love it how it is
I am currently trying to think of a way to clean up the toolbars arrangement, but at the same time keep the same level of usability and discoverability. Not an easy thing. But other that, I don't have big UI changes in mind (as their main UI freak).

> **SPARTAN-118 said:**
> but I just don't want Pitivi to end up looking like LIVES or Cinelerra (I hate their UIs).

Don't worry about that; not a chance it hell, not while I'm alive and kicking :)

> As for WMV files... I should have known they weren't open-sourced
*Of course* they are not open in any way, whenever Microsoft creates a format, it's to lock-in their users or kill a competitor (in this case, Real networks with realmedia). If they cared the least bit about open source and open content and users' freedom, they would use opendocument by default in office, ogg theora/dirac/ogg vorbis/flac/ by default in windows media player/movie maker, and have an internet browser that is not complete crap that breaks the standards and stiffles innovation, etc. The list goes on. They could have done that years ago, but it obviously goes against their business model.

---

### Post by DPic on 2009-12-11
Yay new website is up! [http://www.pitivi.org/](http://www.pitivi.org/)

[http://www.reddit.com/r/linux/comments/adn6q/pitivi_is_an_awesome_video_editor_if_you_didnt/](http://www.reddit.com/r/linux/comments/adn6q/pitivi_is_an_awesome_video_editor_if_you_didnt/)

---

### Post by altonbr on 2009-12-13
> **DPic said:**
> Yay new website is up! [http://www.pitivi.org/](http://www.pitivi.org/)

Looks good! A little too much on the inside jokes and sarcasm though.

---

### Post by switch10 on 2009-12-13
still no transitions....

---

### Post by DPic on 2009-12-14
> **switch10 said:**
> still no transitions....

[http://identi.ca/notice/15122097](http://identi.ca/notice/15122097)

---

### Post by Fernando Hernandez on 2010-01-14
I don't know about the transitions and effects that OP is looking for, but what about additional format support?  I'm trying to import some .mkv clips and it says I need the MPEG-4 AAC decoder plugin, but I don't know how to get it.  Pitivi and Openshot have similar interfaces, but Openshot doesn't seem to work with hotkeys (even the universal CTRL + Z), and I just need something for simple video editing.  Having tried a lot of open-source editors those two seem to have the most understandable interfaces, but is there no plugin I can use to get Pitivi to import .mkv format?

---

### Post by altonbr on 2010-01-15
> **Fernando Hernandez said:**
> I don't know about the transitions and effects that OP is looking for, but what about additional format support?  I'm trying to import some .mkv clips and it says I need the MPEG-4 AAC decoder plugin, but I don't know how to get it.  Pitivi and Openshot have similar interfaces, but Openshot doesn't seem to work with hotkeys (even the universal CTRL + Z), and I just need something for simple video editing.  Having tried a lot of open-source editors those two seem to have the most understandable interfaces, but is there no plugin I can use to get Pitivi to import .mkv format?

PiTiVi is based on gStreamer, so whenever I see this question I always see the answer "install gstreamer everything" meaning go into Synaptic (System > Administration > Synaptic Package Manager), search 'gstreamer' and install all packages that start with 'gstreamer0.10-' except for the 'gstreamer0.10-fluendo' codecs.

Hope that helps.

---

### Post by hesjnet on 2010-01-17
> **switch10 said:**
> still no transitions....

When Ubuntu 10.04 ships with pitivi we will probably see alot more development from third party programmers.

---

### Post by Jarige on 2010-01-23
I installed this after hearing this program was to be included in 10.04. I was a little disappointed when I saw that there weren't any plugins, transitions or effects. However, I am fully confident that we will see a good version in 10.04 :)
This is by far the most easy GUI I've seen in open source video editing programs. The other ones are just a total chaos of features with complicated names and no explanation. Windows Movie Maker is a very easy video editing program, I suggest they'd take it as an example. Even a computer noob manages to use WMM, I hope it would be the same with PiTiVi. I do not like the name though. I expect the 'Vi' part to be 'video', but what are the other parts?

---

### Post by mountain_goat on 2010-01-24
The name, yes, I was wondering that too,
PiTiVi ~ my guess was that it may be French as in petit [small(fem)], the piti part is pronounced the same way as petit in French, silent last 't', so a small video editing program might be called PetitVi, but PiTiVi would look better and easier for English speakers to pronounce.

I too was looking to see if any plugins had been made available yet, and that is how I came across this thread. I am running Lucid Lynx Alpha on my tiny Dell D420 as my traveling netbook companion.

I import MOD file formats directly into PiTiVi from my JVC camera, works just as cleanly as my MAC, so I like that. Actually it shares likeness to iMovie.

What I do like about PiTiVi is that it has been chosen to be packaged with Lucid and the the UI is Gnome and clean and simple. The fact that it is in Lucid sort of indicates hopefully some form of commitment and the awareness to have a decent video editor as part of the installed base.

I guess for video editors, stability is a big requirement as you're not going to be around for long if users loose time consuming edits lost due to program stability issues. Stability is a biggy

I look forward to seeing PiTiVi developing into a solid and mature video editor for Linux.

---

### Post by kiddo on 2010-01-24
> I do not like the name though.

There are a couple of folks who dislike the name, but until someone comes up with a truly awesome replacement, it's not going to be changed (changing a project name is not something you do lightly). So if you guys want to hold a naming competition and something incredibly superior comes out, then I believe the devs would consider it.

> **mountain_goat said:**
> The name, yes, I was wondering that too, PiTiVi ~ my guess was that it may be French as in petit [small(fem)], the piti part is pronounced the same way as petit in French, silent last 't', so a small video editing program might be called PetitVi, but PiTiVi would look better and easier for English speakers to pronounce.

Not a bad guess, but that's not it :) it actually came from Epitech+TV. (Epi+TV --> Pi+TV --> PTV --> PiTiVi). It doesn't make much sense, it's just retrofitted like that.

> I import MOD file formats directly into PiTiVi from my JVC camera, works just as cleanly as my MAC, so I like that. Actually it shares likeness to iMovie.

What I do like about PiTiVi is that it has been chosen to be packaged with Lucid and the the UI is Gnome and clean and simple. The fact that it is in Lucid sort of indicates hopefully some form of commitment and the awareness to have a decent video editor as part of the installed base.

I guess for video editors, stability is a big requirement as you're not going to be around for long if users loose time consuming edits lost due to program stability issues. Stability is a biggy

I look forward to seeing PiTiVi developing into a solid and mature video editor for Linux.



Aaaah, positive feedback, this is so rare among the piles of flames of "no effects! no transitions! that means it can't do anything and that it sucks!!!11". Transitions are the next big thing in the plans, but I don't know when we'll finally get them. I hope in time for 10.04, but I've been wrong before... a couple times.

---

### Post by Jarige on 2010-01-24
I don't think it would be smart to implement PiTiVi before it has transitions and effects. It would disappoint quite a few people who are used to WMM.
I do see a nice future for this program. It still needs some work, but it looks very easy already. Can't wait to use this :)
I would like to see a plugin which will place black rectangle in front of the eyes. And one to place a beep somewhere in the sound, for instance when a name is called or when someone is cursing :)

As for the name, I like PTV more then those weird i's in the name :P
But if you could name it like a normal name, no abbreviations, that would be even better. But I do think that the developers should chose the name. They made the program, they should name it.

---

### Post by kiddo on 2010-01-24
> I don't think it would be smart to implement PiTiVi before it has transitions and effects. It would disappoint quite a few people who are used to WMM.

Me neither. I am worried of it being included in ubuntu due to the potential backlash if they don't have enough time to implement transitions and effects. Ubuntu's release schedule is very tight and the version freezes stuff is really worrying me, especially for the gstreamer dependencies.

---

### Post by Jarige on 2010-01-24
> **kiddo said:**
> Me neither. I am worried of it being included in ubuntu due to the potential backlash if they don't have enough time to implement transitions and effects.
My native language is not English, and I haven't quite figured out what you meant by 'backlash'. I've found some translations, but none of them feels right in this context. Could you explain what you mean by backlash?
I'm Dutch by the way, in case you wondered :) You might have noticed that by looking at my spelling and grammar...

---

### Post by mountain_goat on 2010-01-24
Goede dag Jarige,
I like to know where forum members are. Ik ben in 'Van Dieman's land, Tasmania in Australië. Coming back to Europe in May, can not wait ~~ yaaaaaa :)

'backlash' is the reaction to someone doing something. In this case, I would say, that they are meaning that by making PiTiVi available before more features are in the program might cause some people to criticise the program possibly causing undue frustration for the program supporters and developers.

mountain goat ~ grazing on a warm summers morning ......

---

### Post by kiddo on 2010-01-24
Yep, basically what mountain_goat said, and what [wikipedia says]("http://en.wikipedia.org/wiki/Backlash_(sociology)").

---

### Post by Jarige on 2010-01-25
I'm in the province Overijsel, in the Netherlands :)
And thank you for the explanation, I agree with it...
mountain_goat, where are you going in Europe?

---

### Post by mountain_goat on 2010-01-25
Well I land in Lyon on May 10th, head to the family home in the south of France, then buy a motorcycle and tour about France and visit family in Utrecht,dicht bij der Dom and other parts of the Netherlands, Deventer and Borger near Assen. Will be there in Europe for about 4 or so months, but mostly in France I would say.

Have just bought another laptop, a Dell D420 which is smaller that the large D830 I took with me last year to Europe. With Lucid Lynx Alpha Release (Ubuntu 10.04) installed and working very very well, the D420 is a very light 12" 1024 x 800 screen with a Core Duo processor. I choose to buy this over the latest 10" Atom based netbooks as the D420 is the same weight, but more rugged for the motorbike and with more capacity to do real stuff like editing sound and video, hence my interest in PiTiVi. I haven't been a video enthusiast in the past so this is new to me. I am more skilled in sound recording, and in it's many forms, art, soundscape, live performance recording and so on.

The reason for my interest in this thread is that I will mount my video camera on the motorcycle to record a few of the nice trips through France and then do some basic editing and viewing on the laptop.
So, I'm playing about now getting ready for it. If you are interested you can see this [here]("http://korider.com/index.php?topic=14925.0"), I am 'rockwallaby'

tot ziens
Paul Alting van Geusau

---

### Post by altonbr on 2010-01-25
> **mountain_goat said:**
> Well I land in Lyon on May 10th, head to the family home in the south of France, then buy a motorcycle and tour about France and visit family in Utrecht,dicht bij der Dom and other parts of the Netherlands, Deventer and Borger near Assen. Will be there in Europe for about 4 or so months, but mostly in France I would say.

Have just bought another laptop, a Dell D420 which is smaller that the large D830 I took with me last year to Europe. With Lucid Lynx Alpha Release (Ubuntu 10.04) installed and working very very well, the D420 is a very light 12" 1024 x 800 screen with a Core Duo processor. I choose to buy this over the latest 10" Atom based netbooks as the D420 is the same weight, but more rugged for the motorbike and with more capacity to do real stuff like editing sound and video, hence my interest in PiTiVi. I haven't been a video enthusiast in the past so this is new to me. I am more skilled in sound recording, and in it's many forms, art, soundscape, live performance recording and so on.

The reason for my interest in this thread is that I will mount my video camera on the motorcycle to record a few of the nice trips through France and then do some basic editing and viewing on the laptop.
So, I'm playing about now getting ready for it. If you are interested you can see this [here]("http://korider.com/index.php?topic=14925.0"), I am 'rockwallaby'

tot ziens
Paul Alting van Geusau

That sounds really cool! When you end up putting this all together, can you post on YouTube/Vimeo/DailyMotion and post the link here??

---

### Post by Jarige on 2010-01-25
That does sound awesome :D
I wouldn't do it, I'm not a traveling person :P
I like home, and only go on a holiday during the summer vacations. After two weeks of being in France (that's where most Dutch go on holiday) I'm very glad to be home again... Nothing is more comfortable as your own bed, and nothing tastes as well as home made French fries :P
But I'm happy for you :D Hope I didn't disencourage you by this :P
I hope you'll have a good time in Europe.
One thing; we as Dutch people are said to be very direct in speech, compared to international standards. Therefore other nations may find us rude... Just as you know :) I don't know whether I'm direct, I can't measure it to many foreign people. Please let me know what you liked and disliked about the Dutch people, I'm very interested in that :) And the family you've got in the Netherlands, are they born here?

We're going off-topic :P Are you going to make a full video after the trip? And btw, how old are you?

---

### Post by mountain_goat on 2010-01-26
Thanks guys,
I think I need to set up a blog site where I can write about my travels and people can follow and see photos.
I'll try to set something up over the next few weeks and let you know altonbr and Jarige if you're interested in following my travels.

I still have some months before I start, but already I sense time progressing quickly to arriving in France and the beginning of my journey. There is much for me to work on in terms of getting all my gadgetry together as well as practical things as well.

At this stage I plan to take both the small Dell 420 notebook while riding about those gorgeous mountains as well as the Mac Mini Intel Duo which I will use at the family home in France for more serious and fun stuff.
I will just need to buy another LCD screen for the mac mini when I arrive.

I'll send you a private message Jarige, as I don't want to offend others with off topic talk.

Meanwhile I am happy with what PiTiVi can do for me now. And that is to simply edit sections of recorded film footage by cutting and scrubbing and documenting.

rockwallaby ~ hop hop hop ;)

---

### Post by CJay554 on 2010-03-02
Its a shame... i love the interface in comparison to kino, and its alot lighter than avidemux, and easier to use...

heres a dissapointing link...

[http://wiki.pitivi.org/wiki/PiTiVi_Love](http://wiki.pitivi.org/wiki/PiTiVi_Love)

---

### Post by kiddo on 2010-03-03
> **CJay554 said:**
> Its a shame... i love the interface in comparison to kino, and its alot lighter than avidemux, and easier to use...

heres a dissapointing link...

[http://wiki.pitivi.org/wiki/PiTiVi_Love](http://wiki.pitivi.org/wiki/PiTiVi_Love)

Why is that a disappointing link? It's there to be motivating, encouraging, and to instill passion on new and potential contributors! (and so far, it does seem to work a bit).

---

### Post by CJay554 on 2010-03-07
Well the dissapointing part is that almost all of them are not taken up as projects... =(

---

### Post by kiddo on 2010-03-08
Look at it the other way: other projects don't publicly, overtly advertise their weaknesses and provide an easy, concise list of features that new contributors can work on to learn the codebase. It's certainly much less intimidating than looking at the raw list of bugs and feature requests in pitivi.

I think you didn't look closely enough. A couple of them are undertaken by some contributors. But certainly not the majority, that would be a ridiculous expectation. Besides, if they were all being adopted by contributors, well, there would be no point for this list to even exist, since there would be no need.

---

### Post by CJay554 on 2010-05-10
well yeah obviously, but pitivi now being added to Ubuntu by default i would think there would be more contributors piling in! i wish i could contribute with the plug-ins :/

as far as programming i wouldn't know where to start looking, i know how to program but not so much implementation

---

### Post by Truthiswithin on 2010-08-01
This was a real show-stopper for me, until today I actually went ahead and tried Pitivi.  I realized the basic plugins I was looking for, like fades and annotations are actually doable without any plugins at all.  Fades are built in to Pitivi (those red lines at the top of every clip), and for text annotations or other graphics, GIMP PNGs with transparency are accepted perfectly by Pitivi.  Also, I am quite impressed by the absence of bugs in the program as compared to Cinerella and Open Movie Editor.  So far it hasn't crashed once.  Good work, people! :KS :KS :KS :KS :KS

---

### Post by kiddo on 2010-08-03
It's nice to hear some positive comments once in a while :) look forward to the next release. Effects are almost ready in a development branch, and maybe if we're lucky the guy working on titles (what you call "annotations") will finish the job soon, so you won't even have to use GIMP.

There are some annoying bugs with automatic crossfade transitions though (like [https://bugzilla.gnome.org/show_bug.cgi?id=609792](https://bugzilla.gnome.org/show_bug.cgi?id=609792)), I hope those can be solved.

---

### Post by BentSlightly on 2010-08-03
Pitivi seems pretty good but I have to restart it every time I edit my project. I hope it keeps being developed.

---

### Post by Truthiswithin on 2010-09-20
> **kiddo said:**
> It's nice to hear some positive comments once in a while :) look forward to the next release. Effects are almost ready in a development branch, and maybe if we're lucky the guy working on titles (what you call "annotations") will finish the job soon, so you won't even have to use GIMP.

There are some annoying bugs with automatic crossfade transitions though (like [https://bugzilla.gnome.org/show_bug.cgi?id=609792](https://bugzilla.gnome.org/show_bug.cgi?id=609792)), I hope those can be solved.
:) glad to be of what little support I can... thanks for your work.  Looking forward indeed :)

---

### Post by repunante on 2010-10-18
I cannot make PiTiVi work in Ubuntu 10.10 (neither in Ubuntu 10.04), when I reproduce the files in the timeline the audio is OK but the video stops. The only way to check what I'm doing is rendering the video after every change, which is a tedious process.
Sometimes when I add a video it freezes and I have to force PiTiVi to close.
I have installed all the packages which name starts with gstreamer and I added the PPA to have them updated but nothing improved.
Any suggestion?

---

### Post by kiddo on 2010-10-19
> when I reproduce the files in the timeline the audio is OK but the video stops. The only way to check what I'm doing is rendering the video after every change, which is a tedious process. Sometimes when I add a video it freezes and I have to force PiTiVi to close.

Could you file a bug report instead? (reminder: **devs don't read forums**. They read what's on bugzilla. I read what's on launchpad and forward it to bugzilla if I can reproduce it)

Your description is a bit incomplete, because I'm not experiencing such problems. Need exact steps to reproduce the problem, output from the terminal or debug logs, if you are using the stock ubuntu versions or if you are using the gstreamer PPA, etc.

---

### Post by repunante on 2010-10-30
> **kiddo said:**
> Could you file a bug report instead? (reminder: **devs don't read forums**. They read what's on bugzilla. I read what's on launchpad and forward it to bugzilla if I can reproduce it)

Your description is a bit incomplete, because I'm not experiencing such problems. Need exact steps to reproduce the problem, output from the terminal or debug logs, if you are using the stock ubuntu versions or if you are using the gstreamer PPA, etc.


Sorry about my incomplete description, I'm a neophyte in Linux and I have to figure out how to provide a more complete description.
What I realised is that inUbuntu 10.04, Kino, OpenShot and PiTiVi worked fine but in Ubuntu 10.10 Kino is reproducing the imported videos like 10 times faster, OpenShot suffer from unsynchronised audio/video and the video in PiTiVi just stops. The same is happening in the two computers that I have.

---

### Post by needlez6 on 2011-05-23
I feel like im beating a dead horse with this question, but how come they can't take the effects and stuff from like OpenShot and put them in Pitivi. I would just like something like the new windows movie maker live edition, for Linux. Currently using OpenShot but its a bit different. Also would like to be able to add words and effects at any give time segment. And add transitions to the words or how the words appear. Any ideas would be so help full. Please get back to me by email if you know of anything. [email]needlez6@aol.com[/email]. Thanks

---

### Post by kiddo on 2011-05-23
Effects are available in the upcoming pitivi release, which should be out in only a few days. 

If you have frei0r and libvisual and other libraries like that installed, pitivi has all the effects that openshot and kdenlive have, plus a couple more (from gstreamer).

Text/titles will be added during the summer (there are 4 students working on Summer of Code projects for pitivi).

---

### Post by teledyn on 2011-12-17
I guess it is a really long summer ;)

Yeah, I know, we can hardly complain when it is free software, but it would be really nice if even there was a webpage somewhere with an RSS feed that might tell us what's happening, are we waiting in vain, have all the devs jumped ship to some other project, or do we just keep on using kino (where did all the cool plugins go that used to be in kino?)

---

### Post by kiddo on 2011-12-19
> I guess it is a really long summer

Along the way they figured out that it was better to wait for the GES port to actually add the titles. Effects and transformation are already in, but titles will have to wait for this spring (hopefully). Afaik help is welcome on that front, there are just so many things the devs have to do.

> Yeah, I know, we can hardly complain when it is free software, but it would be really nice if even there was a webpage somewhere with an RSS feed that might tell us what's happening

You mean like pitivi planet on the pitivi front page? :)
Or the rss feed of git.pitivi.org, but you won't see much until they actually merge branches into it (the GES port happens in separate branches so far)

---

