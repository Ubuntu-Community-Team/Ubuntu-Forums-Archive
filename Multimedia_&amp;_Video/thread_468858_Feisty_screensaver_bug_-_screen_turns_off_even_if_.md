---
title: "Feisty screensaver bug - screen turns off even if not allowed to"
date: 2007-06-09
forum: Multimedia &amp; Video
---

### Post by lacerda_sch on 2007-06-09
Hi guys!

I have a problem. I am using Feisty on an ATI Xpress200 with fglrx, XGL and Beryl. I have disabled turning off the screen in Power Management, and turned off the screensaver. I have even tried shutting down the gnome-screensaver process and not letting it start again, as described [in this bug]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/97251"). I have confirmed that it is not running.

Yet, after about 15-20 minutes, the screen turns off. This is extremely annoying for example when watching movies.

Any help would be greatly appreciated :)

--
lacerda

ps: sorry if a thread like this already exists, I checked but could not find anything.

---

### Post by KitChy on 2007-06-09
[http://ubuntuforums.org/showthread.php?t=468108](http://ubuntuforums.org/showthread.php?t=468108)

Exact same problem here! :-p

---

### Post by lacerda_sch on 2007-06-09
I basically think that the problem must be in the fglrx driver somewhere. It is definitely NOT in gnome-screensaver, or VLC. Kitchy, do you also have an ATI card?

---

### Post by jet2230 on 2007-06-09
yeh im having the same problem as well, its really annoying when watching movies, screen just goes blank after 10mins of non activity.

i have ATI x1250 + beryl running. if any1 has found solution to this pls post

---

### Post by KitChy on 2007-06-10
> **lacerda_sch said:**
> I basically think that the problem must be in the fglrx driver somewhere. It is definitely NOT in gnome-screensaver, or VLC. Kitchy, do you also have an ATI card?

Yeh I have an ATI x1800

---

### Post by lacerda_sch on 2007-06-11
Looks like nobody knows the answer. I am starting to get desperate. :( This seems like a small problem, but it completely screws up watching videos.

Should we report a bug or something?

---

### Post by lacerda_sch on 2007-06-12
AAARGH!

I've tried a hack to see if some process is using ACPI to turn the screen off, but I found nothing. Turns out there are lots of ways to turn the screen off, and ACPI is just one of them. The other way I found is the "radeontool" command.

Does anybody know a way that we could find out which process is turning the screen off, and fry that motherf..ker? :)

--
lacerda

---

### Post by lacerda_sch on 2007-06-13
All right guys, I might have found a solution to this problem.

After hacking around in fglrx and Xserver documentation, I found out that xorg.conf has options for DPMS control on monitors. This appears to be the one that is causing us problems.

Try editing your /etc/X11/xorg.conf and add the following lines:

> 
Section "ServerFlags"
	#other options can go here
	Option	    "BlankTime" "0"
	Option	    "StandbyTime" "0"
	Option	    "SuspendTime" "0"
	Option	    "OffTime" "0"
EndSection

This effectively disables power management on your monitor. Setting 

> Section "Monitor"
	#other options can go here
	Option	    "DPMS" "false"
EndSection

might also do the trick, I haven't tried.

This is of course a workaround, and a lame one at that (it is NOT a good thing that your monitor never turns off, I would like my laptop to turn monitor off when not watching a movie, and when not on AC power). But it apparently works. :KS

--
lacerda

---

### Post by jet2230 on 2007-06-13
yo lacerda_sch thanks dude, im gonna try this asap and will report my findings.

---

### Post by jet2230 on 2007-06-13
there was no Section "ServerFlags" in my xorg.conf, but there was Section "Monitor" with Option "DPMS" "true" -i just set it so "DPMS" "false", saved file restarted os problem fixed.

---

### Post by lacerda_sch on 2007-06-14
I think it also works to add the ServerFlags section. But I guess your version is more simple.

Glad I could help you :D

--
lacerda

---

### Post by jet2230 on 2007-06-18
> **lacerda_sch said:**
> I think it also works to add the ServerFlags section. But I guess your version is more simple.

Glad I could help you :D

--
lacerda

you are right, i did actually need to add the ServerFlags section - sorry for my previous post which is actually incorrect, i did not test it out properly and to my dismay the blank screen problem still remained. 

to fully resolve i had to add the ServerFlags section in my xorg.conf,

thanks again.

---

