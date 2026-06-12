---
title: "MythBuntu MythTV source code"
date: 2008-04-06
forum: Mythbuntu
---

### Post by lcastillo on 2008-04-06
Hi, i installed mythbuntu 7.10 from the CD image, but now i want to change some things in MythTV but i can't find the source code, i mean the path.

Please if somebody knows where i can find them let me know.

Thanks,

LCD

---

### Post by superm1 on 2008-04-07
apt-get source mythtv

---

### Post by lcastillo on 2008-04-08
Thanks for the reply, 

Sorry my ignorance, if i modify any archive, do i need to configure all my mythtv or can i compile only that archive? If the answer is the second one, where do i have to allocate that new archive to function with my mythtv.?

i need to modify only few archives to add some things to the main menu.

Thanks.

---

### Post by laga on 2008-04-08
What's an "archive"? :) 

Anyways,
I don't think you need to rebuild MythTV if you just want to modify the menu structure. Maybe this will be good enough for you: [http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide](http://www.mythtv.org/wiki/index.php/Menu_theme_development_guide)

If you want to launch external programs, look for "EXEC".

---

### Post by lcastillo on 2008-04-09
Thanks for the answer.

But what i need to do is to create a new action, so i think i need to change the soruce code :S

Please help me.. :(

LCD

---

### Post by superm1 on 2008-04-09
If you are trying to change the behavior of an action you will have to recompile the code.

Follow these basic steps:

1) apt-get source mythtv
2) sudo apt-get build-dep mythtv
3) sudo apt-get install devscripts
4) dch -i
Put what you are changing in the changelog.
5) Make changes
6) debuild
7) Profit!

---

### Post by DutchLoki on 2008-06-20
> **superm1 said:**
> If you are trying to change the behavior of an action you will have to recompile the code.

Follow these basic steps:

1) apt-get source mythtv
2) sudo apt-get build-dep mythtv
3) sudo apt-get install devscripts
4) dch -i
Put what you are changing in the changelog.
5) Make changes
6) debuild
7) Profit!

Great... had a similar problem. Thanks for the info.

---

