---
title: "MythTV vs LinuxMCE"
date: 2008-04-03
forum: Multimedia &amp; Video
---

### Post by MarshyTheKid on 2008-04-03
I'm getting ready to install an OS on a box I want to use as a DVR and as a web server. The computer isn't lightning fast, I can't remember the speed. I was planning on using MythTV to do this but I heard about LinuxMCE and wanted to hear opinions and whether I could run a webserver as well as a DVR with either distro.
Also how advanced of a video card do I need for a DVR?

---

### Post by kodiakcb on 2008-04-10
Will you be recording and watching tv on the same computer?  If so, you will need a more powerful cpu.  Go with PVR150,250,350 or 500 tv card and it will take some of the processing required because of the on board mpeg2 encoder. If you can, have two systems.  One can be your server and DVR while the other will be one you watch your media with.  

Both Mythtv and LMCE are setup so you can have a Backend server for the grunt work and a Frontend slave to do the pretty stuff(core and media director are the terms used for LMCE).  Both already use apache(web server) so that will already be installed. 

Both also will let you run everything on one system.  Just remember you will be hammering it from several directions.

Mythtv makes a pretty powerful and flexible media center type computer. LMCE, however, is much more.  LMCE combines your media, security and home automation into one and is really designed to be a whole house solution.  Which ever you choose, expect to spend a lot of time working on it to get it just the way you want.

Good Luck.

---

### Post by kodiakcb on 2008-04-10
I should also add that Mythtv has a larger support base and works with a lot more equipment where as the developers and users of LMCE seem to be trying to steer people to using certain equipment. This tends be similar to the Windows/Mac philosophy. Trying to be reliable with flexibility is a hard task and innovation tends to suffer(Mythtv)  While being innovative and reliable you have to deal with a narrower set of variables (LMCE)

While some may disagree with my assessment, the truth is only you will know which you will like better.  Try them both.  Download Knoppmyth (my favorite version of instant Mythtv install, just beware that it is based on Knoppix not ubuntu but it will give you an idea of functionality)  and LCME full install available at your convenient neighborhood torrent.  Install them in turn on a harddrive that you don't mind being erased and try them out.

Good luck

---

### Post by steefjeqv on 2008-04-10
Hi,

Nice poll.

I've voted "other", more specfically VDR.
Very nice OSD, lots of plugins, fully controlled by remote controller.

It's basically designed for (European-like) DVB use (Cable-Sat & Terrestrial) and is now included in LinuxMCE. It can also do analog TV and has (experimental) HD features. It has great network capabilities, so you can share media through your home network.

Bottom end : it turns your PC into a settop box and when you use hardware mpeg decoding (via cle266, dxr3, PVR350 or a FullFeatured DVB card) it can work with  a very limited hardware setup.

One drawback : the Ubuntu packages are not quite what they should be when you're setting up a soft-decoding mpeg system (xine based).
It works great on Debian though (with e-Tobi repository).

[http://www.linuxtv.org/vdrwiki/index.php/Main_Page]("http://www.linuxtv.org/vdrwiki/index.php/Main_Page")

Greetings,
Steven

---

### Post by DutchLoki on 2008-05-28
LinuxMCE versus MythTV???? I hope you know LinuxMCE is a MythTV distro with some extra stuff? 

LinuxMCE
Look nice in the video, but the on screen menu etc just does not work that nice in reallife. I personally would take an other MythTV menu structure than LinuxMCE uses. Good news... there are alot available and its easy to create one for yourself for MythTV.

Also the extra's LinuxMCE offers are for the most part also possible in the other MythTV-distros. Some are not, but are easy to install. Personally I don't want them on my system. 

VDR:
Great project, i'm a potential user when its more mature. Its fast, but not quit ready. 

MythTV distros
Have you looked at MythBuntu or MythDora yet? these two are the most populair MythTV distros, wel documented and wel supported.

---

