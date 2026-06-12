---
title: "Turning the display off"
date: 2009-12-21
forum: Mythbuntu
---

### Post by GuiGuy on 2009-12-21
On one of my frontends I'd like the display to turn off automatically after 20 or so minutes when no one is watching livetv, a movie etc. 

I have tried the power-management and screen saver approach but they switch off the display regardless of what might be playing. 

Any ideas?

---

### Post by Grenage on 2009-12-21
You're not alone, a lot of us are having problems with power management not being ignored, when watching a movie.  This only seems to affect 9.10, not 9.04.

---

### Post by GuiGuy on 2009-12-21
> **Grenage said:**
> You're not alone, a lot of us are having problems with power management not being ignored, when watching a movie.  This only seems to affect 9.10, not 9.04.

Thanks. I didn't realize there was another item to add to the list of 9.10's special new features ;)

---

### Post by GuiGuy on 2009-12-30
> **GuiGuy said:**
> On one of my frontends I'd like the display to turn off automatically after 20 or so minutes when no one is watching livetv, a movie etc.

[LIST=1]
[*]Make sure Xcfe 4 Power Manager is installed - Use synaptic to install it
[*]TURN ANY SCREEN SAVERS OFF!!
[*]Goto Applications > Settings >
[*]Start the Xcfe 4 Power Manager
[*]Click "On AC"
[*]Click the "Monitor" tab
[*]Slide the  "Put display to sleep when computer is inactive for:" to the left so it reads "Never"
[*]Slide "Switch off Display when computer is inactive for" to a preferred interval. I am using 20 minutes
[/LIST]

This now seems so work reliably with my Samsung 1080p 42" LCD/ HDMI display. The display is not triggered to off when watching live TV, but does turn off when frontend is on the menu screen for 20 minutes and nothing else is happening.

---

### Post by Grenage on 2009-12-31
Hey, Guiguy.

Thanks for letting me know about that, I will give it a whirl.

---

### Post by matt06 on 2010-01-06
> **GuiGuy said:**
> This now seems so work reliably with my Samsung 1080p 42" LCD/ HDMI display.

Works for me as well!  Thanks GuiGuy.

---

