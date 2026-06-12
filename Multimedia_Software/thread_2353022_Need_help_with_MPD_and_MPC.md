---
title: "Need help with MPD and MPC"
date: 2017-02-18
forum: Multimedia Software
---

### Post by Sunil_Daswani on 2017-02-18
Hi i am having some trouble with MPD and MPC, i followed the steps from here: [https://ubuntuforums.org/showthread.php?t=664334](https://ubuntuforums.org/showthread.php?t=664334)


but this problem is there: 

/home/sunil# mpd --create-db
[COLOR=#ff0000]cmdline: invalid option: --create-db
[/COLOR]
It isn't creating a music db....

I dont' know how to fix it....

thanks

---

### Post by ajgreeny on 2017-02-18
That thread is now 9 years old so many things may have changed since then.

I don't use mpd/mpc but I imagine there is a man for each so run **man mpd** in terminal and you may get more clues as to what is wrong in your case.  With the man page open search by typing **/create-db** to see if that finds anything for you that helps.

---

### Post by vasa1 on 2017-02-18
You may find more information here: [https://www.musicpd.org/doc/user/](https://www.musicpd.org/doc/user/)

By the way, why are you running as root?

---

### Post by Sunil_Daswani on 2017-02-19
figured it out, used mocp 

and it was ncmpc that was the player
- mpd mpc   ncmpc

---

### Post by ajgreeny on 2017-02-19
Great news! 
Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

