---
title: "Rhythmbox problem"
date: 2010-07-29
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by thonuz on 2010-07-29
Cant find files added to music folder. Using rescan or update or reboot.

---

### Post by ranch hand on 2010-07-29
I think a little more information would be helpful here.

---

### Post by thonuz on 2010-07-29
Hey,

Basically I have been using Rhythmbox to listen to music, I rip my CDs there so I can listen to them on a play-list format is OGG default.
So After ripping CDs I can see them in the music folder but rhythmbox will not refresh and show them. I have tried adding folder and file and also.
In preferences: you have the folder to watch for new files. This never has worked for me.  
So I install Amarok instead again. and can see the new files rather than trying to fix it. 

Rebooting etc did not work. The first 2 cds contents were there I think. Still no new files, but I can open them and listen individually. Amarok has under tools: update collection -- if you have used it. Also in settings is "fully rescan" "watch collection" directory of folder and all that. none of these do anything. 
I had problem in Lucid for a while and they just showed up after a while...

SO can't seen new files in music apps.

---

### Post by ranch hand on 2010-07-29
Wow, I hope you run rhythmbox and file a bug on it.  I would actually file it on Amorak first, seeing as that is what you are using and then change the preferred app to rythmbox, reboot and file it again.

I would refer to the first bug in your comments on the second.

It really sounds like nautilus is not picking things up correctly too so I think I would file on that too.  I would mention both the music player bugs in the comments on this bug.

It may be mainly a nautilus problem but see how you get different results with different apps I would just file on all of them.

I have no trouble with rythmbox except that I would prefer it not to scan the library and have set it that way.  It scans it anyway, I just noticed it today.  I will be filing a bug on it later.

---

### Post by seeker5528 on 2010-07-29
When OGG Vorbis was the only OGG format, they just gave the files .ogg as the extension, now that there is a video format as well, the preferred Vorbis extension was changed to .oga to signify with the extension that it is an audio file.

Assuming when you ripped the files they got .oga as the extension, try renaming a few of the files so they have .ogg as the extension to see if they then get recognized.

If they do get recognized, then you should look for bugs relating to this and if they exist use the checkbox on the page to indicate you are affected by the bug. 

If you can't find any related bugs, then you should create a new bug report indicating the program doesn't recognize the OGG Vorbis files when they have .oga as the extension.

Later, Seeker

---

### Post by mc4man on 2010-07-29
Even though the norm is for rhythmbox to misbehave in some manner, atm seems ok in the 2 area's mentioned here.

Music -> import folder works fine as does edit -> prefs -> music and unchecking "watch my library..."

Both can be easily tested by removing all tracks, dir.'s ect. from rhythmbox and then adding a folder or unchecking the option and restarting rhythmbox. (*remove, not delete*

The default gstreamer profile for "CD Quality Lossy" (.ogg type) is to use .ogg

---

### Post by thonuz on 2010-07-29
Thanks ranchhand and others.

OK I have the 2 first cds (2 albums; 28 songs) I own as .ogg files in rhythmbox. I did this with soundconverter and since then had to install some extras to get them as MP3 on my android device. 
Just opening Amarok now I have about 28 albums and hundreds of songs. Unfortunately some of these are listed twice both as mp3 and.ogg. A different problem I always have because on playlists is its always listed 2X.

With Amarok I have to enter KDE wallet password is the only difference.

Back to rhythmbox i just did import folder and nothing. I do have tons of songs in a missing files folder but they point to a windows partition that is not mounted.

they are default as .ogg which is fine by me. 
I seem to have this on Lucid I think. Rhythmbox then I go to Amarok last time cause of duplicate entries--same story. Lucid no duplicate entries in Amarok though.

Anyway, I get worried when files don't seem to exist in an application.
I am wondering other than nautilus if it could be something with wallet system. I have kubuntu on here also.

Its interesting nonetheless..
Thanks

---

### Post by seeker5528 on 2010-07-29
> **thonuz said:**
> I seem to have this on Lucid I think. Rhythmbox go to Amarok last time cause of duplicate entries. Lucid no duplicate entries in Amarok.

In Amarok you will end up with as many duplicates as you have files that are tagged the same as far as Artist/Album/Track goes. It's case sensitive, so you could change the case somewhere, the album field for example, to separate them if you have the same tracks as OGG Vorbis and MP3. 

> I am wondering other than nautilus if it could be something with wallet system. I have kubuntu on here also.

I can't think of any reason why anything to do with the wallet would affect the situation. In Amarok, and I'm pretty sure it is the same with Rhythmbox, the wallet is only used to store your password for online services (Last FM for example) that you need to log in to.

Never noticed a problem with stuff that, like Rhythmbox, uses Gstreamer directly, but Amarok when using phonon-gtreamer has had issues picking stuff up if directories/files had spaces in the name and in some cases when special characters are used or some characters that are not native to English locales. It never seemed to crop up all that much with phonon-xine, phonon-vlc is pretty new still but I have not heard of any of these types of issues when phonon-vlc is being used either.

Later, Seeker

---

