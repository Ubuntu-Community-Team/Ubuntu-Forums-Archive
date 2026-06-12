---
title: "VPN Weirdness."
date: 2010-10-29
forum: Networking &amp; Wireless
---

### Post by gfxguy on 2010-10-29
I've set up two accounts on my computer; one for "me," and one for "workme," as I often work from home connected via vpn, so let's say those are the usernames.  Notable is that workme has a low (below 1000) UID to match my UID at work, and that often causes weirdness in itself (for example, "switch user" won't show workme; on 9.x I could set options to display lower numbered users, but not on 10.04).

Ok, without making a long story, I've gotten to the point where this happens:

1. I log in as me.
2. I open a terminal and su to workme.
3. I start the vpn client and connect with no problems.
4. From the terminal I run mail, web, and editors, no problems.

I want to STRESS THIS POINT: This still works!  So I have a work around.

The problem is if I log DIRECTLY into "workme," get workme's desktop and everything else... only THEN will vnc fail with "no response from target."  It's not a fluke, I can repeat this all day.  There's obviously something running under the window manager, under gnome, something... that when I log in graphically is interfering with VPN.

If I want workme's desktop, there's a couple of ways... login as me, open the terminal and su to workme and start vpn, then switch user to workme to get workme's desktop being the simplest.

That's just ridiculous, though.

And it happens only when I'm running a gnome session... because I can't log in as workme, open a terminal to "me" and su back to workme... if the graphics from workme's session are on the screen, it simply doesn't work.

What could it be?  Probably some applet, right?  But which one?

Any help is appreciated.

---

