---
title: "x server failed to start( New to ubuntu)"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by foots2015 on 2006-07-04
Hi I am brand new to using linux.

Here is my hardware

celeron d 3.06 ghz. (64 bit)
1 gig ram
nvidia geforce 6200 by pny

Here is my problem and since i am new to ubuntu i don't understand jack about what is going on. 

I have tried to install ubuntu with both the 32 and 64 bit from a disk. When I restart the pc the ubuntu screen comes up and asks me to install. I choose start/install. the next thing that happens is a screen comes up with text (loading restricted drivers ... ok, etc) then I get a screen that says <Failed to start the x server would you like to view the x server output to diagnose the  problem , yes, no.> I choose yes, it gives me a screen with a bunch of text and <Ok> next it says, <would you like to view the detailed x server output as well? , yes, no,>. I choose yes. More text comes up with <ok>. After this a new screen comes up with < x server is now disable. Restart GDM when it is configured correctly , ok, >. After this i get a command line with <ubuntu@ubuntu:~$>.

I have tried both the normal install, and the start in safe graphics mode install.


I don't know what to do can some one please help me?

---

### Post by foots2015 on 2006-07-04
*bump*

---

### Post by MiKuS on 2006-07-04
it wants you to run > sudo dpkg-reconfigure xserver-xorg

go through that and see what you can do, as far as i know you may need to choose the vesa driver from the list then it will let you into a destop, you should then google/search this forum for guide/tutorials/howto's written about installing drivers with your card

best of luck :)

edit: you will need to reset your computer with 

> reboot

---

### Post by foots2015 on 2006-07-04
My main problem is that i need to get ubuntu installed in the first place but i don't' know how to install it from the command line. ( i was hoping to install from the desktop like they advertised). The reason that i need to get ubuntu installed to the hard disk is so i can than restart the computer without reseting the, sudo dpkg-reconfigure xserver-xorg, settings. Is it not true that if you are running off the live cd that when i restart the computer it resets the settings? So i guess what i need is to know how to install ubuntu from the command line.

Ps. I am going to download the alternate version of Dapper Drake, and try it.

---

### Post by MiKuS on 2006-07-05
well instead of typing reboot, type this:

startx

if that doesent work try ermm..

/etc/init.d/gdm start

i think it is.

best of luck

---

### Post by foots2015 on 2006-07-05
[QUOTE=MiKuS]well instead of typing reboot, type this:

startx

if that doesent work try ermm..

/etc/init.d/gdm start

i think it is.

best of luck[/QUOTE]

I tried /etc/init.d/gdm start and it said starting gnome... and to the right of it it had failed in red letters.

---

### Post by MiKuS on 2006-07-05
i'm sorry i cannot help anymore :(

---

### Post by tseliot on 2006-07-05
I have already answered here:
[http://www.ubuntuforums.org/showthread.php?t=209184](http://www.ubuntuforums.org/showthread.php?t=209184)

[COLOR="Red"]Please don't start more than a thread for the same problem[/COLOR]

---

### Post by foots2015 on 2006-07-05
sorry im new and i just wanted to get an answer.
thank you both for your time.

---

