---
title: "Ati FPS POL - Edgy Eft"
date: 2006-12-15
forum: Multimedia &amp; Video
---

### Post by RudolfMDLT on 2006-12-15
Hi,

I am interested to see what FPS count people using Ati cards are getting in Edgy. More to the point, what percentage actually got the cards to work 100%. If your fps count is above 500 please do a quick post on what Ati card you are running and which drivers.

The tool I wish to use as a benchmark is glxgears, something simple that everyone with an Ati card should have installed.

Please run this command for a couple of seconds and do the poll, your input will be greatly appreciated!

[COLOR="Red"]glxgears -printfps[/COLOR]

Thanks,

Rudolf

---

### Post by RudolfMDLT on 2006-12-16
Ah well, so much for my POL...:-?

---

### Post by whatever on 2006-12-16
> **RudolfMDLT said:**
> The tool I wish to use as a benchmark is glxgears
wrong decision, glxgears is not suitable as benchmark tool.

---

### Post by RudolfMDLT on 2006-12-17
whatever,

Why would you say so? If  you know of something better, then please say so, I'm still wet behind the ears concerning these things and Linux in general. I thought it would be a basic tool to see how many users actually got the cards working and in what performance range this was. 

IF you would have set this up differently, how would you have set it up? 

Thanks man,

Rudolf

---

### Post by superm1 on 2006-12-17
Because there is a switch included in the app:

```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

It is good to see if 3D works on a box.  If you want to benchmark, use a 3D app like a game run in a demo mode.  UT2004, doom3 are both good candidates.  The Phoronix guys run tests on all ATI releases using these apps.

---

### Post by RudolfMDLT on 2006-12-17
Okay, but I still don't understand why it's not a good benchmark. If a better card gets a better FPS score than an older, less powerful card - Whats wrong with it as a benchmark? Sorry if I'm being finicky(full o'crap) but it doesn't make sence. 

Sure a game would be a good test, no argument there but isn't there a tool like "PassMark burn in" that is quick to download and simple to install that would be a good benchmarking tool. I wanted the Poll to be quick and effective. glxgears is quick but according to you'r and whatever's advice it not effective making the whole thing pointless.

I would still like to carry ou the Poll and start a new one. If you  or anyone could advice a pain free method for benchmarking a card I would be greatful.

Thank you,

Rudolf

---

### Post by superm1 on 2006-12-17
> **RudolfMDLT said:**
> Okay, but I still don't understand why it's not a good benchmark. If a better card gets a better FPS score than an older, less powerful card - Whats wrong with it as a benchmark? Sorry if I'm being finicky(full o'crap) but it doesn't make sence. 

Sure a game would be a good test, no argument there but isn't there a tool like "PassMark burn in" that is quick to download and simple to install that would be a good benchmarking tool. I wanted the Poll to be quick and effective. glxgears is quick but according to you'r and whatever's advice it not effective making the whole thing pointless.

I would still like to carry ou the Poll and start a new one. If you  or anyone could advice a pain free method for benchmarking a card I would be greatful.

Thank you,

Rudolf
Here is a better summary indicating why glxgears doesn't work as a benchmark from a variety of threads that have hacked this argument to death.
[http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark](http://wiki.cchtml.com/index.php/Glxgears_is_not_a_Benchmark)

So as it currently shows, there is no real *tool* that will give you information about the performance of your card like 3DMark for windows or anything.  If you really want to run a survey checking performance, find a demo of a decent 3D game.  Write a script that will download that demo from a website, extract it in the users home directory, run the games demo's demo mode and spit out a resultant number for the user to post to the forum.

---

### Post by RudolfMDLT on 2006-12-18
Thanks, that explained it very well! No more argument!

As for the scripting, it'll be a nice little holiday project as I know Jack-Nothing about scripting in Linux.

Thank you superm1

---

### Post by superm1 on 2006-12-18
> **RudolfMDLT said:**
> Thanks, that explained it very well! No more argument!

As for the scripting, it'll be a nice little holiday project as I know Jack-Nothing about scripting in Linux.

Thank you superm1

Great, looking forward to your test script.  I'll gladly be a candidate on multiple machines of mine :)

---

### Post by roachk71 on 2006-12-18
This computer is an HP Pavilion xt125 Notebook, with ATi IGP340M.

First Test: 1271 frames in 5.0 seconds = 253.694 FPS
Second: 859 frames in 5.0 seconds = 171.768 FPS

Not bad for a four-year-old computer!

My only graphics-related gripe is that the default screensaver GL rendering engine tends to slow to a drop-dead halt, so I simply use a blank screen for that. ](*,)

---

