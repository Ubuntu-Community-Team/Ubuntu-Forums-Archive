---
title: "ubuntu auto-update-related amarok playback problem"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by JarkaRuus on 2006-10-25
Hi all.  Here's the situation:



We installed Ubuntu 6.06.1 on our machine.  We are not linux professionals, but aren't quite neophytes either.



Installed Amarok and the dependent libs for it.  All worked well, xine-extracodecs worked fine, MP3 playback was great.



After this, something we haven't pinpointed got botched during [or was botched before] an auto-update and broke the boot to X feature, breaking simple login on the machine.  It was actually possible to login by starting X from the CLI but gnome would crash almost immediately, making it impossible to do anything short of ctrl+alt+backspace back to the CLI.



We eventually got X working sufficiently to run a single app, ran synaptic, and installed the Kubuntu components, login screen, &c.  After this we were capable once again of logging in properly through X in both KDE and gnome which apparently returned to normal.



The problem that has persisted since then is that when attempting to run Amarok, it refuses to play any of the library, giving the following error message:

     "No suitable demux plugin. This often means that the file format is not supported."



This seems a bit mysterious, since Amarok is set to use ALSA, which is installed, along with the XINE engine which is also installed with its extras.  We have tried forcing a reinstall of both, along with Amarok, to no avail.  The error persists.



The error also extends across other media apps that use the same libs.



I [dex Otaku] am at a loss for this, since nothing seems to be obviously awry with how things are installed or set up.



If anyone has any ideas on how to fix this, they would gladly be appreciately.



Thank you,

dex Otaku and JarkaRuus

---

### Post by blackmh on 2006-10-25
Try to kill artsd before running amarok and see what happens

---

### Post by JarkaRuus on 2006-10-25
Thanks, blackmh.  That did indeeds fix the problem - this time, at least.  Does this mean I have to kill/force-restart artsd after every reboot?  I suppose I'll find out.

btw, in searching the fora for an existing solution, I came across lots of mentions of problems from a specific update to xine, but almost all those threads were about broken streaming formats [many specifically mentioning mp3 playback still working].  

Any hints on why it's happening in the first place?  I'm curious as to whether this actually had something to do with the broken update or not.

d/j

---

