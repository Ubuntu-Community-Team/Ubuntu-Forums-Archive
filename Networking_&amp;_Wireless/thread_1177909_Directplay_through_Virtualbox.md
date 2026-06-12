---
title: "Directplay through Virtualbox"
date: 2009-06-03
forum: Networking &amp; Wireless
---

### Post by pYrO1v1aniac on 2009-06-03
I'm at my wits end by now.

I've been trying to get directplay to work through Virtualbox so I could play Age of Empires 2 over IGZones. Wine's support for the game is too choppy for multiplayer. The game will launch and all other internet based activity works fine, however, as it is loading multiplayer it times out with an annoying 'Unable to join multiplayer game'.

I have tried forwarding ports, both to Virtualbox (192.168.1.5) and to Ubuntu (Identified as Owner-laptop in the NAT config menu).

I have tried Upnp. First enabled on the router, then on Windows XP, the router appeared for a moment, but when clicked, it vanished, no joy.

I have tried host-only networking, bridged networking, damn near everything everybody anywhere has recommended, and I'm still met with the same impossible screen, hence, my wits end.

Essential specs.
Host- 
Ubuntu 9.04, connected to
Netopia 2247-02 router using
Intellinet wireless G usb adapter

Guest-
Windows XP professional (black edition) running on
Virtualbox 2.2.4

PLEASE HELP.

---

### Post by pYrO1v1aniac on 2009-06-05
Bump for help

---

### Post by pYrO1v1aniac on 2009-06-05
Bump.

---

### Post by yaroto98 on 2009-06-05
If I were you i'd forget the direct play through virtual box and go back to Wine. Wine is notorious for releasing a new version, fixing 9 things and breaking 8. Often times you have to get the right version of Wine through their archives page, use winetricks to install some additional help, and after a few hours of banging your head, it'll start working perfectly. (in my experience)

---

### Post by yaroto98 on 2009-06-05
[Try the WineHQ site for this game]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=99")

---

### Post by pYrO1v1aniac on 2009-06-11
I've tried Wine, and yes, the game works in it, but anywhere there is a menu, or buttons to be pressed, it slugs down, making online multiplayer impossible, as the lobby screen is full of buttons, and therefore causes your latency to display as huge to other players, and you'll get booted every time. Then in game, any time you select a unit, or take any action that involves buttons, the game slows, making it unacceptible. 

It's not a huge issue, and the game isn't broken, so I doubt it's one they're going to fix.

---

