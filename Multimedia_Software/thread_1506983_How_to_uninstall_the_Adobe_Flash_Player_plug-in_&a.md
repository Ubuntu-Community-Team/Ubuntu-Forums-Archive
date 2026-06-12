---
title: "How to uninstall the Adobe Flash Player plug-in &amp;  ActiveX control"
date: 2010-06-11
forum: Multimedia Software
---

### Post by u2rcrazy on 2010-06-11
[FONT=Impact][SIZE=3]Ubuntu 10.045 (Linux) and  Firefox 3.6.3  ~  How to uninstall the Adobe Flash Player plug-in &  ActiveX control [/SIZE][/FONT] 
In general Adobe needs to offer Ubuntu (Linux)  support, but it seems like they don't care.  Currently, I can't use Adobe flash Player to view You Tube video's.  I  followed the link (below) that is stated to help a user fix the problem:

Solve a Problem: The video won't play:
[http://www.google.com/support/]("http://www.google.com/support/youtube/bin/answer.py?answer=56115")[youtube/bin/answer.py?answer=]("http://www.google.com/support/youtube/bin/answer.py?answer=56115")[56115]("http://www.google.com/support/youtube/bin/answer.py?answer=56115")
 
 
I then saw  that Adobe suggested that I first needed to uninstall any older versions  of the Flash Player and then install the latest version of the Flash  player.  I clicked on the link find out how to uninstall it here:
How to uninstall the Adobe Flash Player  plug-in and ActiveX control
[http://kb2.adobe.com/cps/141/]("http://kb2.adobe.com/cps/141/tn_14157.html")[tn_14157.html]("http://kb2.adobe.com/cps/141/tn_14157.html")
 
They didn't  offer any help with Ubuntu 10.045 (or Linux in general).  


[LIST]
[*]Do you know how to uninstall The old Adobe Flash Player?
[*]Also, which new Plug-in should I install?  
I've seen many choices (see [http://get.adobe.com/flashplayer](http://get.adobe.com/flashplayer)), but no instructions are mentioned on which one I should choose or how to install it.
[/LIST]
Thanks in advance!!):P

---

### Post by djwglpuppy on 2010-06-11
Have you tried going into the Package Manager and search for Flash and then uninstall it there?

---

### Post by lovinglinux on 2010-06-11
ActiveX is a Windows thing, no need to worry about it.

Install [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins and install the proper flash version according to your browser architecture. 

If you don't use Firefox or prefer to fix the problem from command-line, then see the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by u2rcrazy on 2010-06-14
First, thank you both for your help.  

[djwglpuppy]("http://ubuntuforums.org/member.php?u=1093406"), I'm new and didn't know where I could uninstall programs like in Windows.  Know I know it sould go to Package Manager.  Thanks.

[lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), I installed your Flash Aid, and noticed your message that it will install the 32-bit version of the Plug-In because Adobe don't have a reliable 64-bit.  I'm assuming that this will be ok on my system, correct?  Do you know the ETA of a 64-bit Plug-in?  Thanks.  This took was a great help.

):P

---

### Post by lovinglinux on 2010-06-14
> **u2rcrazy said:**
> [lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), I installed your Flash Aid, and noticed your message that it will install the 32-bit version of the Plug-In because Adobe don't have a reliable 64-bit.  I'm assuming that this will be ok on my system, correct?  Do you know the ETA of a 64-bit Plug-in?  Thanks.  This took was a great help.

):P

No ETA. At the moment most people are very skeptical if they will indeed release it. You should be "fine" with the 32bit. If you experience problems with controls not being accessible then do this:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Add the following line before the last line of the file opened by the previous command:

```
export GDK_NATIVE_WINDOWS=1
```

Save and restart the browser.

---

### Post by u2rcrazy on 2010-06-14
Thank for the help.  I'm stilling having problems with Video Players on the following websites:  MSNBC.com, metacafe.com, youtube, FoxNews.com, break.com, mynews3.com, youtube.com (Note:  not when embedded in a website, but only when I go directly to youtube.com's page that the video resides on.  I.e, it will work on this page:  [http://www.infowars.com/democrat-congress-critter-assaults-student-journalist](http://www.infowars.com/democrat-congress-critter-assaults-student-journalist)   ,but not on youtube's page:  [http://www.youtube.com/watch#!v=v60oNUoHBYM]("http://www.youtube.com/watch#%21v=v60oNUoHBYM")), cbsnews.com, etc.  I have included some pictures (below) of these sites so you can see that is shown on the screen in the way of an error message and incomparability.

[ATTACH]160429[/ATTACH]

[ATTACH]160430[/ATTACH]

[ATTACH]160431[/ATTACH]

[ATTACH]160432[/ATTACH]

[ATTACH]160433[/ATTACH]


How do you suggest I should go about this?  :confused:

Bob

---

### Post by u2rcrazy on 2010-06-14
Also, here are some more screen shots of errors:

[ATTACH]160435[/ATTACH]

[ATTACH]160436[/ATTACH]

[ATTACH]160437[/ATTACH]

[ATTACH]160438[/ATTACH]



This last site uses some sort of animation that I think isn't a Flash plug-in.  What do you think I can do about this?


[ATTACH]160439[/ATTACH]

---

### Post by u2rcrazy on 2010-06-14
[lovinglinux]("http://ubuntuforums.org/member.php?u=649167"), never mind the above posts.  The funniest thing just happened.  Your Flash-Aid just ran (on it's own no less) and fixed ALL the problems (including the last animated plug-in on christianfinancialcu.com).  Sorry for bothering you with these posts.  

Everybody, I strongly suggest you run Lovinglinux's Flash-Aid.  It will really make things work great.  Nothing worked before now everything works!!  Thanks Lovinglinux!!

Sincerely,
Bob:guitar:

P.S. Now how can I change this thread to show that it's now solved?  :p

---

### Post by lovinglinux on 2010-06-14
It runs after you restart Firefox for the first time after installing the extension or after an extension update.

---

### Post by dangmc on 2010-10-15
Lovinglinux-thank you for flash-aid, it worked great to stop firefox (namaroka)3.6.12pre freezes when right clicking on embedded videos on Foxnews.com. (this also happened with firefox 3.6.10). Videos are now playing great; my only remaining issue is the pause-stop control doesn't work after video starts playing. I tried the hack you recommended in your earlier post-(gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer), but (export GDK_NATIVE_WINDOWS=1) is already present in this file. Any suggestions? thank you for your contributions.

running Ubuntu 10.10
amd_x64

---

### Post by lovinglinux on 2010-10-15
> **dangmc said:**
> Lovinglinux-thank you for flash-aid, it worked great to stop firefox (namaroka)3.6.12pre freezes when right clicking on embedded videos on Foxnews.com. (this also happened with firefox 3.6.10). Videos are now playing great; my only remaining issue is the pause-stop control doesn't work after video starts playing. I tried the hack you recommended in your earlier post-(gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer), but (export GDK_NATIVE_WINDOWS=1) is already present in this file. Any suggestions? thank you for your contributions.

running Ubuntu 10.10
amd_x64

Get the 64bit preview of flash. The latest version of FLASH-AID can install it.

---

### Post by dangmc on 2010-10-16
> **lovinglinux said:**
> Get the 64bit preview of flash. The latest version of FLASH-AID can install it.

I think that is the version installed by flash-aid.

---

### Post by lovinglinux on 2010-10-17
> **dangmc said:**
> I think that is the version installed by flash-aid.

You can install the 64bit preview version or the 32bit version from the repositories. It provides both options.

---

