---
title: "Intrepid - Machine Switches Net Connections For No Apparent Reason"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by N00bB00b on 2008-12-07
I've got Intrepid set up with a couple of net connections - home, work.  Work is set as the default.  For some reason, while I'm at home, Intrepid switches from the home connection to the work connection *on the fly* for no apparent reason, while I'm working on the machine.

Suggestions?

---

### Post by Iowan on 2008-12-08
Wired/wireless? 
DHCP/static?

---

### Post by N00bB00b on 2008-12-08
Wired.

The default (work) connection is static.  The alternate (home) connection is dynamic.

It's the dynamic connection that keeps reverting for some reason to the static one (while the dynamic connection is active, and operating).

It doesn't seem to do it at any particular time or for any particular reason.

---

### Post by Iowan on 2008-12-08
Curious - not the reply I expected.  I've seen other threads with the opposite problem - DHCP kicks in and overrides the static settings.  Since NM in Intrepid seems to have some issues with static addresses, that would have been expected.

How do you switch between the two?

---

### Post by N00bB00b on 2008-12-08
In the other cases, which is the default setting?  Again, in my case, the static setting is the default.

I switch using the NetworkManager Applet 0.7.0.

Yes, the change takes, and the net works - until it gets flopped.

Tonight - no flip.

---

### Post by bab1 on 2008-12-08
@N00bB00b,
I can't tell you what your specific problem is but maybe [[COLOR="Blue"]**this**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1004752") will shed some light.

@Iowan,
You'll find it interesting too.  I found the article the other day.

---

### Post by gTinker on 2008-12-09
[QUOTE=N00bB00b]
It doesn't seem to do it at any particular time or for any particular reason.[/QUOTE]

Are you absolutely sure that this doesn't happen something close to after the same amount of time that the system has been connected?

Say, for example, about the same amount of time as the lease time the router hands out for the connection? At that point, software that was running to try and always keep a connection active might get confused. I'm just guessing but it's easy to test, configure your router for a longer (or shorter) lease time and see if the issue tracks with that change.

---

### Post by N00bB00b on 2008-12-12
I just had it happen again.  I was screwing around, trying out Ekija Softphone.  When I quit, and then exited the widget in the menu, the net immediately switched.

---

