---
title: "Album art driven music player/organizer"
date: 2007-07-28
forum: Multimedia &amp; Video
---

### Post by fwwarr on 2007-07-28
Hi

My first post! I've been using Ubuntu on and off since 6.10 but one of the reasons I still primarily boot windows is wmp11.

I've looked at an incredible number of Linux media players (Rhythmbox, Listen, Exaile, Amarok, Banshee, Songbird, and many others) but there doesn't seem to be a program that integrates album art into the media browser like Windows Media Player 11 does (or the new iTunes, I think). I find that it is much more enjoyable to browse my music collection by looking at album art rather than boring lists of names. It can also make it faster to find things as it is easier to quickly recognize an image than a textual string.

A few other things I look for in a media player are the ability to integrally display lyrics (not having to follow a link to them), possibility to queue tracks through drag and drop and save the "now playing" list as a playlist. Internet radio and podcast support would be nice too. Although these features are not as important to me as album art based browsing.

So, does anyone know an app that does this? (preferably a gtk app)

If not, I guess I could always make/modify one... although it seems plain wrong to make yet another linux media player as there are already so many that are so similar. Does anyone know of an app that could be "easily" modified to provide this functionality? I haven't looked at the source, but Rhythmbox's "browser" doesn't seem to be too tightly integrated with the rest of the gui. I've also thought that Songbird's html support may make adding an album art driven media browser easier. What do you think?

Many thanks,
Fred

---

### Post by jazzguitar247 on 2007-07-28
bump

---

### Post by KoRnholio on 2007-07-29
> **fwwarr said:**
> Hi

My first post! I've been using Ubuntu on and off since 6.10 but one of the reasons I still primarily boot windows is wmp11.

I've looked at an incredible number of Linux media players (Rhythmbox, Listen, Exaile, Amarok, Banshee, Songbird, and many others) but there doesn't seem to be a program that integrates album art into the media browser like Windows Media Player 11 does (or the new iTunes, I think). I find that it is much more enjoyable to browse my music collection by looking at album art rather than boring lists of names. It can also make it faster to find things as it is easier to quickly recognize an image than a textual string.


As far as I know, there's no Linux program that does this.

> 
A few other things I look for in a media player are the ability to integrally display lyrics (not having to follow a link to them), possibility to queue tracks through drag and drop and save the "now playing" list as a playlist. Internet radio and podcast support would be nice too. Although these features are not as important to me as album art based browsing.


Listen at least does the first two - its the only one I've seen that has lyrics+wikipedia integrated into an easily accessible tab.  I think many of them can queue tracks through drag+drop, as well as save a now playing list as a playlist, though I couldn't tell you for sure.  But if an album art-driven interface is a must, then I don't think any existing Linux music managers would be your thing.  But that's not to say something like that couldn't be in the pipeline for any of them.

> If not, I guess I could always make/modify one... although it seems plain wrong to make yet another linux media player as there are already so many that are so similar. Does anyone know of an app that could be "easily" modified to provide this functionality? I haven't looked at the source, but Rhythmbox's "browser" doesn't seem to be too tightly integrated with the rest of the gui. I've also thought that Songbird's html support may make adding an album art driven media browser easier. What do you think?

Certainly, modifying an existing one would be easiest.  You're right on Songbird, actually that strikes me as the music manager that is most likely to incorporate something like that.  I would look into that, maybe ask the devs if that's in planning - and then maybe make a decision on what you want to do.

---

### Post by bom28 on 2007-07-30
Well, it seems to be in the pipeline of my favorite player : gmusicbrowser. The latest ["devel" version]("http://squentin.free.fr/gmusicbrowser/devel.html") does this, though it isn't finished yet. See this [screenshot]("http://squentin.free.fr/gmusicbrowser/screenshots/songtree_example.png").
I think it does the other things you want except radio and podcast.
You may have to try a few of the "layouts" to find one you like or create one to your liking.

---

### Post by fwwarr on 2007-07-30
Thanks for the replies, interesting stuff.

gmusicbrowser seems very promising, the customizable layout  feature is awesome, and there seems to be many great things in the works! I'll see if I can make a layout that is perfect for me.

