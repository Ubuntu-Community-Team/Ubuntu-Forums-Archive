---
title: "an ubuntu studio installer"
date: 2006-04-17
forum: Multimedia &amp; Video
---

### Post by peanut butter on 2006-04-17
i was thinking: would it be easier if i made a script with zenity to install ubuntu studio? would anyone use it. i was thinking of using the BUMPS base since its gpl. (if its ok with the bumps author) any feedback please.:)

---

### Post by ogami1972 on 2006-04-17
Would it install audio software ala Automatix?- I think it would be appreciated, and i would use it if i ever needed a fresh install on my multi-track machine...

---

### Post by peanut butter on 2006-04-17
cool ill get started on it. BUMPS is an automatix thingy for drapper but i can get it to work on breezy.

---

### Post by peanut butter on 2006-04-17
WARNING!!!!!!!!!!!!!!!!!!!!!! This dosn't work...

maby someone who knows bash scripting better can help me:
when ever i try to run the script attached that i made it says unexpected end of file.](*,) ](*,)  how do i get it to run?

---

### Post by MetalMusicAddict on 2006-04-17
Nice idea. Get together with Dolson to get help with this.

---

### Post by dolson on 2006-04-17
I don't like the methods that Automatix uses to install software. If this thing will edit my sources list and install foreign software, then I will not support it.

But if it will check the sources list to see that universe and multiverse are enabled and warn if they are not, and then offer options to install all of the packages that we have listed on the site, without modifying the sources list or forcing installs of foreign packages, then it was already something I had planned on working on when I had more free time.

---

### Post by peanut butter on 2006-04-19
it alredy restores the original sources.list and i will add an option at the beginning of weather to use your sources or to use the packaged one and restore it later.
you might take a look at the code and see if you can adapt it to something you want because i dont have much time to track down all the problems with my code.

---

### Post by mGee on 2006-04-21
I'd definitely like to see this develop. Good luck!

---

### Post by falkenberg_cph on 2006-06-10
Sounds like a good idea. As a newbe i find it all very confusing. It would be nice if the installer could create the patched RT kernel and perhaps even make a test (plus troubleshooting) of the setup. Is that possible.

Carsten

---

### Post by guzerat on 2006-06-13
[QUOTE=peanut butter]maby someone who knows bash scripting better can help me:
when ever i try to run the script attached that i made it says unexpected end of file. how do i get it to run?[/QUOTE]

well... it's a long time since your post and you should have solved it by now but try adding a newline at the end of "usei" :)

---

