---
title: "Live audio streaming daemon"
date: 2022-09-13
forum: Multimedia Software
---

### Post by prsjm3qf on 2022-09-13
For years I've been running icecast2 and darkice to live stream the audio input from a usb webcam on 12.04.
This works fine so long as I manually start darkice from the terminal in a graphical session.
However now I need this setup to work as a daemon when multiple users are using remote desktop sessions.
I can run darkice as a service and it does stream but it streams no input. I can't connect it to the mic without an X session.

so, I have a webcam and a standard microphone and I need to livestream audio from a headless server on ubuntu 20.04 in a way that 
is independent from user remote desktop and local desktop sessions.

I don't need to replicate/fix my current darkice setup. Anything that works will do.

Thanks for any advice. It's driving me nuts.

---

### Post by Autodave on 2022-09-13
Are you really running a 10 year old version of Ubuntu?  I doubt that anyone can or will be able to help you here.  Why are you running that old program and why have you not updated?

---

### Post by prsjm3qf on 2022-09-14
Moving from 12.04 involved a bunch of software re-writes that I didn't want to do.
But I'm updating now to 20.04 and I can't get darkice to work as a service on 20.04.
I wasn't particularly asking for help in detail (though I would appreciate it) so much as "does anyone know a better way of doing this?".
Surely there must be a better way.

---

