---
title: "Windows Media Player 11, am I even close to getting this to work?"
date: 2009-03-11
forum: Multimedia Software
---

### Post by lobes on 2009-03-11
I've been trying to get a windows program called media portal to work in ubuntu 8.10. heres a recap of what I've done:

Installed Wine
Installed MS .NET 2.0 framework from winetricks
I installed MS Visual C++ 2005 sp1 libraries and MS DirectX 9 user redistributable from winetricks.
I installed Media Portal 1.0
Media Portal requires Windows Media Player 11 and thats leading my issues at the moment.  

When I try to install Windows Media Player 11 it
passes authentication and starts to install then I get a generic error.  Nothing thats tells me why.  I have installed the following drivers into system32 folder; msxml3.dll, secur32.dll, winhttp.dll. well msxml3.dll was already there.  

No luck.  Any Ideas?  I am running 64 bit ubuntu but i dont think that would matter when using wine.

Any help is appreciated.

---

### Post by SunnyRabbiera on 2009-03-11
I dont think it will work, sorry to say.
This is why Microsoft sucks.
Wine and linux developers can only do so much without support, and it will be a cold day in hades Microsoft officially supports linux.
You have more of a chance of seeing a Rhinoceros fly.
Why is media portal important for you?
I would not use it anyhow, it probably is loaded down with DRM and Microsoft crap.

---

### Post by lobes on 2009-03-11
no way, media portal is hands down the best media center I've ever used.  And its open source which is a huge plus. I was using it in XP but I want to only use ubuntu.  If i could figure this out I would have no need for XP.  Man, i thought i was on the verge of something.  I'll keep messing with it, who knows. 

I installed these drivers too and the install did go farther before failing.
pdh.dll, odbcbcp.dll and gdiplus.dll

---

### Post by juppuk on 2009-03-11
this is for sunnyrabberia for starters microsoft does not suck if it did then people wouldnt be trying to use their programs on linux using wine and vmware. if its that bad off people advice like just use a different programwithout the slagging

---

### Post by lobes on 2009-03-11
well just to point out media portal is open source.  For some reason they wrote it in "C" and for windows.  I hate HATE Windows media player but its required.  but i guess im going to look into mythtv.

---

### Post by justsomedude on 2009-03-11
Check out xbmc:

[http://xbmc.org/](http://xbmc.org/)

Precompiled binaries for Ubuntu:

[http://xbmc.org/forum/showthread.php?p=185738](http://xbmc.org/forum/showthread.php?p=185738)

---

### Post by binbash on 2009-03-11
you should stop trying it.Move to XBMC

---

### Post by lovinglinux on 2009-03-11
If you need a full-featured Media Center, then try MythTV. I like [XBMC]("http://xbmc.org/"), which is great if you don't need to record TV (as far as I know, it doesn't record), there is also [Freevo]("http://www.freevo.org/") and Elisa.

Also take a look at my media center Firefox extension - [FoxMediaCenter]("http://fmc.isgreat.org/"). It has xmltv support, scheduled recordings, playlist manager, programme filtering and more.

For PVR comparisons - [http://en.wikipedia.org/wiki/Comparison_of_PVR_software_packages](http://en.wikipedia.org/wiki/Comparison_of_PVR_software_packages)

---

### Post by lobes on 2009-03-11
thanks for the sugestions, ill check them out. i really just want something that has a nice movie backup database.  Something that willconnect to [www.imdb.com](www.imdb.com) and pull all the infor for the movie.  Needs to be able to play iso.s, avi's, and most importantly Video_TS Folders.

---

### Post by lobes on 2009-03-11
so i decided to give xbmc a try but I must be doing something wrong.  I've aded the PPA's for XBMC Intrepid and for the XBMC add-ons and I've added the keys for them from [http://keyserver.pramberger.at](http://keyserver.pramberger.at)

now this i where my "newbness" shines..where do I get XBMC?  i assumed it would be under the add/remove programs---->third party programs but its not. somebody make me look stupid and help me out here. thanks in advance

EDIT: Nevermind, i made myself look stupid.  It was in synaptic, duh

---

