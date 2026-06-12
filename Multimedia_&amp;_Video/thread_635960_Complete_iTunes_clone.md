---
title: "Complete iTunes clone?"
date: 2007-12-09
forum: Multimedia &amp; Video
---

### Post by 7llusion on 2007-12-09
Is there any program out there that will completely sync my 3rd gen iPod nano to a library that I have made, this means, that if I change the tags/album over of a track, it will be updated on my iPod?
I would also like to be to make it sync music videos, this means that these videos have tags and will show up on my nano's music database in the iPod and also in the music video section.
And of course photo and normal film syncing.
I have tried Floola, Amarok, gtkpod etc, but none can sync music videos and photos and don't sync iTunes style, that is updating changed tags..
Illusion

---

### Post by dontpannic on 2007-12-10
Can you not try emulating iTunes via Wine/Crossover?

Close firefox
sudo apt-get install wine
winecfg

Set it to emulate Windows 2000 / XP

Open firefox and browse to download iTunes

Hopefully file download box will open and you should get "Open with wine"

If you do:
Run through the installer as normal, Wine should create a shortcut to iTunes on your Desktop and in Applications -> Wine -> Programs -> Itunes

If you don't - save the exe to your home area
open up a terminal
browseto your area
type "wine iTunesSetup.exe"

Last time i looked itunes was supported with wine...

---

