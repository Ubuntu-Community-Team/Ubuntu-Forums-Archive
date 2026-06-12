---
title: "Not able to launch java from the side bar nor run any project from it"
date: 2016-10-30
forum: Multimedia Software
---

### Post by AntoineCompagnie on 2016-10-30
I downloaded Eclispe and locked it to the launcher. Yet, when I click on  it, nothing appears. However when I click from Home/eclipse/eclipse I  actually gets the ide.
However I am not able to execute any of its project, it sticks to an old project I deleted

Here is the message I have:

```
Launch configuration Prolog references non-existing project L3_Informatique.
```

I thnki it is a path issue...

---

### Post by ajgreeny on 2016-10-30
Was there a reason that you downloaded it direct rather than installed it from the repos?

Whatever the answer to that, I think you are correct about it being a pathway problem.

Where is the eclipse executable actually sitting; it would seem it's in an **eclipse** folder in your home?
How did you create the launcher for it which you locked to the launchbar, and if you created the .desktop file yourself, what did you use in the **Exec=** line?
You need to use the full pathway to the executable there which will be **Exec=/home/<*username*>/eclipse/eclipse**, using your username, of course, if the executable is not in one of the several $PATH folders in your system.
You can see the default folders with command echo $PATH which will normally output the list
**/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games**
and if you have anything in a **bin** folder in your home that will also be added to the list.
Any executables in the $PATH folders will work simply with the executable name; the full pathway is not needed in that case.

---

### Post by AntoineCompagnie on 2016-10-30
Hi, I surely had a bad Windows relfex... When the software was running I only did a right click to do "Lock from the launcher".
How can we set up the full pathway to the executable?
Here is echo $PATH result :

```
:~$ echo $PATH
/home/antoine/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games
```

which is a bit different.

---

### Post by ajgreeny on 2016-10-31
Your echo $PATH is actually the same as mine but does include the /bin folder from your home which you apparently have; I don't.

Have a look in **/home/antoine/.local/applications** folder for an **eclipse.desktop** file and if found open it with command```
gedit /home/antoine/.local/applications/eclipse.desktop
``` and if necessary change the Exec= line in that to the pathway of you eclipse executable which I suspect is **/home/antoine/eclipse/eclipse** but check that first.

If you now logout and in again you may find that the launcher in the launchbar now works for you.

---

