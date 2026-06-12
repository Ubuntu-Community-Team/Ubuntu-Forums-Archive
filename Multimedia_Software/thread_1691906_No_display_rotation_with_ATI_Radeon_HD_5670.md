---
title: "No display rotation with ATI Radeon HD 5670"
date: 2011-02-20
forum: Multimedia Software
---

### Post by meow9th on 2011-02-20
-- Short story --
After installing a new graphics card (ATI Radeon HD 5670), I find that when I attempt to rotate one of my displays, both go blank for a few seconds, then display the login screen.

-- Long story --
I have been happily using the open source ATI driver with onboard graphics since upgrading to Maverick. No issues whatsoever, easy dual-head set up with GUI (System -> Preferences -> Monitors).

I have two displays, of differing resolutions, and one is rotated 90 degrees. I do not clone my display, and so my workspace is extended across both monitors.

Then I tried to a discrete graphics card, HD 5670. I disabled my onboard graphics to prevent confusion. When Ubuntu loaded, the login screen was the same as it always is, but when I tried to log in, my monitors went blank for a few seconds, then I was presented with the login screen again.

I tried recovery mode, and when I chose failsafeX, my monitors went blank. I finally gave up waiting and tried something else.

I found that I could log into a console with no problem (either from recovery mode or from the normal log in screen).

I created a new user. When I logged in as the new user, I found that I could once again customize my dual-head set up in the GUI -- until I got to the rotation part. As soon as I tried to apply that change, my monitors went blank for a few seconds, then showed me the login screen.

I tried to rotate my display using xrandr in the terminal as well. Same thing. Blank, then login screen.

I know that HD 5670 is supported by the ati driver. I know that rotation is supported by the ati driver. I'm just mystified by how these two features can't seem to work together. What am I missing? :confused:

---

