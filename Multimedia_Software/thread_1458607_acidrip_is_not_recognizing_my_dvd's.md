---
title: "acidrip is not recognizing my dvd's"
date: 2010-04-20
forum: Multimedia Software
---

### Post by SGC622 on 2010-04-20
I had a dual boot installation of vista and Kubuntu 9.10 on my computer, i primarily used kubuntu and was phasing out windows, then all of a sudden I was in the process of creating an ISO file with KISO and Kubuntu i assume crashed and went back to the login screen, and thats where it stayed despite my attempts to type in my password to login, it just kept resetting back to the login screen. so in short after my attempts to salvage it i ended up deleting windows and reinstalling kubuntu 9.10 on that partition and leaving the old partition with my malfunctioning kubuntu as it was to drag the data to my new kubuntu install. 

My question to you is before the whole ordeal with kubuntu crashing i was using Acidrip to back up my dvd collection and it was going fine, i had two drives for one the path was /dev/dvd and for the other drive it was /media/cdrom0 and i hit load and it would bring up the dvd info and i'd rip it on my computer no problem.  Ever since the new install of kubuntu acidrip keeps saying either "no valid files found" or "cant read disk faulty?" i have no idea whats wrong. i am using the same drive paths, i even tried /dev/sr0 and i got a little bit of loading from acidrip like it was gonna bring up the dvd but it eventually said "cant read disk faulty?" again. I have tried reinstalling it and everything. aswell i tried creating an iso with terminal by typing in.
> 
cp /dev/sr0 file.iso

and i get 

scott@home:~$ cp /dev/sr0 file.iso
cp: reading `/dev/sr0': Input/output error
scott@home:~$


its like kubuntu's communication with my hardware has gone to sh*t any one have this problem or know how i can go about fixing it?

---

