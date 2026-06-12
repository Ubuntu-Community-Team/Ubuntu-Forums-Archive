---
title: "HELP! Networking dead after 11.10 upgrade"
date: 2011-10-24
forum: Networking &amp; Wireless
---

### Post by JohnE1 on 2011-10-24
I've been offline for a week now and really need help to get this fixed. Having an update introduce such a major problem is a BIG snafu, to say the least.

Ping can't find anything but the local PC.

When I try to restart the networking service, I get error messages pointing to resolv.conf.

It turns out that resolv.conf is empty.

I'm guessing I have DNS client issues.

Suggestions, please?

TIA!

John

---

### Post by jameshedwards on 2011-10-26
I would try to edit the resolv.conf and add in your nameserver(s). the syntax is:

```

nameserver w.x.y.z

```

---

### Post by jonobr on 2011-10-26
try putting in
[http://74.125.224.81/](http://74.125.224.81/)
in your browser

if you get to google, all is ok, just your resolv.conf needs filling.
for a quick test you could put in

nameserver 8.8.8.8 to use a public dns
however your own device/router should be the resolv.conf ip address here.

If your using DHCP this should have been populated

---

### Post by JohnE1 on 2011-10-27
Thanks to all who tried to help. I tried editing resolv.conf and a valid DNS name server did not help. Without digging deep it appears that the upgrade and or subsequent update, did something to the DHCP client on my machine; maybe even removing it? I had a working system and have little time between work and sleep to troubleshoot and fix what Ubuntu broke.

For the following reasons I've decided to abandon Ubuntu and go to Fedora:

1. the upgrade breaking my networking was the final straw

2. the forced switch from GNOME to Unity (sure, I could monkey around to get back to GNOME, but that's bucking the path Ubuntu wants to force its users onto). Linux is about free choice, not forced choices.

3. Ubuntu 11.11 getting rid of Synaptic. Are you kidding?!?! Synaptic was the best package manager out there for Linux and you want to abandon it? Bad, bad, BAD decision!!!

4. Ubuntu's warning that 11.11 doesn't support older Intel on-board graphics. Abandoning one of Linux's strongest features of working on even older hardware. To abandon older hardware is a mistake. Almost all new PCs come with Windows. It makes sense that a LOT of Linux users have older PCs and don't want to continue throwing $$'s at MS for a closed operating system, so, they switch to Linux. Let me upgrade my hardware at my pace as my needs justify it.

One of the main reasons I ever used Linux is because it supports any and all hardware, especially older hardware that Windows chose to leave behind. Now Ubuntu is doing the same thing.

Unity is no GNOME; not even close. Where's my admin functions in Unity? I have to guess and search to find apps that were at my fingertips via a simple menu in GNOME. GNOME just works; if it ain't broke WHY fix it??!!!!!

GNOME has been stable for years and gives me easy access to Administrative functions via a GUI; these Admin functions I don't use often enough to remember all their shell commands and options, so GNOME has always been excellent for a full-time desktop user, part-time Admin, as needed.

Package management has always been one of the biggest weaknesses/issues with any Linux distro, and Ubuntu had the best solution with Synaptic. Now to see them abandon Synaptic with nothing equal that I could easily find through Unity, well, that just adds to my reasons to go elsewhere.

So far, Ubuntu has the best GUI printer support I've used, so I will miss that, but hopefully my replacement distro will also have an excellent printer manager/GUI interface.

I switched from CentOS (Red Hat based) to Ubuntu and was enjoying the fast debian package management and the nice printer management/support that Ubuntu had, but now there are more things I don't like about Ubuntu than things I like about it. Releasing an update that killed my networking was the final straw. If the solution to fix my broken Ubuntu is to download an .iso and make a LiveCD to fix the mess the upgrade created, then I'd rather spend my time making a LiveCD of a distro that won't kill my PC's O/S.

TO Ubuntu, you should have tested 11.11 more thoroughly, and not been so aggressive in making changes to something that worked. Give me a choice, just don't try and force me to do things "YOUR" way. That's not Linux freedom.

When all else fails, Red Hat works, period!!

Best regards,

JohnE1

---

### Post by jonobr on 2011-10-27
Sorry to see you go, but your talking/shouting at the wrong people here.

If your gas pedal sticks in your car, try screaming at toyota, not at the people helping you out of the car and trying to beat down the bent hood.


Respectfully.

---

