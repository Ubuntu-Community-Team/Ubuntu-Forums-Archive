---
title: "TV showing us as projector... how to remove overscan?"
date: 2010-07-25
forum: Multimedia Software
---

### Post by smahnken on 2010-07-25
There's several threads dealing with overscan, but I've got an interesting twist in my setup that (I believe) is putting a kink into the proposed solutions.  

I'm trying to set up a media center PC with Ubuntu 10.~.  The motherboard has built-in ATI graphics (3300 series), and connects to my television (Panasonic capable of 1080i) via HDMI.  As can be expected, the overscan makes the top and bottom bars nearly invisible (as well as a portion of the sides).

When I run the Catalyst Control Center, it informs me that the monitor is a projector, not a TV.  Try as I might, I can't convince the thing it's attached to a TV.  When I run "aticonfig --tv-info", I am informed that a TV is not connected.

One question I could ask, though: does it matter?

The reason I'm asking is that I can't find the "Configuration" menu option in the CCC that all the other threads talk about.  I know where the little black triangle menu is, but there's no "Configuration" item in it.  There's also (as best as I can tell) no way of adjusting overscan for a digital projector.

So if anyone could tell me how to get the overscan options to show up (presumably they're still under the Configuration menu), I'd appreciate it.

---

### Post by smahnken on 2010-07-26
Another detail or two:

The television is an old-school HD utilizing a CRT, but the card says its a digital flat panel/projector (xrandr is using the identifier DFP2, and CCC shows a projector icon).  I'm assuming that's because it's connected via HDMI.

So given that the visible screen area is somewhat smaller, how does one restrict the desktop to only the visible area?

---

### Post by Gangrule on 2010-09-11
Hi All,

I have pretty much the same problem. My video card is a ati radeon HD 4800, connected to my monitor (DVI) and HDTV (HDMI). The TV is new, and supports upto 1080p. 

In windows7 i can edit the over-scan properties of the TV and make the image fit the screen within the Catatlyst control software. 

In Ubuntu 10.04, and Catalyst control software 10.8, my TV shows up as a projector (i don't know why it's not showing up as a TV), and there's no option to edit the overscan settings. Thus the TV image does not fill the screen which is annoying and not good for plasma TVs.

I've tried to use this command with no luck
xrandr --output DFP_EXTTMDS --scale 1.01x1.01

there's also an option with aticonfig, but i'm not sure i know how to use it.
aticonfig --DFP_EXTTMD -overscan=on

Any thoughts?

---

### Post by smurfik on 2010-12-05
Hi! I have the same problem:( Me TV is always recognised as a projector. Is there any solution please? (Ubuntu 10.10, ATI HD4330, FULL HD LCD Panasonic Viera TV)

---

### Post by musicleigh on 2011-06-02
I am also Experiencing a similar issue, Catalyst sees my Panasonic TV as a projector, this results in large black bands around the edge of my screen I have had this issue since 10.04 and am currently using 11.04

My TV is 1080P capable and is attached via HDMI.

Any solutions yet?

---

### Post by Crayoneater on 2012-01-25
I also have the same problem.  Is there a solution to this?

---

