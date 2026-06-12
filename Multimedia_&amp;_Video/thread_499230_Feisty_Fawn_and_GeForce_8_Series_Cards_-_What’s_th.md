---
title: "Feisty Fawn and GeForce 8 Series Cards - What’s the deal?"
date: 2007-07-12
forum: Multimedia &amp; Video
---

### Post by ZeusABJ on 2007-07-12
Hey guys,

I'm having some issues with Feisty Fawn and my GeForce 8800GTS card and it seems like I'm not the only one. The only thing that frustrates me is the fact that its so hard to get a clear answer on what the state of this situation is. I know that if I enable the restricted nVidia driver I get the XServer equivalent of the BSOD and I have to revert to a previous backup of my Xorg.conf. Some other posts that i have read around here seem to indicate that the development team is aware of this issue and that it is earmarked as a bugfix for Gutsy Gibbon so does that mean I just need to wait for Gutsy?!

Also, one other thread I found *did* provide a solution in the form of Alberto Milone's Envy application. I ran Envy and it did install a driver without crashing X. The problem is the driver Envy installs seems to perform poorly on my system (even without Beryl, Compiz or desktop effects enabled). For example, when I click and drag the edges or windows to resize them they seem to "stutter". Enabling desktop effects or Beryl makes this "stutter" more apparent and it appears to be a framerate issue or something (like the system is bogged down). By contrast some other distros I've tried like OpenSuSE and PCLinux OS have given me a much smoother and fluid level of performance.

I really like the Ubuntu philosophy, community and general usability but I just seem to be continually plagued by these irritating video and performance issues. Why do the other distros seem to perform better? Equally frustrating is the fact that while these other distros seem to perform better (from a video standpoint) they just don't compare to Ubuntu when it comes to usability, so switching to one of them really isn't an option for me. I'm not trying to gripe or anything, I'm just wondering am I doing something wrong? I mean if these other distros run better for me, surely there must be some way to "tweak" Ubuntu to get the same level of performance.

I just can't be the only person facing these issues. Surely someone else has encountered them. Also given the number for GeForce 8 cards in circulation I'm *sure* the Ubuntu team has to be aware of these issues. If I need to wait for Gutsty then no problem! I'm patient. I just wish I could get a straight explanation on this issue without having to troll 40-50 forum posts for a casual comment about this that my or may not be true. Could someone PLEASE just tell me what the situation is with these newer cards?

BTW Alberto, if you read this I'm not dissing Envy. I would NEVER do such a thing. You are a *HUGE* asset to the community around here and I appreciate everything you do... even if your avatar is a little creepy...

:lolflag:

---

### Post by ZeusABJ on 2007-07-12
Surely someone must know whats going on with this issue. Am I missing something? Is there already a thread out there that answers my questions and I'm somehow not seeing it when I search?

---

### Post by dabl on 2007-07-12
Possibly the little breakthrough at the end of this thread could be helpful: [http://kubuntuforums.net/forums/index.php?topic=3084816.0](http://kubuntuforums.net/forums/index.php?topic=3084816.0)

:)

---

### Post by ZeusABJ on 2007-07-13
> **dabl said:**
> Possibly the little breakthrough at the end of this thread could be helpful: [http://kubuntuforums.net/forums/index.php?topic=3084816.0](http://kubuntuforums.net/forums/index.php?topic=3084816.0)

:)

Well thats something I suppose. It still doesn't explain why I seem to have "stuttering" with Ubuntu when I resize windows. Does anyone else have this problem?

---

### Post by ZeusABJ on 2007-07-13
Here, these are the bug reports I was talking about:

Feisty Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/121096](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/121096)

Gutsy Bug Report:
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/120943](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.22/+bug/120943)

Can anybody give me any sort of update on this or detail their GeForce 8 Series experiences?

---

### Post by Motoxrdude on 2007-07-13
post the out put of
```
glxinfo | grep direct
```

and run

```
glxgears
```
does the gears spin smoothly?

Btw, when you resize a window it will studder almost no matterw hat because it has to redraw the window almost constantly until you stop resizing it.

---

### Post by zekopeko on 2007-07-13
> **Motoxrdude said:**
> post the out put of
```
glxinfo | grep direct
```

and run

```
glxgears
```
does the gears spin smoothly?

Btw, when you resize a window it will studder almost no matterw hat because it has to redraw the window almost constantly until you stop resizing it.

he should try trevino's repos for compiz. 
i have only a NV6200 and with the default compiz in feisty it was kinda slow.
 installed the new 0.5 git version and everything is flying.

---

### Post by ZeusABJ on 2007-07-13
> **Motoxrdude said:**
> post the out put of
```
glxinfo | grep direct
```

and run

```
glxgears
```
does the gears spin smoothly?

Btw, when you resize a window it will studder almost no matterw hat because it has to redraw the window almost constantly until you stop resizing it.

*Sigh* yeah the gears are smooth. Code output was:

direct rendering: Yes

So it looks like everything is okay. I don't get it. Maybe its Gnome or Compiz. Maybe my Chipset driver are to blame. Its FUNCTIONAL, it just seems like something is getting bogged down somewhere. Other distros just seem to run "smoother" but none of them are as functional as Ubuntu. I don't know. Its frustrating. Maybe some future driver release will correct the issue. I just imaged this working setup so I'm going to try Kubuntu and see if its better. 

Thanks for the help!

---

### Post by ZeusABJ on 2007-07-13
> **zekopeko said:**
> he should try trevino's repos for compiz. 
i have only a NV6200 and with the default compiz in feisty it was kinda slow.
 installed the new 0.5 git version and everything is flying.

Thats an option. Where can I find these repos? Any online tutorials?

---

### Post by ZeusABJ on 2007-10-15
All I can say is "God Bless the Gutsy Gibbon"! Almost ALL my Video Card issues have been fixed in the upcoming 7.10 release! FANTASTIC job!!! 

Thanks so much Ubuntu team!

---

