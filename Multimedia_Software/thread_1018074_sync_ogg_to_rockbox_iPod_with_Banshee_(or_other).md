---
title: "sync ogg to rockbox iPod with Banshee (or other)"
date: 2008-12-21
forum: Multimedia Software
---

### Post by itix on 2008-12-21
I need to sync my ogg vorbis music to my iPod, but banshee says that the iPod doesn't support ogg, which it is absolutely right about... if we are talking about a regular iPod. This one however is loaded with rockbox, so I need Banshee to ignore the fact that it's ogg and sync anyways.

If that is not possible, I'd like to sync the ogg music in some other way.

---

### Post by cozmicharlie on 2008-12-22
I am not sure you can do that.  Rockbox makes your ipod behave as a normal file system outside the Apple firmware.  I tried it on Rythmbox, gtkpod and Amarok and no luck.  You may have to sync the files just as you would any other folder using something like Unison or rsync.  You could set up a script so whenever you plug in your ipod it automatically syncs with your music folder on your computer.

The only player that seems to recognize my Rockbox files on the Ipod is Songbird.  I did not try and sync but it does give the option.  You might try that.

You might be able to do it using playlists.

---

### Post by itix on 2008-12-22
Yeah, I think you might be right...

I managed to get the songs on to the iPod by creating a separate music directory and moving all the files there and then play them using the file browser feature.

Thank you for your reply though. I'll look into Unison and rsync. It would be nice to have automatic sync to the iPod.

---

### Post by cozmicharlie on 2008-12-22
I use a program called Quickstart.  It is very handy for easy back ups etc.  I noticed it did have an option for file sync so you may want to check it out.  Info here [http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work](http://lifehacker.com/5064373/quickstart-configures-your-ubuntu-system-without-terminal-work)

---