One thing I forgot to mention is the ability to deal with unprotected wma, which is the format I ripped most of my collection too, but hey, maybe it's time that I re-rip my whole collection to ogg or something. I thought that since gstreamer can read my wma files (with ugly plugins), gmusicbrowser would be able to manage them, but I guess there's an issue with reading the wma tag information.

By the way, I'm surprised I never found out about gmusicbrowser... it seems like a top notch music browser to me, I guess it's still largely in development though.

---

### Post by KoRnholio on 2007-07-30
I've never heard of gmusicbrowser either...it sound interesting.  Hopefully it keeps getting actively developed.

---

### Post by Ryoushi19 on 2007-07-30
Good point, the open source media players are, unfortunately lacking in the department of browsing by CD jacket, album artwork, or whatever you wish to call it.  But thanks to the fact that Linux is open source, anyone who read this can look at it and try their hand at fixing that.  ^.^

---

### Post by !nkubus on 2007-07-30
I've been searching for something like this. I tried gmusicbrowser a while ago, I was impress but also frustrated by this program. It's slow and it hangs a lot when play with it.

I hope the nexts version will be better :)

---

### Post by bom28 on 2007-07-31
> **!nkubus said:**
> I've been searching for something like this. I tried gmusicbrowser a while ago, I was impress but also frustrated by this program. It's slow and it hangs a lot when play with it.

I hope the nexts version will be better :)

I use it a lot, and I don't find it slow, apart from the initial scan. What did you find slow exactly ?
And I don't experience any hanging while playing either. Have you tried other audio backends (it can use gstreamer, mpg321/ogg123/flac123 or mplayer)

Maybe you should post your complaints on the gmusicbrowser forum if you want the next version to be better, because I haven't seen post complaining about speed or playback problems.

And I must say that although there is a lot of features in development, I find it very stable and usable.

---

### Post by timo1023 on 2007-08-01
Wow, thanks a lot for the rec, bom28! I've been looking for a good music organizer and this is perfect.

Thanks again.

EDIT: Looks awesome, too.
[http://i72.photobucket.com/albums/i180/timo1023/Screenshot-BluesMusicbyG.LoveSpecialSauce.png](http://i72.photobucket.com/albums/i180/timo1023/Screenshot-BluesMusicbyG.LoveSpecialSauce.png)

---

### Post by Bohlio on 2007-08-01
I started a thread a while ago asking if anyone knew anything about an opensource coverflow type media player... didnt really get any answers....
[Opensource Coverflow Thread]("http://ubuntuforums.org/showthread.php?t=473102&highlight=opensource+coverflow")

---

### Post by timo1023 on 2007-08-01
Bohlio:
[http://www.google.com/search?hl=en&q=banshee%20coverflow](http://www.google.com/search?hl=en&q=banshee%20coverflow)
Not really usable, but I haven't seen anything else that resembles what you're asking for.

---

### Post by paulg on 2007-08-01
[Muine]("http://muine-player.org/") is a very simple player with an album cover driven library. I often find it *too* simple but it does it's job. It's in one of the repositories.

---

### Post by !nkubus on 2007-08-02
> **timo1023 said:**
> Wow, thanks a lot for the rec, bom28! I've been looking for a good music organizer and this is perfect.

Thanks again.

EDIT: Looks awesome, too.
[http://i72.photobucket.com/albums/i180/timo1023/Screenshot-BluesMusicbyG.LoveSpecialSauce.png](http://i72.photobucket.com/albums/i180/timo1023/Screenshot-BluesMusicbyG.LoveSpecialSauce.png)

Wow can you post your layout file i'm not able to make it looks like this :)

Thanks

---

### Post by bom28 on 2007-08-03
> **!nkubus said:**
> Wow can you post your layout file i'm not able to make it looks like this :)


I think it's the "itunes like" layout with some panels hidden (by shrinking them completely), and the album list in mosaic mode (right click on it to change the mode).

---

### Post by Bohlio on 2007-10-02
I just found[JukeBox3D]("http://www.gnome-look.org/content/show.php/Jukebox3D?content=63113") that may be close to what I am looking for, Downloading it now...

---

