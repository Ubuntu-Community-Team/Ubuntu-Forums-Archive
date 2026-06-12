---
title: "Kubuntu has no sound"
date: 2011-03-05
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by firstc624 on 2011-03-05
Title really says it all.  If i go to the system settings and check the sound properties it doesn't play and sound then after a while it will start playing sound for no reason.

I was trying to listen to music, amarok, and of course it wasn't working so i figured ok, this is  a beta so maybe the sound is messed up.starting looking around went to close the program and then sound started working.   

I have had the same experiace w/ youtube and any other site that has sound.


has anyone else had this?  and if so what did you do to fix it?  Thanks for the help


Oh this happens chrome, and ronkq so it wasn't browser related


EDIT

To make this more instulting to me, my battery just got low on my laptop and the stupid even sound fired.   now after about 10 min of telling it to "play the sound kicked in"

---

### Post by Johnny3 on 2011-03-05
Did you try going to system/sounds/hard ware and make shore your sound card is checked? Sometime 11.04 will try and use my video card for sound don't known why. Also I used to be able to use 
sudo aptitude update
sudo aptitude install linux-backports-modules-alsa-lucid-generic
In 10.10 and 10.4 but doesn't work in 11.4 said no such command or something like that? This is a new bee talking.
GB Johnny3

---

### Post by firstc624 on 2011-03-05
I am runniing KUBUNTU  those settings you are refering to are in Ubuntu


Very odd behavior

---

### Post by seeker5528 on 2011-03-07
Could be something with pulseaudio.

If you go to 'System Settings --> Startup and shutdown --> Autostart', look for 'PulseAudio Session Management' and deselect it, log out, log in.

Does that make a difference?

If you want to get rid of pulseaudio, open synaptic, on the left select 'status' and 'all', on the right single click any package, then type 'pulse' (without the quotes). Now you should see 'pulseaudio' and some 'pulseaudio-*' packages listed which you can select and remove.

If you don't like the list of additional stuff it indicates will be removed while you are selecting these packages you can cancel the removal, then go to 'Settings --> preferences --> general' and uncheck the box next to 'consider recommended packages as dependencies' to reduce the list of additional packages that will be removed, after making the selection you can go back and check the box again, most of the time recommended packages won't be pulled in again when upgrading things that are already installed.

Later, Seeker

---

