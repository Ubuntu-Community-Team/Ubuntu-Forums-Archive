---
title: "cant play music"
date: 2008-10-17
forum: Multimedia Software
---

### Post by odedlo on 2008-10-17
hi
i tried playing my music, which is all in mp3 format,  it just didnt work. recently i had to by a new motherboard so i reinstalled ubuntu on my computer - hardy haron - and had to build a driver for my networking, and a dialller, i guess the setup couldnt automatically install important software.. (i think??).. after that, i also had to configure my soundcard so i installed alsamixer. the jist of it is - i have the start up sounds and i can hear sound when i watch streaming over the internet, BUT i cant hear any music. it started with not working on rhythmbox, so i uninstalled it. after that i installed amarok which also didnt work, and i had to force quit it so i unistaled it also. last i installed exail, which also doesn't work. 
can someone PLEASE help me?

---

### Post by Ubun00btu on 2008-10-17
Have you installed the proper codecs for listening to MP3 or whatever filetype you are trying to listen to?  I had a similar situation (except mine was mostly driver related) but I had a fresh install and needed to reinstall the codecs to listen to MP3s.

---

### Post by odedlo on 2008-10-17
i think so..
do you mean gstreamer0.10 ugly and the like?

---

### Post by minky311 on 2008-10-17
Try starting all the music applications you have in the terminal by typing in the name of the program. After the program starts if it begins to freeze force quit it and check the terminal to see if it outputs any errors. Post the output here and hopefully it might give us some clues as to why it crashed.

---

### Post by odedlo on 2008-10-18
nothing is happening. i open a terminal window type in amarok, and nothing happens. when i type in 'rhythmbox' the program strats, but then nothing jappens, no music no sound and no crash...

---

### Post by atomo133 on 2008-10-18
right click on the file -> open with totem
if the type is not supported you will be promted to install some codecs
you might need internet connection

---

### Post by odedlo on 2008-10-18
also checked if it will work with ogg format and it doesn't. rhythmbox just doenst do anything...

---

