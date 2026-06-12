---
title: "start beryl-manager on startup"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by acerlinux on 2006-11-05
I just simply add the "beryl-manager" into the startup programs, but it seems that most of the time it will not work properly, the symptom is:

the shadow of the panel is flashing some times, and the window's border too. at the same time, the CPU usage is 100%. If I log out and log in again, it will works very well. does any one know what is the problem and how to solve it? thanks.

---

### Post by ihavenoideax2 on 2006-11-05
I was having the same problem but i did something and it stopped doing it. I just wish i remember what i did to fix it. I bet you now when i boot back into ubuntu it will be doing that again.

---

### Post by Uolirod on 2006-11-05
It, the flashing windows borders, etc., usually occur because there are two instances of emerald running but I don't why that happens or how to fix it.

---

### Post by zgornel on 2006-11-05
Add emerald to the Gnome Sessions Startup List .... Depending on the theme, it works :D

---

### Post by acerlinux on 2006-11-05
> **zgornel said:**
> Add emerald to the Gnome Sessions Startup List .... Depending on the theme, it works :D

Well, would you like to show me how? and could you explain why? that should be great. thanks.:-k

---

### Post by Suzan on 2006-11-05
I've added the entry

emerald --replace

to the start programs and have no problems.

---

### Post by acerlinux on 2006-11-05
> **Suzan said:**
> I've added the entry

emerald --replace

to the start programs and have no problems.

Could you write more detailed info. here to show me how to do that step by step? That should be grateful, because I am really at an entry level.:-k :-k . thanks

PS: is that just simply add "emerald --replace" to the startup programs just like I added "beryl-manager"? do I need to consider about the startup sequence for the programs? if applicable how?

---

### Post by Suzan on 2006-11-05
> **acerlinux said:**
> I just simply add the "beryl-manager" into the startup programs

So you've add one entry in the startup programs that ist called "beryl-manager". Just add another entry that is called

emerald --replace

---

### Post by acerlinux on 2006-11-05
> **Suzan said:**
> So you've add one entry in the startup programs that ist called "beryl-manager". Just add another entry that is called

emerald --replace

one more question regarding that, if I add:
1. beryl
2. emerald
is that will take same effects as:
1. beryl-manager
2. emerald --replace

Thx

---

### Post by corstar on 2006-11-05
> **Suzan said:**
> So you've add one entry in the startup programs that ist called "beryl-manager". Just add another entry that is called

emerald --replace

Thanks, this worked for me..

---

### Post by cjnucette on 2006-11-07
Well my problem is that beryl-manager disappear from the startup programs list, even if i include the full path:**/usr/bin/beryl-manager**.

---

### Post by ShadowVlican on 2006-11-22
> **Suzan said:**
> I've added the entry

emerald --replace

to the start programs and have no problems.
i thought i had it all setup right... til next reboot and i had this damn border/window flashing

followed your advice, now it's fixed! (permanently i hope :rolleyes: )

thanks!

---

### Post by thebert on 2006-11-26
I am having the same problem as cjnucette.

---

### Post by iwan-zx on 2006-12-24
I used to have the same problem with Beryl, **emerald --replace** fixed it.
Thanks a lot, Suzan :)

---

