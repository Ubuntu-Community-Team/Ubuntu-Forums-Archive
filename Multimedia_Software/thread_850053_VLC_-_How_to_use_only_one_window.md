---
title: "VLC - How to use only one window"
date: 2008-07-05
forum: Multimedia Software
---

### Post by TRANQU111TY on 2008-07-05
How can I get VLC to open up in the same window so that there is only one instance of VLC whenever I open up another video?

---

### Post by shirilover on 2008-07-05
Open the preferences, somewhere should be an option for 'allow only one running instance' and 'enqueue files in playlist'.

As I am using a nightly build, the location of these options may not be in the same place as the version you are using.

---

### Post by TRANQU111TY on 2008-07-05
I am using "VLC media player 0.8.6e Janus (wxWidgets interface)" and there does not seem to be an option anywhere, even with advanced options checked to allow only one instance of VLC.

Apparently it doesn't exist.

---

### Post by mc4man on 2008-07-05
It won't be available till 0.9x (or current nightly builds)

---

### Post by shirilover on 2008-07-05
Ok, in 0.8.6h
Go to Preferences, check advanced options.
In the tree, select advanced.
Check the box for 'Allow only one running instance' in performance options.

---

### Post by mc4man on 2008-07-05
Can you get 0.8.6h as a .deb or do you need to build it ?

---

### Post by Memes11 on 2009-01-26
Hello,

I up a bit this topic as I have the same problem, actually, not completely but really looking alike enough to be in the same thread.

I already setted up the option to allow only one instance and to enqueue. So, if I have VLC running, whenever  I select one or several files, they are enqueued in the same instance. The problem is when VLC is not running yet, if I select all my mp3 and hit enter, even though I changed the command line for the default app to use, I still have several instances.

Is there anybody to help me?

Thanks

---

### Post by Memes11 on 2009-01-26
This forum is magic, I posted then, retry to launch the MP3 several at the first time and.... it works:D... was I bad enough not to see it was working.

OK, to help some others, and maybe me next time I'll face the issue;), here is the command line I use for the default app to open the file. 

```
vlc --playlist-enqueue --one-instance --one-instance-when-started-from-file -Z -L
```

I guess, I will have to teach my system for every file type, but this is still to confirm.

If anybody thinks the code is too much, tell me, I'm interested.

---

### Post by Memes11 on 2009-01-26
Me again...

So, after some test, it seems that the code above works but not 100%

When I open a group of file, the first 2, 3 or 4 open in different instances while the rest of the group go together with the latest instances open, it is like if the system was too quick and so, VLC does not have time to say "hey, only one instance!!". For this one, I really do not know how to proceed. Does anyone know?

For info, I saw the problem with clips of 20-60Mo (mix of mkv, mpeg, avi, wmv...), on a system  core2Duo E6600, 5GB DDR2-800.

And what is strange is that it seems it does not do the same with a bunch of MP3 (smaller file though)

---

### Post by Memes11 on 2009-02-08
up

---

### Post by LewRockwellFAN on 2011-04-21
> **Memes11 said:**
>  . . .  here is the command line I use for the default app to open the file. 

```
vlc --playlist-enqueue --one-instance --one-instance-when-started-from-file -Z -L
```I guess, I will have to teach my system for every file type, but this is still to confirm.

Thanks! This works 100% for me. I put it into a nautilus custom action, and set VLC to ALLOW multiple instances. So if I just use the regular "open with vlc" I can open multiple instances, which I occasionally want to do, but if I open with the custom action, it loads any thing I point it at, will let me add one or several at a time, lets me add more entries to the playlist (how nice of vlc to use a word I can spell -- instead of que, quee, qeu, qeeu, quuee, whatever) of a running instance. I'm not sure what you mean about teaching your system about every file type. For me this will feed the vlc playlist any media file or files I throw at it. I got sidetracked into this area googling around trying to learn more about nautilus-custom-action and trying a tutorial that used enqueing to vlc as a (bad) example. This is one of maybe 4 or so approaches I've seen and the only one that works worth a darn for me. Not sure why you aren't getting quite as consistent a result. Maybe because you are running it from the command line while I'm using nautilus-custom-action. I'm using the 10.04 LTS, Lucid, 32 bit the VLC  is 1.0.6, goldeneye, installed from the repositories with Synaptic. Oh . . . I just noticed the date on these posts. I guess that is the effect of almost 3 years of progress. Anyway, it works fine now, if OP is still around or if anyone wants to try it. Hey, even if OP has moved on, this is worth bumping, cause it's fun.

> **shirilover said:**
> Ok, in 0.8.6h
Go to Preferences, check advanced options.
In the tree, select advanced.
Check the box for 'Allow only one running instance' in performance options.
That works, of course, but at the cost of having to go back in and change it any time you want to run multiple instances. Not a big deal perhaps, but annoying.

---

