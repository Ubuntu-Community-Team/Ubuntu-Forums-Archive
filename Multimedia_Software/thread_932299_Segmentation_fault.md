---
title: "Segmentation fault"
date: 2008-09-28
forum: Multimedia Software
---

### Post by tetrafuran on 2008-09-28
Several software seem to crash suddenly without any warnings. If I run them from the terminal I usually get all sorts of errors, but all of the have one thing in common: Segmentation fault

I even noticed it happens to gimp. 
> (script-fu:12093): LibGimpBase-WARNING **: script-fu: gimp_wire_read(): error
Segmentation fault
In several games I get longer error messages, but they are essentially the same.

What's going on in here? How can I fix it? I really need to get some editing done and gimp keeps crashing every five minutes. Also gaming experiences are equally limited. Otherwise graphics are as they should be.

---

### Post by eldragon on 2008-09-28
i asume you are using software from the repos. so we can rule software errors out of the equation :D

i would start by checking system ram. system temperatures, and hdd for errors.

for system ram: use a livecd and pick the system RAM check option.

for system temp: i think the app is called lmsensors, find it in the repos
 you could stress your cpu with burnmmx which is available through the cpuburn package in the repos.

for hdd test. hmm i think a fsck should suffice, but not sure.

---

### Post by tetrafuran on 2008-09-28
I searched for lmsensors and found only gdesklets and wmsensors. Neither one of them seem to really match. I'm still trying to figure out how to use gdesklets. terminal didn't recognize the command lmsensors, so I'm runing out of ideas. 

In the meanwhile I'll probably test RAM with the live disk as you suggested.

ok. desklet program doesn't seem to do anything at all. It starts and disappears. What next. 

By the way I have tried this same hardware with windows xp and a few 3d games. No crashing seems to happen in there. When I'm running sauerbraten under linux I'm not using any of the fancy modern 3d stuff. I made the game as ugly as I can, and it still crashes. In windows I used elder scrolls 3 Morrowind with all the eye candy available. It didn't crash more often than it did in my old computer. Perhaps I should still run a 3d mark to see if windows can handle a bit of stress.

---

### Post by tetrafuran on 2008-09-29
I started running the memory scan. It seems to take a while. 4:45 gone so far... it reminds me why I never ran it fully.

---

