---
title: "audio delays after a (very) long time"
date: 2010-04-11
forum: Multimedia Software
---

### Post by el_baby on 2010-04-11
Hi,

I have a problem with an "in-house" developed C++ application using [Allegro]("http://www.talula.demon.co.uk/allegro/") and running on ubuntu 8.04.

Our old machines are Intel Mac Mini with the complete desktop (gnome) installed and never had audio problems.

Lately we're startin to use industrial PCs made by [Acrosser]("http://www.acrosser.com/") and, since I wanted to clean-up our installation ('cause we don't need a desktop, only x.org and alsa) I changed the setup.

I made a basic installation using the [minimal CD]("https://help.ubuntu.com/community/Installation/MinimalCD") and adding x.org, alsa and a couple more things. Everything seemed to be fine.

However, if I let the application running for a **very** long time (say about 8 hours or more), the audio begins to show a delay of about half a second, that is, it starts about half a second *after* I see the action that triggers it. This audio delay does not stop or delay the application running... that is, the "play" we send to Allegro doesn't block our app.

This DOESN'T happen on the old Mac's with gnome even if they're running for days.

Now, if I'm on the new Acrosser experiencing the delay and pres ctrl-alt-F1 to switch to tty1 and then go back to the X display pressing ctrl-F7 without stopping the application, the delay is gone... I suspect that the console switch sends some kind of reset to the audio driver or something like that.

Question 1) Does anyone know how to send that kind of reset to the audio driver? (that is a "quick and dirty" solution)

Question 2) Does anyone has a clue about the actual root of the problem? (that is, how I really correct it)

TIA

---

