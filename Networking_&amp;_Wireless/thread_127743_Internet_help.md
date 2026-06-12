---
title: "Internet help"
date: 2006-02-09
forum: Networking &amp; Wireless
---

### Post by monkeypoo on 2006-02-09
hiya

after getting another crazy virus that wouldnt go away and having to reinstall for the 4th time in a month I smashed up my copy of xp in a fit of rage and procedded to install ubuntu on my toshiba A40


first i was getting trouble but i muddled my way through it i got all my hardware working  except my bt voyager 105 

i searched the forum and followed someone instruction for hoary it used the deb package of eciadsl and it wouldnt install correctly synaptics reports it has a broken package and alot of the files arent in the right place

i was logged in as root when i tried gettin the modem running do you reckon its some file permissions that stopping it from installing eciadsl correctly?

shall i try using a diffrent version of eciadsl?

any help would be greatly appreciated

thank you for your time

---

### Post by monkeypoo on 2006-02-09
[QUOTE=monkeypoo]hiya

after getting another crazy virus that wouldnt go away and having to reinstall for the 4th time in a month I smashed up my copy of xp in a fit of rage and procedded to install ubuntu on my toshiba A40


first i was getting trouble but i muddled my way through it i got all my hardware working  except my bt voyager 105 

i searched the forum and followed someone instruction for hoary it used the deb package of eciadsl and it wouldnt install correctly synaptics reports it has a broken package and alot of the files arent in the right place

i was logged in as root when i tried gettin the modem running do you reckon its some file permissions that stopping it from installing eciadsl correctly?

shall i try using a diffrent version of eciadsl?

any help would be greatly appreciated

thank you for your time[/QUOTE]


o kay i figured out i dont have permission to run shell scripts the problem was i had to install that ppoe thing but the shell script doesnt run when i cd to the directoy its on and type sudo sh go it says bad interpreter premission denied?

how do i sign in as admin?


EDIT: okay i was getting these errors cos iwas running from fat32


but now when i try to run /configure i get no acceptable c compiler found?

any help anyone?

---

### Post by Lambert on 2006-02-09
in a hurry shouldn't have posted.

---

### Post by KB3MKD on 2006-02-09
> 
but now when i try to run /configure i get no acceptable c compiler found?

any help anyone?

i think that's supposed to be ./configure, not /configure  The period is important.

Assuming you have it correct on your system, run *sudo apt-get install gcc-4.0*

---

### Post by monkeypoo on 2006-02-09
ive installed the gcc using aptget ive managed to install ppoe according to ubuntuguide.org however when i run eciadsl deb package i get the same dependenci issues no pppoe installed

man im tired im offf to sleeepp tomorows another day

thanks for the help

---

### Post by mips on 2006-02-09
[QUOTE=monkeypoo]ive installed the gcc using aptget ive managed to install ppoe according to ubuntuguide.org however when i run eciadsl deb package i get the same dependenci issues no pppoe installed

man im tired im offf to sleeepp tomorows another day

thanks for the help[/QUOTE]

Where did you install gcc from, the cd ?

---

### Post by monkeypoo on 2006-02-10
hiya 

i installed the GCC from the cd

---

### Post by mips on 2006-02-10
[http://ubuntuforums.org/showthread.php?t=127249](http://ubuntuforums.org/showthread.php?t=127249)
[http://www.lack-of.org.uk/viewarticle.php?article=114](http://www.lack-of.org.uk/viewarticle.php?article=114)

---

### Post by penquin on 2006-02-10
I just finally got my computer to dual boot and the dsl internet won't work.  I can get ubuntu updates but firefox doesn't load.  I am new to linux so any help will be nice if you could point me in the correct direction and exactly where and how.

---

### Post by mips on 2006-02-11
[QUOTE=penquin]I just finally got my computer to dual boot and the dsl internet won't work.  I can get ubuntu updates but firefox doesn't load.  I am new to linux so any help will be nice if you could point me in the correct direction and exactly where and how.[/QUOTE]

[http://www.ubuntuforums.org/showthread.php?t=78337](http://www.ubuntuforums.org/showthread.php?t=78337)    Post#4 Option1

---

### Post by monkeypoo on 2006-02-12
i have tried that guide before i cant install eciadsl because i dont have pppoe installed?

what do i do?

---

### Post by mips on 2006-02-13
I have never used pppoe. Is it not available on the cd or cant you download it via windows or something.

---

### Post by monkeypoo on 2006-02-13
hiya 

ive managed to get it installed thanks for all the help

i used the latest stable eciadsl source and it worked :KS 

I've gone on a package installing frenzy, automatix dont work for me so i've had to do it all by hand. 

again thanks for all the help

---

