---
title: "security that comes at cost of wine usability?"
date: 2010-08-08
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Yeeha on 2010-08-08
Apparently because of /usr/share/applications/wine.desktop has Exec=cautious-launcher %f wine start /unix then all windows executables have to flagged as executables as security measure but... What about cd and dvd setup.exe, install.exe and autorun.exe
you cant flag them as executables, oddly i could install one game from cd but not the other. With other i got Blocked: wine start /unix because of that. Ofcourse people can search around how to fix this on their own but really is this security measure worth it?
Here are ways how to fix it or work around it: [http://stream-recorder.com/forum/blocked-wine-start-unix-problem-opening-exe-t6560.html?](http://stream-recorder.com/forum/blocked-wine-start-unix-problem-opening-exe-t6560.html?)

Edit: That blocked didnt come from cd but mounted iso using acetoneiso. And that iso is backup at external harddrive since cds seem to get unusable way too fast and its more convinient that way so dont even start talking about piracy :). So i am unsure if cd & dvds are affected with this problem, have to install more games...

---

### Post by mc4man on 2010-08-08
> Ofcourse people can search around how to fix this on their own but really is this security measure worth it?

In terms of wine and .exe's of any sort the 'security' policy, as currently implemented, is total nonsense.
In the overwhelming majority of cases .exe's are intentionally executed, so a roadblock without a detour becomes worthless.

The user either gives up in frustration or on their own finds the way around and runs the .exe anyway

As far as a cd, if you have a typical fstab entry for the cdrom drive, (possible if following an upgrade path), then the security policy is overridden by the mount options.

(there are some other positives for wine users to having a static, known mountpoint for cdrom drives

---

### Post by Jordanwb on 2010-08-08
What I did was right click the exe, go to Properties, go to the "Open With" tab and add "wine" as the program to run it and it bypasses that annoying "security" feature.

---

### Post by 23dornot23d on 2010-08-08
> 
In the overwhelming majority of cases .exe's are intentionally executed, so a roadblock without a detour becomes worthless.

The user either gives up in frustration or on their own finds the way around and runs the .exe anyway
So very true ..... 
I now find that I use distros that do not block this action ..... its so annoying ..... I have maybe 3 or 4 programs that I use from the Windows Programs area on the C: drive

But it is write protected ..... so no alterations can be done to it from Linux ..... to the properties ...... yet these programs run best from there in another Distro.

Altering the properties ..... what a security feature ..... like asking are you sure .... are you
positive ...... do you really want to run that ..... ( what does this remind you of ) 

Those programs are now unusable using UBUNTU .... unless you want to start using the
command line to get one running. ( is that secure > ? )

I see little point in having development in WINE to make windows programs run ,,,
if the other security developers are trying to stop Windows Programs running ........

Seem's one counters the other  .....

I run multiple OS's so not a problem for me I just log out and use another system

Imagine the majority the ones that only have one system ..... we tell them they can run there programs using WINE ..... then when they get here ..... well you can ,,,, if you jump through a few hoops first ...... as we do not trust you to know what you are running.
_____________________________________________________
Thanks for that link ..... this is what I wanted .... just need to go through each of my latest Ubuntu Distros and change it.
**Solution #4: Change the default launch command**

Edit the default launch command for wine
     
     gksu gedit /usr/share/applications/wine.desktop 
Change from 
     
     Exec=cautious-launcher %f wine start /unix 
onto 
     
     Exec=wine start /unix %f

---

