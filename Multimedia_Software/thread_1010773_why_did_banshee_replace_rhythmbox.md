---
title: "why did banshee replace rhythmbox?"
date: 2008-12-14
forum: Multimedia Software
---

### Post by spandanj on 2008-12-14
I just want to know what was the reason behind making a brand new audio organizer software, ie. banshee, when gnome already had one, ie. rhythmbox?

Was it because of better programming language? Was it.......? I don't know?  But what was the reason to start from scratch instead of improving upon rhythmbox?

Did Banshee NEED to use Mono language make it? couldn't it have done just with GTK+? 

...Just curious

---

### Post by directhex on 2008-12-14
Nothing has "replaced" anything. There have always been, and always will be, buckets of alternatives for any given task.

Banshee evolved from an player called (if memory serves) Sonance, which was written, as with all Free Software apps, to scratch an itch - a developer said "I want a player with XYZ features, I want to write it in ABC language"

Your language shows a slight level of confusion though. GTK+ is a widget toolkit - Banshee uses GTK for its widgets. Mono is not a language, it's a framework - C# is the language. Did Banshee need to use C# instead of Rhythmbox's C? Any developer will tell you just how much quicker & easier it is to develop an app with an easy high-level language (like C#) instead of needing to do your malloc() by hand with a low-level language like C.

---

### Post by spandanj on 2008-12-14
I was just wondering because I thought Mono was somehow related to microsoft. and, I wondered why they used a Mono framework then? Mono is just the open source software to support closed source framework -- .net, ASP, Winform, etc. So, I don't like the fact that banshee is ultimately build on those windows protocols/framework via Mono. 

could they have not built all those features of Banshee in rhythmbox instead of building Banshee? eg. equalizer, good "currently playing" page.


I prefer to use a media player completely build in Free OSS languange thus stay true to Linux's promise. Adapting Microsoft's closed source framework via Mono to build a free open software, eg banshee, directly goes against that. 

Sadly, Banshee is better than Rhythmbox in several ways. I would like to stick with rhythmbox because it is the default Gnome media jukebox. But, it lacks features...urgh.

---

### Post by alternatealias on 2008-12-14
> **spandanj said:**
> I was just wondering because I thought Mono was somehow related to microsoft. and, I wondered why they used a Mono framework then? Mono is just the open source software to support closed source framework

The .NET framework is not closed source. The .NET framework and the C# language are ECMA and ISO standards (as are C and C++, for example).

> **spandanj said:**
>  -- .net, ASP, Winform, etc. So, I don't like the fact that banshee is ultimately build on those windows protocols/framework via Mono.

You need to stop listening to rubbish spread by misinformed individuals with an axe to grind.

> **spandanj said:**
> could they have not built all those features of Banshee in rhythmbox instead of building Banshee? eg. equalizer, good "currently playing" page.

Possibly, but maybe the Banshee author(s) didn't know about Rhythmbox when he started hi project. Or maybe he didn't like the architectural design of Rhythmbox's code. Or maybe he didn't like C and preferred C#. Who knows.

Why does linux have umpteen million email clients, text editors, etc?

Or, closer to home, why didn't the authors of the Tracker project join forces with the pre-existing Beagle project to make Beagle better instead of starting their own project?

I suspect for similar reasons that the Banshee developers started their own music player.

The "why" isn't important. What is important is that you have the freedom to choose which application you want to use and that you have the source code available under an agreeable license so that you can modify it to your heart's content.

> **spandanj said:**
> I prefer to use a media player completely build in Free OSS languange

There's no such thing as a Free OSS language. C was created by AT&T which was an "evil monopoly" at the time (still is, depending on who you ask).

> **spandanj said:**
> thus stay true to Linux's promise.

Linux's promise is that it is a Free and Open Source kernel. Mono's promise is that it is a Free and Open Source VM for .NET languages.

> **spandanj said:**
> Adapting Microsoft's closed source framework via Mono to build a free open software, eg banshee, directly goes against that.

Actually, it doesn't because your assumptions about it are wrong.

> **spandanj said:**
> Sadly, Banshee is better than Rhythmbox in several ways. I would like to stick with rhythmbox because it is the default Gnome media jukebox. But, it lacks features...urgh.

I, myself, prefer to use Banshee because I *personally* find it to be technically superior to Rhythmbox. The UI is more polished, it has more of the features I want, it's faster, etc.

As DirectHex above mentioned, one possible reason that Banshee is developed at a faster pace (and thus has more features) is because they are writing the application in a higher-level language (C#) which means that they don't have to manually manage memory allocation/deallocation which is a heavy burden, and becomes heavier the more complex the application gets.

Having just listened to the following podcast ( [http://herdingcode.com/?p=109](http://herdingcode.com/?p=109) ), it sounds to me that the Mono project was started for precisely this reason. Apparently the founder of the GNOME project (and later the Mono project) was unhappy with the amount of time that he and other GNOME developers were having to spend dealing with memory management issues and other issues prevalent in low-level programming languages and so started the Mono project so that developers would have the option of using a simpler language, thus being able to produce better quality applications in less time.

---

### Post by spandanj on 2008-12-14
hey AlternateAlias,

thanks for clearing things up for me. I really appreciate your help. Especially the radio podcast

Now, I am not so sad about using Banshee, anymore.

As for which applications to choose from, eg. banshee or rhythmbox, or beagle or tracker, I hope Ubuntu, as a distro, will make a better choice for me, so I don't have to.

---

### Post by alternatealias on 2008-12-14
Glad to be of help :-)

---

### Post by directhex on 2008-12-14
> **spandanj said:**
> As for which applications to choose from, eg. banshee or rhythmbox, or beagle or tracker, I hope Ubuntu, as a distro, will make a better choice for me, so I don't have to.

Which it does do. Ubuntu used to use Beagle - it was replaced by Tracker as Tracker was superior (though Beagle exists as an alternative). Ubuntu has always used Rhythmbox, and the Desktop Team are the ones who would make a decision about changing that default

---

