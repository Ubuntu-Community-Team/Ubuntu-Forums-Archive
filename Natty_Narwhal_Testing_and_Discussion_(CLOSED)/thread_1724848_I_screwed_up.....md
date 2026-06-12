---
title: "I screwed up...."
date: 2011-04-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by AmuletOfNight on 2011-04-08
So....I was messing with Compiz's settings (ubuntu 11.04, using unity) and i accidently unchecked OpenGL and clicked the wrong button, and it disabled everything else which caused unity to crash, and then i click reset to default in compiz and restarted ubuntu, but now i have no unity interface, no interface at all..so, does anybody have any idea what i did? how do i fix it? o.O

---

### Post by AmuletOfNight on 2011-04-08
Bump! I really need this resolved. Can I re-install unity or something?

---

### Post by VinDSL on 2011-04-09
Open a terminal and try:

```

compiz --replace

```

If that doesn't work:

[LIST]
[*]Ctrl+Alt+F1
[*]Login
[/LIST]
```

DISPLAY=:0.0 compiz --replace

```

---

### Post by mc4man on 2011-04-09
If you unset all the compiz plugins then the absolute min. to return to a 'workable' unity login would be opengl, composite, unity, window decoration
and then take it from there - the defaults are seen here, not all needed, names maybe a hair different than shown

> initializing compiztoolbox options...done
Initializing mousepoll options...done
Initializing wall options...done
Initializing move options...done
Initializing gnomecompat options...done
Initializing detection options...done
Initializing session options...done
Initializing staticswitcher options...done
Initializing regex options...done
Initializing decor options...done
Initializing scale options...done
Initializing opengl options...done
Initializing animation options...done
Initializing ezoom options...done
Initializing fade options...done
Initializing imgpng options...done
Initializing place options...done
Initializing composite options...done
Initializing unityshell options...done
Initializing snap options...done
Initializing grid options...done
Initializing bailer options...done
Initializing resize options...done
Initializing unitymtgrabhandles options...done
Initializing vpswitch options...done
Initializing expo options...done
Initializing workarounds options...done




---

### Post by AmuletOfNight on 2011-04-17
Well, I reset all of them to default, and compiz still wont start. Compiz trys to initialize, but then ends with "Segmentation fault (core dumped)" And unity wont start because compiz won't start. Hmm....

---

### Post by Blasphemist on 2011-04-17
Can you log into classic? I'm guessing that may be what you've done for the last week. If you can login to classic, and run ccsm, and re-select open gl and unity, do so. Then regardless of what classic looks like, restart and login to unity. It should be good. If it is, log out and login to classic and de-select unity. Then restart again and login to unity. It should still be good. And so should classic.

---

### Post by texla on 2011-04-17
DISCLAIMER - I am not a dev so you may want to see if one of them approves this first - but, this got me out of a similar jam beautifully:

                                                                     Originally Posted by **lucazade**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=10683671#post10683671")                 
                 [I]have you tried to reset compiz/unity settings?

**ctrl+alt+t  to open a terminal**

**unity --reset**

[I]After I did this, the terminal did stay open for a long time and I had to force it closed - But, once I restarted the computer  everything was back to square1! - hope this helps!
[/I]
[/I]

---

### Post by ConsumingFire783 on 2011-04-20
I'm having the exact same problem.  I can't even open a terminal (ctrl+alt+t doesn't work).  I tried the other solutions, and those didn't work.  Any more ideas???

---

### Post by ankspo71 on 2011-04-21
Hi,
Do you see a menu when you right click on the desktop? If you do, you can create an application launcher for 'gnome-terminal' or 'unity --reset'. I'm not at my Unity desktop so my wording may be a little off. But it should work if your desktop is displaying icons on the desktop.
Hope this helps.

---

### Post by ConsumingFire783 on 2011-04-21
Well, that seemed to work.  Thanks!  When I did the reset at first, it went back to being all screwed up as soon as I closed the terminal.  But after restarting, it saved the changes, and is now working.  I finally have a working top info bar and side bar with icons!  And I know how to make a terminal link, too.

---

