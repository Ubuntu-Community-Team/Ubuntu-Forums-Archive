---
title: "Line 6 Gearbox equivalent for Ubuntu?"
date: 2010-04-25
forum: Multimedia Software
---

### Post by CloudArchitect on 2010-04-25
Hey on windows I use cubase SE3 and Gearbox by line 6 to get stuff done, Gearbox is amazing and you can make some amazing stuff with it. The only problem is on ubuntu it doesn't really work or have native support..

So I was wondering if there are any equivalents for ubuntu? 

Also if you've heard of EZdrummer are there any linux equivalents also?

And they all need to work with Ardour :)

Thanks in advance

---

### Post by cb951303 on 2010-04-25
there is no real alternative. 
there are some ladspa plugins that simulate guitar amps and effects but to my ears they don't sound good.

but, guitar rig 3 and revalver mkII both works OK with wine.
(in fact revalver mkII uses wxwidgets as its gui toolkit.)
which are IMHO a lot better sounding then gearbox.

---

### Post by cchhrriiss121212 on 2010-04-25
> there is no real alternative. 
Thats sort of right but quite misleading. There is in fact a program called guitarix which does amp simulation and rakarrak which has effects, and these are not plugins. There isn't much need to use wine for audio production unless you have a huge vst library.
> Also if you've heard of EZdrummer are there any linux equivalents also?
Hydrogen is the best drum machine I have seen, as it is hugely tweekable and allows you to import and create your own drum kits. 
> And they all need to work with Ardour :smile:
This is not a problem with any jack based audio program, as they all are designed to connect through the jack server with low latency. I take it you have jack up and running?

Check out [this ppa]("http://ubuntuforums.org/showthread.php?t=1350304") for all this stuff in up to date versions. A lot of musicians come to ubuntu and the first instinct is to try and run everything through wine, which is understandable, but there are loads of professional quality packages out there.

In the future, try checking the ubuntu studio forum for audio and video production.

---

### Post by CloudArchitect on 2010-04-25
The only problem there is with guitar rig and wine is that I don't actually really want to use wine at all. If worst comes to worst I'll go and get it :)

I'm looking into hydrogen right now, it seems pretty damn nice. I'm downloading a ubuntu studio iso at the moment so when I get it I'll have a proper verdict on it.

And can guitarix do this? [http://www.soundclick.com/bands/page_songInfo.cfm?bandID=1045565&songID=8882543](http://www.soundclick.com/bands/page_songInfo.cfm?bandID=1045565&songID=8882543) - Something I did with gearbox EZdrummer and cubase on the setup I have at the moment. If it can make that tone for distortion then I'll download it really very very fast

---

