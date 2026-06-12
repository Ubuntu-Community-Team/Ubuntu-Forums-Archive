---
title: "Ununtu crash after update"
date: 2010-09-10
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by mpaczynski on 2010-09-10
Hi All

Yesterday I updated system from System Update and my Ubuntu creashed totally. 
Now each time I run system there is only tty window there is no xwindows any more. system shows error nad starting only command line.
I think it is due to grapic card drivers update.
Do you know how to rolback this update from command line?

If possible plase check this graphic card update as it create problems.

BR
Michal

---

### Post by utnubuuser on 2010-09-10
Updated or Upgraded?

If it was a kernel update that's causing the crashes, use the grub-menu and try an older kernel (further down the list).

If it was an upgrade, try to get into system recovery from grub-menu and try the option to "fix-broken".

---

### Post by mpaczynski on 2010-09-10
There was system update.

I tried fix broken but that didn't do the trick :(

in this update was also kernel upgrade so I do not know what exactly caused that problem.

BR
Rafal

---

### Post by ronacc on 2010-09-10
what version of Ubuntu were you running before the update , 10.04 , 10.10 or some other ?

edit:  also what graphics card are you using ?

---

### Post by mpaczynski on 2010-09-11
Hi I am running 10.10 beta - for tests I just installed it again. But I have that same error. During installation I have no mouse pointer. After installation I can change appearnace and "sometimes" but that is randomly I have mouse pointer.

All other works fine. But....
I installed updates again and that some error. Fixing is not helping. I think there is some problem with graphic card drivers.

I have notebook HP Pavilon ze4900 graphic card: Intel 82852/82855 GM/GME

can you plese find fix for that.

Previously I had Ubuntu 10.04 insalled it works with no problems. But during installation I had to change command line otherwise system was not installing. sorry but I do not remember what I need to add to instll script something "... -1".

BR
Michal

---

### Post by malti on 2010-09-11
I had the same pointer problem with the same graphics card and found a solution in another thread... Suspend the system (Ctrl+Alt+Del) and then resume. Worked for me.

---

### Post by mpaczynski on 2010-09-13
Hi 

Thank you for info. It is really works :)

However problem with system upgrade persist.

Yesterday I restored system from backup and installed all updates (except system update - called partial release).
system was working fine.
Next step I installed partial release as well - system fail I got infotmation Failed: POWER_MODE and system is running only in console mode.

I think there is an isse here.
Can anybody take a look on that and try to fix it.

I am kind of sure that I am not the only one running into that.


Thank you.

BR
Michal

---

### Post by terryazthompson on 2010-09-13
Same Problem here Dell Inspirion 1150.  Installed Partial upgrade after fresh beta install of 10.10, had mouse problem before partial upgrade and console only, no graphics after partial install.

---

### Post by ronacc on 2010-09-13
have a look at sticky #3 .

---

### Post by mpaczynski on 2010-09-14
Hi

Can you enclose link or something. Unfortunatelly I do not know what is sticky #3.

Thank you :)

BR
Michal

---

### Post by ronacc on 2010-09-14
the sticky's are always at the top of the pages , it is always a good idea to read them when starting to test a developement version , they contain valuable information .

[http://ubuntuforums.org/showthread.php?t=1479146](http://ubuntuforums.org/showthread.php?t=1479146)

sticky #3 is about partial upgrades and why the are usually a bad idea and must be approached very carefully .

---

### Post by mpaczynski on 2010-09-19
Hi All
I think now womething is better. I was able to update linux kernel.

BR
Michal

---

