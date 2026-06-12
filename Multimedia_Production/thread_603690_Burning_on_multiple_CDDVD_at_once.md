---
title: "Burning on multiple CD/DVD at once"
date: 2007-11-05
forum: Multimedia Production
---

### Post by plaindonut on 2007-11-05
Forgive me if I posted on the wrong forum as this is my first post.

I'm looking at making a shell script that allows a user to log on and type the command 'burncds' and with 5 cd burners on, it will pull the images right off the CD's.

There is a GUI application called TurboJet that does exactly what I want but I don't want a GUI app. I want to completely automate the burning process of 5 ISO images I have to be burned on 5 blank CD's.

This works fine using TurboJet so I know everything is working perfectly fine. When I create a shell script, it only processes one line at a time. So it will burn the first CD, after the burn is complete, it moves on to the second CD. Does anyone know how to run a command line that will execute everything all at once? 

Here is the command I'm using - 
cdrecord -v dev=/dev/scd0 image1.iso
cdrecord -v dev=/dev/scd1 image2.iso
etc....

---

### Post by Vavo on 2007-12-01
I am not very expirienced.. try to add & (or space &) at the end of the lines.. it runs the comand in background ?!? so you can use it for second command etc

---

### Post by sethvath on 2007-12-01
Something smells wrong here. Are you running some bootlegging operation or do you really have a mountain of data to backup?

---

### Post by Vavo on 2007-12-05
Is cloning illegal? ;)

I think that from command line you will not achieve the same thing. The software that support burning with multiple recorders at same time, manage to send the same stream to all recorders....here it will be like doing it five times in multi task environment.

---

### Post by sethvath on 2007-12-06
Copying something you own might be legal. I've seen bootleggers argue that they purchased "one" copy of a music disc therefore they are entitled to copy it as much as they want and sell it for a profit.

---

