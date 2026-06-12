---
title: "Music Organiser/Player"
date: 2009-05-02
forum: Multimedia Software
---

### Post by jamieleshaw on 2009-05-02
IS there a music organiser/player that is like windows media player 11?

P.S: I'm trying to get a friend of mine to switch to Ubuntu.

---

### Post by xc3RnbFO8P on 2009-05-02
You can check in Application> Add/Remove (all available application)
Listen
Banshee
Elisa (media center)

> P.S: I'm trying to get a friend of mine to switch to Ubuntu.
Good luck :)

---

### Post by x33a on 2009-05-02
amarok
songbird
rythmbox
banshee
exaile
quod libet

and lots more.

---

### Post by Quift on 2009-05-02
I have a related question, I want to re-organize my library. To many formats, to many dublicates, files not laying in the same order etc. I'm now trying to write a script that would do this for me, but so far I havn't gotten farther that this..

# Gå till rätt mapp
cd /home/pierre--emil/Skivbord/testmapp

# Lägga alla filer till testmappen på skrivbordet

mv */*.mp3 /home/pierre-emil/Skrivbord/testmapp | mv */*.ma4 /home/pierre-emil/Skrivbord/testmapp | mv */*.waw /home/pierre-emil/Skrivbord/testmapp | mv */*.wma /home/pierre-emil/Skrivbord/testmapp | mv */*/*.mp3 /home/pierre-emil/Skrivbord/testmapp | mv */*/*.ma4 /home/pierre-emil/Skrivbord/testmapp | mv */*/*.waw /home/pierre-emil/Skrivbord/testmapp | mv */*/*.wma /home/pierre-emil/Skrivbord/testmapp | mv */*/*/*.mp3 /home/pierre-emil/Skrivbord/testmapp | mv */*/*/*.ma4 /home/pierre-emil/Skrivbord/testmapp | mv */*/*/*.waw /home/pierre-emil/Skrivbord/testmapp | mv */*/*/*.wma /home/pierre-emil/Skrivbord/testmapp

# Töm alla mappar på innehåll, och töm sen de tomma mapparna
rm ./*/*/* |rm ./*/*/ |rm ./*/* |rm ./*/ | rmdir ./*

# Varning!! Raderar allt förutom mapparna som jag vill ta bort.
# rm ./*

# Filformat att hantera .mp3, .m4a, .ogg, .waw, .wma
# Konvertera alla filer till samma format .ogg
soundconverter -b *.m4a | soundconverter -b *.mp3 |soundconverter -b *.wma |soundconverter -b *.waw

# Ta bort alla nya dubletter
rm *.mp3 | rm *.m4a | rm *.waw | rm *.wma

This basically pulls out all the music from their directories, converts everything too Vorbis, and removes the old files. I would probably chain the delettion to come directly after a particular file conversion to save disk space during process. 

But here is my further question. After this I wish to re-identify every single track and rename it using picard, aswell as putting everything back in order in Musik/Artist/Almbum/song.ogg from this single location.

is it possible to use picard in CLI, and how would I get everything sorted into the correct directiries? Any ideas?

I appriciate any help with this.
best regards, Quift

---

