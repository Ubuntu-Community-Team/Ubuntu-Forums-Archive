---
title: "Dual Screen With Nvidia Working ... But Not So Great"
date: 2011-04-02
forum: Multimedia Software
---

### Post by jage on 2011-04-02
OK, I just want to head check that I'm not missing something.  For the record, I know there is Separate X Sessions, but I want to keep this about TwinView if possible since that's what I'm trying to use (for now anyway).

Lubuntu 10.10 with Nvidia GeForce FX 5500, dual monitors.
Nvidia Driver: 173.14.28

Main Monitor: 1680x1050
Secondary: 1440x900

As you can see they are different sizes.  With Twinview, the desktop is simply treated as one giant screen, 3120x1050.

The problem is this leaves deadspace of about 150 px x 1440 px in the smaller monitor.  That's approximately 2 full rows of desktop icons.

On top of the icons going into deadspace, windows attempt to spawn into open space, which means instead of being put on my primary, they often spawn with the window controls in the deadspace (*Question 1: can I make windows spawn on one screen?)

At one point I lost half of my panel, as it was in deadspace.  I did figure out how to manually set it to anchor on one side nd width == screen width, so I can have my lubuntu menu on the left and still see my clock on the right of the same screen.

The only mitigating solution I can find is to make the smaller screen pan (Advanced -> set pan to = height of larger window).  While I can now get to lost windows that spawned, the smaller screen pans when you move the mouse on the larger screen... it's already giving me a headache. (Question 2: is it possible to only pan on the smaller screen?)

Relative size and deadspace aside, when I fired up a game (Angry Dwarves) it treated both monitors as one large one, which means the board spawned split by both borders. (Question 3: can I force a game or whatever to use one screen without opening X Server Settings and turing off one monitor?)

Editing xorg.conf and putting resolutions in separately ("1680x1050 1440x900" one solution I read) locks the display into a blank screen which takes focus away from another x-session after a few seconds.  xorg has to be restored from backup using recovery on the CD (even when you repeatedly Alt-F2 to restore, the xorg.conf is locked.)

I've played with resolutions placement and everything, I can't come up with anything better than:
1) live with deadspace and open X Server Settings when panning is needed to recover something auto placed
2) modify panels to act like they belong in one screen.
3) open X Server Settings and shut down a monitor to play a game

I want to make sure I'm not missing anything OBVIOUS to everyone else- Something obvious with TwinView, Separate X Servers is something I am going to try and work on separately.  From most of the things I've read these are long standing complaints and people just live with them or buy other monitors.

So, (Question 4: Is there any better way to use TwinView than just "living with it"?)

Thanks!

---

