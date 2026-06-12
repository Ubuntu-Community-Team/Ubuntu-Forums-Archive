---
title: "Lots of stuff crashing since upgrading to Natty"
date: 2010-11-28
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by El Rey de Todo on 2010-11-28
Hey guys, I've been having trouble with lots of stuff crashing since I upgraded to Natty a few weeks ago. I'm not sure what to do about it now, I've tried everything I can think of.

Symptoms:
* On login, most of my panel applets crash and ask if I want to reload
* Unit seems to crash. I didn't even realize it was scheduled to start up until it didn't crash once this morning.
* Sometimes the panel doesn't show up at all
* killall gnome-panel from command line seems to make everything work fine
* My window manager (all of them! compiz, metacity, mutter) seem to crash frequently, especially during window resizes from the bottom edge (why that edge?!). Restarting from the command line makes them work again for a while, but they'll crash again eventually.

Some facts about my install:
* The only non-default repo I have added currently is for VirtualBox
* I have tried creating a new user account, same/similar symptoms
* I used to have xorg-edgers at one time, but I have ppa-purge'd it since then
* I had the gnome3 ppa installed for a while, but the problem started before that. I think I have totally reverted those packages but I'm not positive.
* I haven't seen any stack traces on command line when my wm crashes. I've seen 

What can I do to try to isolate the problem? I don't even know which library is at fault, though it seems reasonable to suspect something underlying my entire graphics stack (gtk or glib?) based on the variety of apps which are crashing. What should I try to reinstall? Has anyone else had major crashing problems?

---

### Post by kaldor on 2010-11-28
This sort of thing is highly common and expected with a development release. I hope you didn't install it on a production machine!

This may not directly help your issue, but please consider reporting every bug you find. You can use *ubuntu-bug name* in the terminal to report issues with the specified package.

For example if you find a glitch with Firefox:

*ubuntu-bug firefox*

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by Penguin=) on 2010-11-28
Yeh don't worry they are coming up with a fix, OR a new version.
Like natty 2, so don't worry, it just means you will have to upgrade again...urrgghh, i hate doing that! =(

---

### Post by El Rey de Todo on 2010-11-29
To be clear, I'm not mad or angry. I know this is still in early alpha stage, and I upgraded being fully aware that there would be intermittent breakage. I'm mainly concerned because it's been two weeks now and I don't see anyone else saying "every time I boot my Natty box everything crashes!" That makes me think there's something wrong with just my install. As for reporting bugs, I don't know what to report against. It seems like *everything* is crashing, I don't know what package to report against...

---

### Post by deanjm1963 on 2010-11-29
The first alpha isn't out until the 2nd December ... what you've been using so far is "highly risky" ... and as it says ... use at your own risk. Once the alpha is out there should be things to look out for when submitting bug reports. If you're after a stable system, Natty in it's present state is not the way to go.

---

### Post by El Rey de Todo on 2010-11-29
Let me say this again, because it doesn't seem to be clear:

I KNEW WHAT I WAS GETTING IN TO.

I am not complaining. I'm asking for help figuring out what bug to report. I can't find any hints of the errors that are causing things to crash. My messages log is empty. ~/.xsession-errors has some warnings about glib assertion failures but nothing that really says what happened. Running a window manager from the command line doesn't tell me what went wrong when the WM eventually crashes.

I DON'T KNOW WHAT'S BROKEN SO I DON'T KNOW HOW TO REPORT IT BEING BROKEN.

---

### Post by deanjm1963 on 2010-11-29
There is nothing to report until the developers say "this is how it is, give us feedback, these are the problems" - once the first alpha arrives they will say what needs to be looked at ... until then ... 

> **El Rey de Todo said:**
> Let me say this again, because it doesn't seem to be clear:

I KNEW WHAT I WAS GETTING IN TO.

I am not complaining. I'm asking for help figuring out what bug to report. I can't find any hints of the errors that are causing things to crash. My messages log is empty. ~/.xsession-errors has some warnings about glib assertion failures but nothing that really says what happened. Running a window manager from the command line doesn't tell me what went wrong when the WM eventually crashes.

I DON'T KNOW WHAT'S BROKEN SO I DON'T KNOW HOW TO REPORT IT BEING BROKEN.

---

### Post by DougieFresh4U on 2010-11-29
Yes I know this is early in the testing and blah blah blah... :p
I to have the 'crashing ' that has been mentioned - reload clock and a couple of other things. 
Just waiting as I figure it will sort out eventually

---

### Post by cariboo on 2010-11-29
The indicators are the problem, I think we are all suffering from the same thing.

---

### Post by chrisccoulson on 2010-11-29
> **El Rey de Todo said:**
> * On login, most of my panel applets crash and ask if I want to reload


Install gnome-panel-bonobo to fix crashing panel applets

---

### Post by Quackers on 2010-11-29
> **chrisccoulson said:**
> Install gnome-panel-bonobo to fix crashing panel applets

Gnome-panel-bonobo is already installed in mine and panel apps still crash during boot. Killall gnome-panel usually sorts them out.
It only happens when compiz runs on mine.

---

### Post by El Rey de Todo on 2010-11-29
It's actually comforting to hear that other people are having this issue as well. I was starting to worry because I couldn't find a bug filed for this or a forum thread and it had been over two weeks. Even in early alpha I expect to see some conversation about crashing problems somewhere...

So next thing: are the ubuntu devs aware of this issue? If not I really do need to file a bug, but I don't know against what package still. If I assume the window manager crashing thing is separate from the panel applet crashing thing, maybe I should file against gnome-panel initially?

---

### Post by Quackers on 2010-11-29
In the last 10 minutes I have had some compiz updates. I have run them and rebooted, but still have the same issues. It's not a complaint, just an observation :-)
It may be worth trying them on your system.

---

### Post by garvinrick4 on 2010-11-29
I have decided to just remove my panel applets and make my own nm-applet in custom launcher and go with the flow. Seems to keep up and running and I got a wifi connection.

---

### Post by The Compiler on 2010-12-07
I ended up replacing nm-applet with indicator-network and connman, like described on [https://wiki.ubuntu.com/ConnMan/Installation](https://wiki.ubuntu.com/ConnMan/Installation)

It works like a charm now, my panel seems to be fine again and all applets seem to be back. indicator-network doesn't support everything yet (PEAP and stuff like that I suppose), but it's pretty okay, at least for a workaround.

Flo

---

### Post by kyleabaker on 2010-12-07
I just run "killall nm-applet" on startup since I'm connected via LAN. That fixes things for me. :D

---

