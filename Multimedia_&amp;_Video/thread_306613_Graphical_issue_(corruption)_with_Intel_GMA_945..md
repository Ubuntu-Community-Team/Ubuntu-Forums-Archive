---
title: "Graphical issue (corruption?) with Intel GMA 945."
date: 2006-11-25
forum: Multimedia &amp; Video
---

### Post by Antilles on 2006-11-25
I recently setup a dual-boot on my laptop with Ubuntu 6.10 and Windows XP Pro.  My laptop's graphics card is an Intel 945G which isn't supported by default at native resolution.  After installing 915resolution and editing xorg.conf to get my resolution to display properly, I eventually encountered a problem with the graphics where two sections of the screen would render the content of windows that are placed elsewhere.  By the time I noticed this I had no idea what triggered the behavior.  My description is not very good, so I took a couple screenshots (from the desktop to show it more easily, but it also occurs on top of other windows).

[img]http://astro.temple.edu/~tua59576/Screenshot.jpg[/img]
The main menu is open off to the left.

[img]http://astro.temple.edu/~tua59576/Screenshot2.jpg[/img]
A gThumb window is to the right.

The first time this occurred, I tried purging and reinstalling the 915resolution tool, but that didn't fix it (I have a feeling that removing this tool isn't the equivalent to removing/reinstalling a driver in Windows as I'd hoped it to be).  After that, I reinstalled Ubuntu as I couldn't find any fixes.  It has now shown up a second and third time.  The second time, a scratched/smudged DVD causes my system to lock up, and I had to hard boot.  After that reboot, I logged in and the same issue was present.  This current time, I can't figure out what the change is, the only thing I can think of is that I recently tried starting a Beryl session, where the Ubuntu splash screen refused to go away.

I searched to see if anyone else had encountered this issue, but until I registered 5 minutes ago, I wasn't able to view the attached images in the one [topic](http://www.ubuntuforums.org/showthread.php?t=246008) I thought might be related.  Now I can see that it's the same issue.

I've installed the OS three times due to this problem recurring, and I really don't want to do so again.  Especially as it seems that this will just return after a certain space of time.

---

### Post by hey560 on 2007-02-20
Hello Antilles,

I have the exact same problem as you. I think the other thread you pointed out is also the same issue.

It occurs every once in a while for me, which makes it very annoying. 1 in 3 reboots this problem will show up. I have attached a screenshot.

I have a Lenovo 3000 N100 with the Intel GMA 945 graphics chip set:
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)

Were you able to find a fix for this?  Is this a known bug?

-hey560

---

### Post by Antilles on 2007-02-27
Sorry, but I never found a fix.  I took a break from running Ubuntu due to the issue, actually.  When I saw you had responded, I was hoping that you had a solution.

No idea if this is a known bug, I had trouble coming up with search terms that would describe the situation adequately but I never came across a bug report.

---

### Post by hey560 on 2007-02-27
Thanks for your response.  I haven't been able to find a solution yet either.

I still use Ubuntu though since now the problem only happens every 1 in 10 reboots.

Anyone else have any insight into this problem?

---

### Post by hey560 on 2007-03-07
FYI there is a bug report on freedesktop.org for this bug:

[https://bugs.freedesktop.org/show_bug.cgi?id=9381](https://bugs.freedesktop.org/show_bug.cgi?id=9381)

I don't think it has been resolved yet. Check it out.

---

