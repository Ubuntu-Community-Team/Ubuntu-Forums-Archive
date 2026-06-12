---
title: "how to add system sound event?"
date: 2009-05-28
forum: Multimedia Software
---

### Post by timcredible on 2009-05-28
i'm running 9.04 jaunty, and would like to add a new system sound event (new-message), but can't figure out how to do that.  does anyone know?  also, with the system sounds, how do you listen to what the current sounds are?  i don't see a play button on system->preferences->sound.  thanks.

---

### Post by ben2talk on 2009-07-14
Hi - I'm a little confused that you don't see a play button on system->preferences->sound.

This icon should run gnome-sound-properties for you, and on my system there are two tabs, one for Devices and the other for Sounds.

There should be a fairly small triangle on the far right of each line... format is:

Alert sound................Filename..............|> (where |> is my badly drawn ascii play button)

Now the sound files are kept by default in /usr/share/sounds - but you can easily copy these to your home/user/sounds folder and edit them with audacity (there are some nice subtle kde sound effects which sound nice with 12db amplification and a bass boost)

If you click the play button and the sound is set to Default, then I find there quite often IS no sound - but the Alert sound and Desktop Login definitely work on mine.

I'll keep an eye open, I'm trying to add sounds myself - for example I used 'KDE-Window-Minimise' amplified for my 'magic lamp' minimise effect, but cannot add an equivalent sound for RESTORING the window - which is annoying. It sounds nice going down, but comes up quietly.

---

