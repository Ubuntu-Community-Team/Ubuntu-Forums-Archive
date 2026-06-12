---
title: "rip/play problems"
date: 2008-03-06
forum: Multimedia &amp; Video
---

### Post by japephillips on 2008-03-06
this will be confused post, sorry, but I am confused

i recently loaded up and use KDE because of gnome dropping things like app close/min/max and failing various windows things like drag and drop, leaving windows on top of each other and then locking up

now if i load audio cd, it shows on desktop as that but right click to 'properties' says 'unknown'

as i put it in, it offers to open or extract into k3b

i have the libmad/sox/vcdx and all the other relevant stuff and k3b finds it
but if i click on the cd icon it doesn't play, either in k3b or without, nor does it find any other player

k3b does not 'extract' to mp3 if i ask it to
grip extracts but to ogg and won't change that
gnomebake and serpentine don't find the cd player
juicer will open it but not have any mp3 options

i can 'copy' it in k3b to another disc (blank)
but i cannot add it to a k3b 'project', drag and drop gives 'no support for non local files message'
so if i fiddle around i can extract via grip but not to mp3
 i can play it from within some players such as kaffeine but not others and it doesn't play automatically
direct copy but not edit in k3b

seems to be a file association/recognition/mounting thing or a soundjuicer integration thing but that is as far as i can see and I am not good at this stuff

i want to be able to open the audio cd into k3b and see/edit/extract/ tracks like i used to in Nero on win
I want to have it automatically offer to play when i put a disc in

just a thought, should i somehow undo all the gnome stuff now i have KDE working?
I HAVE looked around the forums but don't understand enough to work this out myself, sorry.

 i see from other 'solutions' that if i try amarok and kaudiocreater instead it might work but that isn't really a true answer and is only a last resort, i am fed up with just attempting and often failing in downloading tons of 'just in case' stuff on synaptic (i have very slow and bad dialup too) and I am bloating my laptop with unneeded files

---

### Post by Bubba64 on 2008-03-06
If Gnome was installed correctly originally you shouldn't of had the problems you describe so going on to another desktop may have brought the problems along.

---

### Post by japephillips on 2008-03-06
wow
i never thought of that

cd player not seen properly? i dunno
does no-one here know about this stuff?

$ dcop kded mediamanager fullList
/org/freedesktop/Hal/devices/volume_uuid_915eaa06_ccb2_4f71_bd81_ce4680caaab3
sda1
38G Media

true
/dev/sda1
/
ext3
true

media/hdd_mounted

---
/org/freedesktop/Hal/devices/volume_part_1_size_476727296
scd0
Audio CD

false
/dev/scd0
/media/cdrom0

false
audiocd:/?device=/dev/scd0

---

