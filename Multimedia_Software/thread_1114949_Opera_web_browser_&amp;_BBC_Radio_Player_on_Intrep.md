---
title: "Opera web browser &amp; BBC Radio Player on Intrepid"
date: 2009-04-03
forum: Multimedia Software
---

### Post by arrowhead on 2009-04-03
Hello,

I've installed Opera on Ubuntu Intrepid but I can't get the [BBC Radio Player]("http://www.bbc.co.uk/radio/") to work. When I click on any of the Listn Live links the player window opens but nothing plays. I think I have all of the right codes installed in Ubuntu because the player works in Firefox.

---

### Post by gandaran on 2009-04-03
> **arrowhead said:**
> Hello,

I've installed Opera on Ubuntu Intrepid but I can't get the [BBC Radio Player]("http://www.bbc.co.uk/radio/") to work. When I click on any of the Listn Live links the player window opens but nothing plays. I think I have all of the right codes installed in Ubuntu because the player works in Firefox.
which opera version do you have and which player plugin works with firefox?

---

### Post by arrowhead on 2009-04-03
I have Opera 9.64 installed and the browser plugin that is working in Firefox says this when the About menu option is clicked, "Totem Browser Plugin 2.24.3" followed by "Browser Plugin using GStreamer 0.10.21".
:-)

---

### Post by gandaran on 2009-04-03
> **arrowhead said:**
> I have Opera 9.64 installed and the browser plugin that is working in Firefox says this when the About menu option is clicked, "Totem Browser Plugin 2.24.3" followed by "Browser Plugin using GStreamer 0.10.21".
:-)
opera is a KDE browser so doesn't work with gtk applications (totem-plugin), install another player plugin like mozilla-mplayer plugin, mplayer is best for bbc site, choose open real video format if it asks you to choose between real video or windows media video on the bbc radio page.

---

### Post by arrowhead on 2009-04-03
Thank you very much gandaran, it worked \\:D/

I opened the Synaptic Package manager, selected the **mozilla-mplayer** to be installed and let Synaptic install it along with all of it's dependencies.

---

