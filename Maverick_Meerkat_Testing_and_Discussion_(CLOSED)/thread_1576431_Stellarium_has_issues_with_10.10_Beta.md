---
title: "Stellarium has issues with 10.10 Beta"
date: 2010-09-17
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by henrodon on 2010-09-17
I installed 10.10 beta and everything seems to work fine except Stellarium. It will run, but I can't access half of the menus -- the half on the left side. I tried uninstalling and re-installing -- no difference. Is there anyone out there who can help this almost-newbie get this old standby running?

---

### Post by Soul-Sing on 2010-09-17
driver for your videocard allready enabled via hardware drivers?

---

### Post by henrodon on 2010-09-17
Thanks for the very quick reply. Videos play fine in vlc, so I guess the answer is yes. 
Is there something else to do regarding your advice? It's not something I really understand.

---

### Post by Soul-Sing on 2010-09-17
> **henrodon said:**
> Thanks for the very quick reply. Videos play fine in vlc, so I guess the answer is yes. 
Is there something else to do regarding your advice? It's not something I really understand.

sorry: system, administration: hardware drivers
is there a driver av. for your videocard, or are you using an intel card?

---

### Post by henrodon on 2010-09-18
System>Administration>Drivers

"No proprietary drivers are in use on this system."

---

### Post by Soul-Sing on 2010-09-18
> **henrodon said:**
> System>Administration>Drivers

"No proprietary drivers are in use on this system."

So there are drivers available?

---

### Post by henrodon on 2010-09-18
No drivers at all are listed when I try that search. The search return ONLY the sentence I quoted. 

But as I said, I can play videos with vlc, so somehow the system is figuring out what to do. How, I have no idea, given my very limited computer smarts.

---

### Post by Soul-Sing on 2010-09-18
what is the outcome of:

(install first: ```
sudo apt-get install mesa-utils
```)
```
glxinfo|grep direct
```

---

### Post by oprogue on 2010-09-24
I am not the OP, but am having the same issue.  Here are the results:

[INDENT]ph@ph-laptop:~$ sudo apt-get install mesa-utils
[sudo] password for ph: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
The following package was automatically installed and is no longer required:
  libdvbpsi5
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 121 not upgraded.
ph@ph-laptop:~$ glxinfo|grep direct
direct rendering: Yes
ph@ph-laptop:~$ [/INDENT]

Without a restart or anything the same behavior is exhibited - both menus are empty.  I have additionally "marked" and re-installed Stellarium without success.

Your time, consideration and recommendations are appreciated.

---

### Post by Soul-Sing on 2010-09-24
direct rendering is ok

i have no idea what problem this could be.
you could start it from the console/terminal and copy=paste the errors.

---

