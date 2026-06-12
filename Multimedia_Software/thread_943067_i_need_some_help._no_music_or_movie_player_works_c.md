---
title: "i need some help. no music or movie player works correctly"
date: 2008-10-09
forum: Multimedia Software
---

### Post by dazift on 2008-10-09
i usualy use amarok for music and from the start that went very slow whenever i run it, it keeps looking for new music and slows everything down. but i dont care much for amarok. i switched over to audacious wich is really cool because i am used to winamp and that worked really well until a few days ago when the visualizer didnt work right but i didnt mind and kept on using it then one time it closed and i could never reopen it again. i tryed everything from removing and installing to reinstalling but nothing changes it. also movie player does not work, when i open it my screen goes black and i cant do anything. i also tried reinstalling that with no luck. i also tried rhythmbox but that froze up my computer at that point i was frustrated and now im writing this. this is on my compaq presario c700 if you need to know anything else about it just ask. i really need your help because i have no idea what else to do. thanks.

---

### Post by doas777 on 2008-10-09
don't take this as verse, but it sounds to me like it could be a progressive hardware failure. what temp is your CPU running at?

just a shot in the dark. do some diagnostics and see what comes of it.

---

### Post by soumyajit pramanick on 2008-10-09
hi, i dont know about how to fix movie player and rhythmbox(i am having same prob with rhythmbox) but i guess i have a solution for audacious.

1. first uninstall audacious

2. go to your home folder

3. hit ctrl+H (you will see the hidden folders)

4. delete the folder named .audacious

5. reinstall audacious.
this should fix it.

---

### Post by dazift on 2008-10-10
after uninstalling tried to look for .audacious, couldnt find it. reinstalled nothing changed. even when it is installed i still cant find that folder... idk what that means, im somewhat new to linux. 

my computer runs at a very moderate temperature. idk exactly what it runs at but when i run vist the computer seams to get a lot hotter than when i run ubuntu

---

### Post by fib1807 on 2008-10-10
U knw what ? I think if rythmbox gets dim and also amarok u might prolly want to reduce the grafic effects via gnome-appearane-properties and/or reduce the mtu of local interface (do this if u have problems with firefox getting dim and many other things getting dim etc..otherwise believe me it'll RUIN the case)


1.first check if u have lo interface using sudo ifconfig
2.then check the number of MTU (mine's arnd 16000 odd and it's ideal) 
but meddling it may sometimes (only sometimes give better performance)

command to change lo interface's mtu:
sudo ifconfig lo mtu <desired value>

just reduce it to 10000 as a start value and change it untill u get satisfactory results.

---

### Post by dazift on 2008-10-10
ok i found the file in .config and deleted it and that fixed the problem. thank you!! by any chance do u know if i can find a similar thing for amarok

---

