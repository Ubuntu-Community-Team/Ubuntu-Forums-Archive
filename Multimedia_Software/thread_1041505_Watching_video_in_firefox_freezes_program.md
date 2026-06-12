---
title: "Watching video in firefox freezes program"
date: 2009-01-16
forum: Multimedia Software
---

### Post by curiousnoob on 2009-01-16
Sometimes while watching streaming video through firefox the program will suddenly freeze forcing me to force quit firefox.  When I attempt to restart it I get an error message saying that I cannot because Firefox is already running and I have to restart the computer.  
This seems to happen randomly, though always after watching video, and I can not seem to narrow it down to a type of video format or even a certain piece of video.  
Has anyone heard of this/know a solution?

---

### Post by hikaricore on 2009-01-16
Anytime firefox won't close like this you can easily kill it from a terminal as such:
> kill -9 $(pidof firefox)
Or from the gnome system monitor, top, htop and a wide array of other process management titles.

Now on to the problem at hand:

-Tell us about your video hardware

-What drivers you have installed for it

-Are you using desktop effects or not

-Do you have any sound trouble at all (this could cause crashes as well)?

-What version of Ubuntu are you running?

-Please also post the output of the following:
> glxinfo | grep rendering

---

### Post by curiousnoob on 2009-01-16
-Tell us about your video hardware
[COLOR="Blue"][COLOR="Blue"]No video card.[/COLOR][/COLOR]

-What drivers you have installed for it
[COLOR="Blue"]No proprietary drivers installed.[/COLOR]

-Are you using desktop effects or not
[COLOR="Blue"]Visual Effects set to None.  All other themes and settings are at the Default.
[/COLOR]
-Do you have any sound trouble at all (this could cause crashes as well)?
[COLOR="Blue"]No sound trouble.[/COLOR]

-What version of Ubuntu are you running?
[COLOR="Blue"]Hardy Heron[/COLOR]

-Please also post the output of the following:glxinfo | grep rendering 
[COLOR="Blue"]direct rendering: Yes[/COLOR]

[COLOR="Blue"]It is a Dell Dimension 4550[/COLOR]

---

