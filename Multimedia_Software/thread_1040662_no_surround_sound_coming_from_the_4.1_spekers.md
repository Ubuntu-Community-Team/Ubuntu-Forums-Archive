---
title: "no surround sound coming from the 4.1 spekers"
date: 2009-01-15
forum: Multimedia Software
---

### Post by Santooka on 2009-01-15
dear friends,

i have 4.1 creative speakers, and the rear speakers are not working at all,

i even think that ubuntu is not detecting them available as speakers in the first place...

i have a gigabyte mother board G31M-ES2L...

i tried to modify anything in alsa or pulseaudio or modify the audio channels but i guess either i am totally ignorant to these tools and drivers or i did what is supposed to be done and nothing reacted to my action, or maybe ubuntu doesn't support the rear speakers at all :P

help me please.... to listen to the four speakers i use windows vista and i really don't wanna turn back to windows anymore....

thank you

---

### Post by linuxwizard on 2009-01-16
Have you tried this > gksudo gedit /etc/pulse/daemon.conf >  than look for this line > # default-sample-channels = 2 > now remove the comment from the beginning of that line and than change the 2 to 5. You will need to restart PulseAudio. 

[http://www.pulseaudio.org/wiki/FAQ](http://www.pulseaudio.org/wiki/FAQ)

---

### Post by Santooka on 2009-01-16
ok i did what u told me to do but still it's not working

first i checked my mother board specs and i found that it supports 4 channels, which i use in windows and it's not counting the subwoofer as a stand alone channel.

so i wrote 4

but still the rear speakers are not working at all

and i tried to do exactly like they said in this thread:[http://ubuntuforums.org/showthread.php?t=795525]("http://ubuntuforums.org/showthread.php?t=795525")

and the same, nothing's happening

do u have any explanation?

---

### Post by linuxwizard on 2009-01-16
You need to change that to a 5 which represents a 4.1 system. The 4 you put would represent a 3.1 system. If you look at that link I gave you it shows just what I am trying to tell you to do. I had the same issue I changed mine to 5 for a 4.1 and my sound works great.

---

### Post by Santooka on 2009-01-16
still nothing :s

did what u said and still nothing happened...

any new ideas?

---

### Post by linuxwizard on 2009-01-16
After making the change did you restart PulseAudio ?

---

### Post by Santooka on 2009-01-16
yep, i restarted ubuntu!!!

still nothing

---

### Post by Santooka on 2009-01-16
ok is there any way to work with alsa on this?

---

### Post by markbuntu on 2009-01-16
If you want some more tools to control your sound go here

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

