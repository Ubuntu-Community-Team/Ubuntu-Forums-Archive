---
title: "Problem with screen refresh rate"
date: 2008-12-28
forum: Multimedia Software
---

### Post by 2serious on 2008-12-28
Well... newb issues >_<.

I just installed ubuntu and it was working fine but i started experimenting without knowing and ended messing it up. I change my screen refresh rate to 75 herts (which is what i use in Vista) and now my monitor says that input isnt suported and i dont know how to change it back since i cant see anything.

Any help please???



Remember im a complete new user with ubuntu, so please bear with me, im using a NVIDIA GEforce 6150se nforce 430 and an HP 17" LCD monitor

Thanks in advance for any thing you can tell me.

---

### Post by 2serious on 2008-12-29
Help please!!!!!!

---

### Post by gettinoriginal on 2008-12-29
When you start your machine you'll get a message like "press esc to enter the menu". Press escape.  Follow the directions at the bottom to obtain a command line.  If all things went well. you'll get a login prompt. login as user, next sudo -s to get a root shell next thing you have to do is reconfigure your xorg. You can do that with the next command:dpkg-reconfigure xserver-org, look for your refresh rate and edit it. (for more info look here:  [http://www.mepis.org/docs/en/index.php?title=Dpkg-reconfigure_xserver-xorg](http://www.mepis.org/docs/en/index.php?title=Dpkg-reconfigure_xserver-xorg)) Test it with the command startx. If all is ok reboot .done. Good luck. :P

---

