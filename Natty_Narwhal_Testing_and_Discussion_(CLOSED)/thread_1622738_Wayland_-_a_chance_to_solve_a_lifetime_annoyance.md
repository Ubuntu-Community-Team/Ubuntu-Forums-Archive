---
title: "Wayland - a chance to solve a lifetime annoyance?"
date: 2010-11-15
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by muze4life on 2010-11-15
Hi,
One of the long-time annoyances of a Linux distro is that the clipboard is dropped (cleaned up) once the user closes the app (only exception is gedit, probably uses some workaround).

People eventually realised that this needs to be fixed but never agreed upon who must take care of the clipboard - the X server or the (Linux) kernel - hence this annoyance is set to exist forever.

Some people worked around this issue by creating tools that work around it, some of them work more or less good (parcellite), some less so.

Since Wayland is not burdened by backwards compatibility (afaik nor by the X protocol) - would Canonical try to get the Wayland devs to get Wayland to take care of the clipboard to solve this issue once and for all please?

---

### Post by seeker5528 on 2010-11-15
> **muze4life said:**
> Hi,
One of the long-time annoyances of a Linux distro is that the clipboard is dropped (cleaned up) once the user closes the app (only exception is gedit, probably uses some workaround).

The clipboard works fine and as it was designed to work for those of us that don't want a clipboard history with potentially sensitive information hanging around. The real annoyance has been that not all copy and paste methods work with all programs. In some you might not be able to use the middle click, in some you might not be able to use 'Ctrl'+'C'/'Ctrl'+'V' and in others you might not be able to use the context menu to select copy/paste.

If you want extended clipboard features, then install a clipboard manager. Klipper has worked pretty good for some time, some purists may not want to install it in Gnome, but it works fine there too. Don't know about the Gnome/GTK eqivalents. 

Later, Seeker

---

### Post by muze4life on 2010-11-15
On a desktop OS common sense implies that almost always (like 99.9% of the time) the user does want and expect the clipboard to stay after the app is closed.
Those who operate sensitive stuff on a shared computer **and** keep "the sensitive information" in the clipboard are a (very) tiny minority hence **they**'re supposed to do workaround stuff, not the overwhelming majority, that's fair and common sense.

---

### Post by Decatf on 2010-11-15
Wayland is a chance to solve a lot of problems..

Security isn't any reason at all for having broken functionality like this. If there was really some sensitive data on the clipboard it either shouldn't have been allowed to be copied like that or the user should be provided a warning/prompt about it.

---

### Post by aysiu on 2010-11-15
> **muze4life said:**
> On a desktop OS common sense implies that almost always (like 99.9% of the time) the user does want and expect the clipboard to stay after the app is closed.
Those who operate sensitive stuff on a shared computer **and** keep "the sensitive information" in the clipboard are a (very) tiny minority hence **they**'re supposed to do workaround stuff, not the overwhelming majority, that's fair and common sense.
This approach makes much more sense.

**Not sensible**
[list][*]Clipboard by default remembers nothing once you quit the application
[*]Almost everyone has to use some helper application like Klipper to workaround
[*]The tiny minority of Linux desktop users who work with sensitive material that can't be left in the clipboard are happy with the defaults.[/list]

**Sensible**
[list][*]Clipboard by default remembers what you copied into it even after you close the application[*]The vast majority of desktop users are happy with this default and expect this behavior that is standard in Windows and Mac[*]The tiny minority of people who want the clipboard erased can have a workaround application that deletes clipboard history when you close the source app.[/list]

---

### Post by krazyd on 2010-11-15
> **muze4life said:**
> Hi,
One of the long-time annoyances of a Linux distro is that the clipboard is dropped (cleaned up) once the user closes the app (only exception is gedit, probably uses some workaround).

Must be a bug in Gnome. Works fine in KDE.

---

