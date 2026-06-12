---
title: "TuxGuitar"
date: 2009-06-13
forum: Multimedia Software
---

### Post by marcwatt@api-partners.com on 2009-06-13
I actually have 3 questions now that i am on here, but the question that prompted me to write concerns tuxguitar. which by the way is the kewlest thing i have found in a long time. i cant find any real good documentation for using the app. so if anyone knows of where to find that...would be great.

#1 how do you do a block copy paste of a measure. for instance i made a bass line in one measure and would like to block paste it for the next 50 measures or so. it seems that i can only do one past at a time. very time consuming...there must be a better way.

#2 different question all together. why does my computer say kubuntu when i first login and i thought i loaded ubuntu and my system says i am runnin ubuntu? strange

#3 when i first loaded ubuntu, i picked the 32bit version on accident when i have a 64bit processor. havent had problems but should i or could i simply upgrade?

#4 can i switch the boot order on startup? i am running vista and ubuntu and i rarely use vista. however it is listed first and if i am not paying attention (quite often) after 5 seconds if i havent chosen an O.S., it starts up vista. would like it to be the other way around.

#5 hmmmmm no #5 i guess. except i would like to say i love this O.S. and the great support i get here at the forum. thanks

i wonder when the last time someone said that about microsoft and vista in particular?

---

### Post by Yoshiman007 on 2009-06-17
for #3, you can not upgrade from 32 bit to 64 bit. You have to do a clean install. I would encourage doing a separate clean install if you wanted to check out 64 bit's advantages and disadvantages(none?). I believe the biggest benefit is the additional RAM it can address and browsing is also supposed to be significantly faster.

for #4, you need to edit your Grub menu. I believe the easiest way to do this is to edit it with root privileges via:
```
sudo gedit /boot/grub/menu.lst
```
Carefully navigate to the end of the file and you can see all of the menu options that you would see on boot up. Simply change the order of the entries and you will have changed the order they appear on your computer when it boots.

Glad to be of service, and i hope your other problems are addressed. (I had the Kubuntu problem after installing Kubuntu as an alternative to Gnome, perhaps you installed a KDE only program, such as Amarok, which may have overwritten your loading screen entry. Either way, I have no idea how to fix that issue)

---

