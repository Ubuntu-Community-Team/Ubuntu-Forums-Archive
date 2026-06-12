---
title: "Docking and detecting external monitor"
date: 2008-07-13
forum: Multimedia Software
---

### Post by nickzeff on 2008-07-13
Here is my scenario, which I don't believe is that unusual:

I have a laptop (Dell D820) and a replication port with an external monitor attached.

When undocked and around the house, I use the laptop with a wireless connection.

However, there are plenty of times when I want to dock mid-session - perhaps the battery is low, I want the benefit of two displays or a wired network connection. If I slip the laptop onto the replication port, it should immediately allow me to use the laptop's LCD **and** the external monitor I have placed to the right.

This two screens setup works fine if I am docked at login since my xorg.conf has all the right info in it. But if I want to **dock mid-session**, it requires an X restart in order to set up my external monitor as a separate X screen. This is a pain in the rear end, since I nearly always have media playing and several applications open at the same time.

Now I hate to say it, but Windows just works. It works out that I docked, and turns on the second display since it can remember the config from when I was last docked. After about a year of Ubuntu, this is the only remaining thing that makes me nostalgic for Windows.

So... two questions:

[LIST]
[*]Is there any way to set up a docked and undocked X profile which allows me to at least manually switch the external screen on and off without an X restart? Bear in mind that I want a separate X screen NOT a cloned or twinview setup here.
[*]If this is not currently possible, what is stopping this from happening? I assume it is X server not supporting this, rather than a problem with my nVidia drivers (since Windows can do this). Does anyone know more about why this restriction exists? Is it something that would be difficult to develop without rewriting X or something?!!
[/LIST]

---

### Post by nickzeff on 2008-07-13
So I guess there isn't ;)

---

### Post by mindhaq on 2008-07-23
I have a D830 with an docking station and external monitor, and facing similar problems.

What works for me is nividia settings. It's not automatically, but at least it can detect and configure the external screen without restarting.

But using twinview (i.e. one big desktop across two screens) with this setup made me other problems, like when I dock off, I still have only half the desktop on the notebook screen, and starting programs (like nvidia settings) might be opened where I cannot reach them.

I really wonder why dual screen is still such an issue on linux. This worked flawlessly almost ten years ago with windows 98 and a Matrox video card...

---

### Post by nickzeff on 2008-10-08
A few months later, I worked it out!

Hurrah!

[http://ubuntuforums.org/showthread.php?t=940932](http://ubuntuforums.org/showthread.php?t=940932)

---