### Post by muze4life on 2010-11-15
> **krazyd said:**
> Must be a bug in Gnome. Works fine in KDE.
No, KDE by default ships with Klipper which is KDE's workaround for this issue. Gnome usually doesn't ship with an workaround. For those who use Gnome I'd suggest installing "parcellite" to solve this annoyance (Mint's Gnome ships with it installed, Ubuntu's Gnome doesn't).

---

### Post by kyleabaker on 2010-11-15
> **muze4life said:**
> No, KDE by default ships with Klipper which is KDE's workaround for this issue. Gnome usually doesn't ship with an workaround. For those who use Gnome I'd suggest installing "parcellite" to solve this annoyance (Mint's Gnome ships with it installed, Ubuntu's Gnome doesn't).

This has also annoyed me for years. It never annoyed me enough to look into a solution, but thanks for the tip, I'll be giving parcellite a try.

---

### Post by krazyd on 2010-11-16
> **aysiu said:**
> Almost everyone has to use some helper application like Klipper to workaround
why is this not sensible? I think that having a clipboard manager provides the opportunity for extending the clipboard beyond simple copy+paste (scriptable actions etc.)

It also makes it very simple to provide all the features you listed under "sensible".

I really don't see why having a clipboard manager is such an issue.

---

### Post by zika on 2010-11-16
> **muze4life said:**
> No, KDE by default ships with Klipper which is KDE's workaround for this issue. Gnome usually doesn't ship with an workaround. For those who use Gnome I'd suggest installing "parcellite" to solve this annoyance (Mint's Gnome ships with it installed, Ubuntu's Gnome doesn't).
Thank You, very much, indeed, for this tip about parcellite. This situation bite me so much times but I've, never, decided to explore it more... Great!

---

### Post by slooksterpsv on 2010-11-16
> **zika said:**
> Thank You, very much, indeed, for this tip about parcellite. This situation bite me so much times but I've, never, decided to explore it more... Great!

You and me both, especially when I'd copy the page I was at on Chrome or Firefox, close the app cause I needed to switch browsers and find it wouldn't paste. Glad to know.

---

### Post by chrisccoulson on 2010-11-16
GNOME has gnome-settings-daemon, which already has a clipboard plugin (and has had this for ages) to implement a clipboard manager. This works for most applications, but is known to not work in Firefox (although it does work in FF4.0).

I can't see how Wayland would help fix this though. If anything, it would be worse as there would be nowhere for applications to store clipboard contents once they close

---

### Post by cariboo on 2010-11-16
I personally don't have a problem with copy-pasta, maybe I've been using a Linux variant for so long, that I've changed my habits enough so that this doesn't affect me.

---

### Post by tretle on 2010-11-16
Agreed, wayland is not a place to throw a clipboard fix. Its supposed to be a lightweight replacent for the x windowing system. 
As a side note I would like to state that I cringe every time I hear the statistic of 99.9% and "not sensible" used in the same post. 
It screams assumption to me and implementing fixes based on assumptions is a bad idea.
Would be nice if there was a standard for aggregating application interaction information anonymously so that the ux team could help advise projects based on real statistics.
Even then I doubt they would come accross the infamous 99.9 .

---

### Post by psusi on 2010-11-16
Yea, this isn't a Wayland issue, it is a gnome doesn't have a (working) clipboard manager issue.

---

### Post by muze4life on 2010-11-16
> **chrisccoulson said:**
> GNOME has gnome-settings-daemon
Which is what I'm talking about, the users and devs need a decent and unified desktop implementation of the clipboard API, there's nothing new about it,  Mac and Windows already work this way and people are happy. The current implementation in X is broken by design, and Gnome and KDE use different solutions/APIs for this problem, so no wonder that many apps don't support copy/paste as expected by the vast majority because of the fragmentation of the solutions to this problem **so these apps simply use the crippled implementation from X**.
We, the Linux users (and devs), should stop defending stop-gap decisions and fragmentation for stuff that is used that often, this call is mostly directed at "Linux fans" since they're typically so protective that they would defend even bad decisions as virtues just not to admit a (design/usability) problem in the Linux distros.
It must be implemented somewhere and doing it in Wayland would be relatively easy since it's a new project and geared explicitly towards a _modern (Linux) desktop_ and I do think that it would fit there well and it of course would not make it bloated.

