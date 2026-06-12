---
title: "Can MythBuntu easily detect shared folders?"
date: 2008-06-27
forum: Mythbuntu
---

### Post by tijmz on 2008-06-27
Hi there,

I'm currently thinking of building a MythBuntu box, but I'm not completely sure about what to expect of it. I am not that interested in using the TV tuner functionality, but I want to use it as a video/audio jukebox that is connected to the TV.

I've already found that it can work as a jukebox for locally stored media (and I figure it should be able to play video DVD's/audio CD's from a local optic drive just as easily), but for the setup I have in mind it is also important that it can fetch audio/video from folders shared on my home LAN.

Now the thing is these folders are unlikely to have a fixed path. On top of that, they will be stored on WinXP, Vista, OS/X and Hardy Heron machines. Can I still easily have MythBuntu scan the LAN for shared folders on startup under such circumstances? Can I have these folders then appear in the MythBuntu main menu in a clear way, so that people can have its content streamt to the MythBuntu box without too much hassle?

It's not a problem if I have to do a lot of tweaking to get such a thing working, but in the end the jukebox should be useable by pretty much anyone.

---

### Post by freymann on 2008-06-27
> **tijmz said:**
> 
Now the thing is these folders are unlikely to have a fixed path. On top of that, they will be stored on WinXP, Vista, OS/X and Hardy Heron machines. Can I still easily have MythBuntu scan the LAN for shared folders on startup under such circumstances? Can I have these folders then appear in the MythBuntu main menu in a clear way, so that people can have its content streamt to the MythBuntu box without too much hassle?


MythBuntu does not auto-discover shares on your LAN. Anything you'd do to access media on shares would have to be done manually, and if they are ever changing locations, you're in for some fun.

---

### Post by Joshua on 2008-06-27
I think samba has tools that you could use to scan for shared folders and then mount them somewhere, but as far as I know, you'd have to write some sort of program to do it automatically.  I think the other problem would be that in MythTV, you need to set up the directories before using it.  So you'd have to make sure that your program mounted everything in the same place every time.

---

### Post by tijmz on 2008-06-27
Thanks for the replies!

A bit of a shame that auto-detect won't work, but I guess I could convince my co-residents to drop their media files in fixed folders to ease things up. Or could I bypass this problem by using something else than MythBuntu (I'm also considering booting up Elisa under a light-weight installation)?

---

### Post by freymann on 2008-06-27
> **tijmz said:**
> Thanks for the replies!

A bit of a shame that auto-detect won't work, but I guess I could convince my co-residents to drop their media files in fixed folders to ease things up. Or could I bypass this problem by using something else than MythBuntu (I'm also considering booting up Elisa under a light-weight installation)?

 Just remember that Myth expects all music in one directory, all pictures in another directory, and videos in another directory. Your frontends must all map to the same directory structure. 

 This link may help:

[http://www.mythtv.org/wiki/index.php/Mediashares](http://www.mythtv.org/wiki/index.php/Mediashares)

 Alternatives?

 I can't believe I'm saying this, but [http://www.linuxmce.org/](http://www.linuxmce.org/) will do what you want. It will detect and catalog shares from anything on your internal network, but you must set it up with dual network cards with external/internal LAN. 

 In comparison, MythBuntu is much easier to set up. LinuxMCE may take you weeks or months, but LinuxMCE is more fun ;-)

---

### Post by tijmz on 2008-07-01
Thanks for the tip. I might check out LinuxMCE, but first I'll experiment some with [Elisa Media Center](http://elisa.fluendo.com/).

---

