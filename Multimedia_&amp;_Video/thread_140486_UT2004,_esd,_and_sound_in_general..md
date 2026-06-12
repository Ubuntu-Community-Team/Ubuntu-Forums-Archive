---
title: "UT2004, esd, and sound in general."
date: 2006-03-06
forum: Multimedia &amp; Video
---

### Post by pbaehr on 2006-03-06
My installation of Unreal Tournament 2004 works most of the time but periodically when I restart it a second or third time the sound is not present.

I can fix this using
```
killall esd
```
and the sound comes back on fine.

When I exit the game I run
```
esd
```
to get the sound back for the rest of the system and I get an error. I'm not at my computer so I can't remember the error. Rebooting the computer starts it back up like I'd expect.

What I'd really like is for someone to point me in the direction of an FAQ or some   document that discusses the sound system on Linux. ESD, OSS, ASLA, and all that. I'd like to get a better idea of what's actually going on. For example, is my computer using all of these? Just one at a time? What's the difference between them. Things like that. Thanks!

---

### Post by DarkED on 2006-03-06
Try adding this to the ut2004 shell executable.

You will see something like this --> #Prefs the users starting preferences

Under that line add this:

sleep 5

This is the soundfix for Unreal Tournament GOTY, and should work for you also.
Good luck!

---

### Post by pbaehr on 2006-03-06
Incredibly simple, but why does it work?

Well, I'm assuming it will work. I won't be able to test it for 2 hours or so.

What is it pausing momentarily to allow for? I'm still on my quest to actually understand the sound system in Linux.

---

### Post by pbaehr on 2006-03-09
Just to follow up, after 2 days of testing (since it only does it sometimes) it seems the "sleep 5" fixed the trouble with ut2004, though, I'd still like to know what it is waiting for.

---

### Post by CameronCalver on 2006-05-16
when i run ut2004 i has sound but if i quit it then get back into it it doesnt i have to log off or restart computer and it will be fine any1 no a solution

---

### Post by Rosenrot on 2006-06-21
[QUOTE=DarkED]Try adding this to the ut2004 shell executable.

You will see something like this --> #Prefs the users starting preferences

Under that line add this:

sleep 5

This is the soundfix for Unreal Tournament GOTY, and should work for you also.
Good luck![/QUOTE]


how do you open the ut2004 shell executable? then how do you add sleep 5 underneath #Prefs the users starting preferences?

---

### Post by Rosenrot on 2006-06-22
?

---

### Post by Rosenrot on 2006-06-26
i found out how to open my ut2004 shell executable with a text editor but i don't see ANYTHING like this 

#Prefs the users starting preferences

could someone please help?

ive only gotten sound once and that was yesterday
and i try to recreate the sam conditions as it was when i started it succesfully but it won't work : /

---

