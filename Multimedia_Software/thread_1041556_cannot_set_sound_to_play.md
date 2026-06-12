---
title: "cannot set sound to play"
date: 2009-01-16
forum: Multimedia Software
---

### Post by hoboboot on 2009-01-16
about 2 weeks ago i followed a guide on these forums in hardy, it got my sound working perfectly, quite simply at that, now, since then i've wiped my drive and installed 8.10 which, the guide was originally written for, only said to work with hardy heron(and it had)

so i've upgraded to 8.10 because it correctly supports my video card...and my sound card is installed detected and whatnot, but, its not setup to work right from what i can tell. 

so here is the guide i followed before, which is said to work with interpid,

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

and so, the problem im having is that i cannot get it to, simply because i cannot install the following packages with synaptic, due to being unable to find them, these packages are : 

asoundconf-gtk
gnome-alsamixer
alsa-oss
padevchooser
gstreamer0.10-pulseaudio
ubuntu-restricted-extras

the guide which, i followed 2 weeks ago from hardy and worked flawlessly, cannot be followed in intrepid as it says... or at least, for me. can anyone else find these packages in their 8.10 intrepid ibex's synaptic package manager? 

is there a way i could get them? a setting to get old packages or does anyone know whats replaced them? 

i've edited the menu SYSTEM>PREFERENCES to show MULTIMEDIA SYSTEMS SELECTOR, assuming it had replaced the asoundconf-gtk default sound card selector... however this may not be accurate, and i still have yet to figure out how i might choose a device for playback with pulseaudio... 

are the packages in the repository different for seperate versions of ubuntu or have these packages simply been removed in the last 2 weeks? if so, what for, they were extremely useful tools...... 

am i missing something? can anyone help or answer some of these questions?

---

### Post by markbuntu on 2009-01-16
When you open Synaptic hit the reload button. Then search.
I just tried a search without reloading first and it did not find any of the packages, after reload it found them all.

---

### Post by hoboboot on 2009-01-16
solved. that was weird. thanks alot.

---

