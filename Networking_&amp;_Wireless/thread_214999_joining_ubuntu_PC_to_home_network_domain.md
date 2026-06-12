---
title: "joining ubuntu PC to home network domain"
date: 2006-07-13
forum: Networking &amp; Wireless
---

### Post by devpatel on 2006-07-13
i have a network domain at home at the moment and am trying to connect my ubuntu computer to it...ive assigned a static I.P. to this machine and have tried to connect it to my domain named kerai.co.uk

i looked at my windows xp network places and found that my linux machine was in its own workgroup of Mshome....i also have another icon with Mshome of Kerai, which is where i want my linux computer to show up.

i currently do have internet connection on this(linux) machine and but cannot connect to my other hosts.. ive just installed Samba and have no idea how to use/configure it and where to find an icon for it   if any..

thanks in advance..


__________________________________________
newbie to linux- Ubuntu 6.06 - Dapper Drake.....i think...how do you find out??

---

### Post by Paerez on 2006-07-13
edit "/etc/samba/smb.conf" and change this line:
```
 workgroup = MSHOME
```
to your workgroup (domain)

then restart samba (I think its "sudo /etc/init.d/samba restart")

---

### Post by devpatel on 2006-07-13
Thanks for that.....but i got 3 more problems
1. in my File browser, on the left shows the user, Desktop and File system. Is there anyway i can also make it show Netork or something like that. i tried to drag it from the menu but i didnt work

2. on my XP computer, when i go to my network places, i still see Mshome even though theres nothing in it...i also see Mshome on te linux computer aswell...how do i get rid of this....i havent rebooted my system yet which i think should resolve the problem..

3. when i want to access files from another local machine, i have to type in a username(which usually comes up with the linux user/previously entered user by default) the password and i have to keep typing in the Workgroup whick is kerai. but the default which comes up is 'WORKGROUP'. is there anyway i can change that so the default for workgroup is kerai..

thanks again for your help

---

### Post by Paerez on 2006-07-13
Sorry I don't know about the rest of that stuff (except I think you are right about the reboot for #2), I don't use samba that extensively.

---