---

### Post by cariboo on 2010-11-16
If you want this perceived problem fixed, go to where you will do the most good. I would suggest [this]("http://mail.gnome.org/mailman/listinfo/desktop-devel-list") would be a good place to start.

---

### Post by Mr. Picklesworth on 2010-11-16
Sarah Strong worked on this for her Summer of Code project this year. Pretty good blog posts on it here:

[http://sarahestrong.blogspot.com/2010/05/gearing-up-for-gsoc-clipboard.html](http://sarahestrong.blogspot.com/2010/05/gearing-up-for-gsoc-clipboard.html)

[http://sarahestrong.blogspot.com/2010/06/clipboard-managers-for-ubuntu.html](http://sarahestrong.blogspot.com/2010/06/clipboard-managers-for-ubuntu.html)

The reason gedit works is because it conforms to the [Clipboard Manager specification]("http://www.freedesktop.org/wiki/ClipboardManager"). The problem with just blindly tossing in something like Glipper by default is that the clipboard stuff is actually quite intricate. When you paste an item, the target application communicates with the source and chooses from a selection of different formats (plain text? straight image data? a list of URIs?). Similar to drag & drop. It's why the two, when they work, work so well.

There is a lot of stuff that we need to be really careful not to break :)

---

### Post by psusi on 2010-11-16
> **muze4life said:**
> The current implementation in X is broken by design, and Gnome and KDE use different solutions/APIs for this problem

No it is not, and no they don't.  The API is very similar to the one Windows uses too, the only difference is that Windows comes with a built in clipboard manager that takes over simple data like text when the application owning the clipboard exits.

---

### Post by muze4life on 2010-11-16
> **psusi said:**
> No it is not, and no they don't.  The API is very similar to the one Windows uses too, the only difference is that Windows comes with a built in clipboard manager that takes over simple data like text when the application owning the clipboard exits.
Of course it is crippled since it doesn't behave as most users would expect (as on Mac and windows) - or is that not a fact either? If so, then you're obviously not serious.
Of course they do, for example Gnome uses a daemon as told above (for devs) etc.

---

### Post by Giant Speck on 2010-11-16
> **seeker5528 said:**
> The clipboard works fine and as it was designed to work for those of us that don't want a clipboard history with potentially sensitive information hanging around. The real annoyance has been that not all copy and paste methods work with all programs. In some you might not be able to use the middle click, in some you might not be able to use 'Ctrl'+'C'/'Ctrl'+'V' and in others you might not be able to use the context menu to select copy/paste.

If you want extended clipboard features, then install a clipboard manager. Klipper has worked pretty good for some time, some purists may not want to install it in Gnome, but it works fine there too. Don't know about the Gnome/GTK eqivalents. 

Later, Seeker

The European Union should fine Microsoft for bundling a clipboard manager with Windows.

---

### Post by psusi on 2010-11-16
> **muze4life said:**
> Of course it is crippled since it doesn't behave as most users would expect (as on Mac and windows)

Because you don't have a clipboard manager installed, not because there is anything wrong with the api.

---

### Post by robert shearer on 2010-11-16
> **seeker5528 said:**
> 
If you want extended clipboard features, then install a clipboard manager. Klipper has worked pretty good for some time, some purists may not want to install it in Gnome, but it works fine there too. Don't know about the Gnome/GTK eqivalents. 

Later, Seeker


**Glipper** for Gnome.
( It has to be installed then log out and back in then right click on any panel and add it from the 'add to panel' menu.)

---

### Post by muze4life on 2010-11-16
> **psusi said:**
> Because you don't have a clipboard manager installed, not because there is anything wrong with the api.
This is getting funny, will you use another type dialectics next time?
No, the design is actually bad (choose your metaphor at will, or some euphemism if you think it doesn't sound pretty) because the contents of the clipboard are designed to get lost after the app is closed which is not what most desktop users want, in fact, it's what most desktop users don't want.

---

### Post by ranch hand on 2010-11-16
> **muze4life said:**
> Of course it is crippled since it doesn't behave as most users would expect (as on Mac and windows) - or is that not a fact either? If so, then you're obviously not serious.
Of course they do, for example Gnome uses a daemon as told above (for devs) etc.
Why not turn this argument around and realize that Mac and Windows are broken because they do not work the same as Gnome?

---

### Post by muze4life on 2010-11-16
Because, as you know but pretend not to know (probably just to argue a bit around) that was a reminder that I'm not suggesting something out of the box and has nothing to do with the/your "It's not window$$ cliché" and that almost all of those people are happy with the way it works (unlike most of the Gnome users) and .. I won't bother explaining more since your aim is not to understand but to argue obviously.

---

### Post by aysiu on 2010-11-16
**How it should work**
Copy from application A
Quit application A
Alt-Tab to application B
Paste into application B

**How it should not work**
Copy from application A
Alt-Tab to application B
Paste into application B
Alt-Tab back to application A
Quit application A

See the extra step in there?

---

### Post by krazyd on 2010-11-17
> **aysiu said:**
> **How it works right now*:**
Copy from application A
Quit application A
Alt-Tab to application B
Paste into application B

FTFY.

*not applicable on a [buggy app/DE combo]("https://wiki.ubuntu.com/ClipboardPersistence#The%20state%20of%20things").

Funnily enough, the "official" fix is... to use a Clipboard Manager!

---

### Post by teh603 on 2010-11-17
> **ranch hand said:**
> Why not turn this argument around and realize that Mac and Windows are broken because they do not work the same as Gnome?Dunno, the old GEOS "clipping scrap" system works pretty much the same way as it does on the Mac and Windoze, too. The main difference was that the clipping scrap is a physical file on the root level, while its stored in memory elsewhere.

---

### Post by lean on 2010-11-17
Please people, get the facts straight.

ClipbardManager is now af freedesktop project. This means that both KDE and Gnome, and every body else who makes a desktop environment can support clipboard persistense in a standardised way. So an KDE program works in Gnome, and vica versa. NO NEED TO INSTALL ANYTHING EXTRA.

[http://www.freedesktop.org/wiki/ClipboardManager](http://www.freedesktop.org/wiki/ClipboardManager)

The problem is that some applications does not follow this specification, but only supports X's standard (and forgets when closed).

If a program does not work, it is a bug of that program and nothing else.
Firefox 3 does not support ClipboardManager specification, Firefox 4 does.

There is no magical solution, and none should be tried, since they would be inferior to the official way of doing things. Just submit bugs for the programs that have a problem, and keep informed that way.

---

### Post by mixmaster on 2010-11-17
Lol.  This is such a severe problem that, despite using linux since the days when you installed slackware off floppies, I'd never even noticed it.

My personal beef with the clipboard is that there are too many apps around which don't support mouse swipe/middle button paste and I don't suppose a clipboard manager is going to alleviate that problem.

---

### Post by cecilpierce on 2010-11-17
> **mixmaster said:**
> Lol.  This is such a severe problem that, despite using linux since the days when you installed slackware off floppies, I'd never even noticed it.


I remember those days to, still have Slackware 1.2 in a pile of junk !

Has any body got it going yet, I get segmentation fault and not much going on in the IRC channel.

---

### Post by cpmman on 2010-11-17
Some moons ago I had a plain text file called Natalie and she could remember anything and everything I chose to tell her with shift/arrow or ctrl/arrow and ctrl/c or ctrl/x and ctrl/v.  She didn't know about urls or graphics but then no-one else did either and she would happily copy herself onto a 5¼ floppy for a trip out of the office.

She moved on to greater things with GEM desktop but had to change allegiance when a Big Blue suitor used his club to beat competitors to death.  The copy/cut/paste became easier but still had the restriction of a single line memory so she survived - until M8 came along with text, graphics, url and other recognition features up to 25 items.

Linux offers so many alternatives (I now use Parcellite - which can also communicate with Natalie if needs must) but also QuickFox Notes which saves Natalie the bother of physical travel - indeed she thoroughly enjoys popping up any where in the world I happen to be.

Now ... (pause to remember an item not given to chosen memory bank) ... what was the problem again?

---

### Post by seeker5528 on 2010-11-17
> **muze4life said:**
> On a desktop OS common sense implies that almost always (like 99.9% of the time) the user does want and expect the clipboard to stay after the app is closed.
Those who operate sensitive stuff on a shared computer **and** keep "the sensitive information" in the clipboard are a (very) tiny minority hence **they**'re supposed to do workaround stuff, not the overwhelming majority, that's fair and common sense.

And by that logic the common sense solution would be to add a clipboard manager to the default set of OOB stuff.

Better to include extra functionality in an additional utility that can be easily removed from the start up applications, instead of fixing something that's not broken that would then require some obscure work around to disable.

I have no problem being required to disable/uninstall stuff that is included because it is considered generally desirable to the average person, having to resort to some obscure mechanism to do the disabling is another story. 

Later, Seeker

---

### Post by Reiger on 2010-11-17
Apparently the problem is that Xorg waits with copying until a paste is performed. So if the app quits then it must somehow save its clipboard contents so the data will still be available to the X subsystems.

Wayland is not going to be a replacement for X, as it's aim is to bridge a subset of X with display manager functionality in a much more lightweight package. In that philosophy the solution is to get on with the times and have a dedicated clipboard manager (as does Windows, OSX, KDE, Gnome proper...). You'll even get more usability as an added bonus (at least if you use the klipper model) as the user can explicitly select a piece from the history and paste it again.

---

### Post by robert shearer on 2010-11-17
> **Reiger said:**
>   You'll even get more usability as an added bonus (at least if you use the **klipper** model) as the user can explicitly select a piece from the history and paste it again.

As does **Glipper**.

---

### Post by tretle on 2010-11-17
Tbh I dont think you understand what the point of wayland is and what its actually replacing. 
No it doesn't make sense to just include any old fix related to the Linux desktop into Wayland purely because its a new project.
Yes, having such an attitude would lead Wayland to bloat very quickly. 
Last time I checked Firefox was a pain at integrating other elements of the desktop like the application dialog. 
Should we include an application dialog system with wayland purely because a certain application breaks the hig or should we as a community report the broken hig to the application developers in question and ask them to fix it. 
This proposal makes about as much sense as including the clipboard manager with Rhythmbox.
You characterise linux advocates as ignoring the problem when in reality they are showing you exactly where the problem resides.

---

### Post by ranch hand on 2010-11-18
> **tretle said:**
> Tbh I dont think you understand what the point of wayland is and what its actually replacing. 
No it doesn't make sense to just include any old fix related to the Linux desktop into Wayland purely because its a new project.
Yes, having such an attitude would lead Wayland to bloat very quickly. 
Last time I checked Firefox was a pain at integrating other elements of the desktop like the application dialog. 
Should we include an application dialog system with wayland purely because a certain application breaks the hig or should we as a community report the broken hig to the application developers in question and ask them to fix it. 
This proposal makes about as much sense as including the clipboard manager with Rhythmbox.
You characterise linux advocates as ignoring the problem when in reality they are showing you exactly where the problem resides.
My Gods, a clipboard manager for rhythmbox!!  Just what everyone needs.

Great idea.

---

