---
title: "help with screen resolution"
date: 2008-12-22
forum: Multimedia Software
---

### Post by suggsville on 2008-12-22
I have a problem, and i am new to ubuntu. I have a
SiS Mirage 3 Graphics card and a Generic PnP Monitor. The problem is that on my windows partition my screen can run upto 1280x800 but with the Ubuntu 8.10 the highest resolution i can run is 800x600 which is a real pain. Is there anyway of improving my resolution so that it is something closer to what my Windows Vista resolution is? As i said i am a complete newbie so any help would be appreciated.

---

### Post by wolfen69 on 2008-12-22
go to applications>accessories>terminal. type in: ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` hit enter, give password, (will not show up) then reboot.

---

### Post by suggsville on 2008-12-22
thanks for the tip, it didnt work though. I know the graphics card is pants, is there any type of driver update that i could try or something along those lines? Its not had any driver update/change since the laptop came out of the box.

---

### Post by XPuntu on 2008-12-22
The dpkg command never seems to work for me. Take tonight for example.

Anyway, do you have 'Screens and Graphics' enabled as a menu item under "Applications>Other"? I would try changing the resolution there first. However, I find that after running the dpkg command, "Screens and Graphics" won't launch. 

After going through the dpkg routine, reboot your machine and if you're lucky (like I was tonight), a routine will come up asking you to select your monitor and graphics card. If you do get that option, don't try "test". It also doesn't seem to work well. 

Once you get to your login screen, you'll hopefully have your resolution just as you want it.

This is my non-scientific tutorial by the way. I don't know why I have the trouble I do but this has worked for me lately....

Hope it helps.

---

### Post by suggsville on 2008-12-22
just tried that last idea, still no good. im beginning to wonder why im leaving Vista!

---

### Post by coolethan on 2008-12-23
> **suggsville said:**
> just tried that last idea, still no good. im beginning to wonder why im leaving Vista!
because Vist sucks! do you have any other version of ubuntu on a disc or anything like that?

if not you can try editing the xorg.conf file which holds all the information concerning screens and graphics and monitors and screen resolution.

---

### Post by suggsville on 2008-12-23
as i said im new. this is the first ubuntu i have got. How would i go about editting the xorg.conf file? and what would i need to change and hw etc?

---

### Post by coolethan on 2008-12-23
[http://www.linuxforums.org/forum/mandriva-linux-help/49485-how-do-i-edit-xorg-conf.html]("http://www.linuxforums.org/forum/mandriva-linux-help/49485-how-do-i-edit-xorg-conf.html")

i was never very good at editing the xorg.conf file directly but this forum thread can help you.

---

### Post by suggsville on 2008-12-23
that site is useful, except it does not help me. I still do not know what i have to change and how, in fact when i run the xorg.conf it has no driver info. Does this mean i have no driver installed for my graphics card (this bloody SiS Mirage 3)?
When i run the System-administration-Hardware Drivers option, it only only lists my Wireless LAN card. what does this mean?

---

### Post by coolethan on 2008-12-23
it very well could be that you don't have a driver installed, heck! i never ever had a driver for my rage 128 graphics card for the whole 8 months i've used ubuntu. did you follow what the site told you? when you type in those codes you should just be able to go and in place of 800x600 type in whatever your resolution should be. i wish i could be of more help man.

---

### Post by suggsville on 2008-12-23
yeah i did what the site said, but it ill wouldnt allow me to change the reslution. If i had a driver installed other than the xorg.conf fle, how would i know? And if i don't have one installed, where is the best place to get one that will actually work?

---

### Post by coolethan on 2008-12-23
ok if you need to get a driver i would suggest the NVIDEA website, that is if your graphics card is an NVIDEA card. from there i will redirect you to this thread. [http://ubuntuforums.org/showthread.php?t=1019762]("http://ubuntuforums.org/showthread.php?t=1019762")

---

### Post by suggsville on 2008-12-23
my driver is a SiS Mirage 3, not Nvidea unfortunately. What does it mean if this comes up

 [ Error writing /etc/X11/xorg.conf: Permission denied ]
it says this when i try to save the xorg.conf file.

---

### Post by coolethan on 2008-12-23
what that means is that the computer is trying to protect itself from someone going in and potentially screwing up nesacary files. so you need privaledges beyond the regular user, depending on what your trying to do you will either have to type in sudo and then the command or log in as root. are you working from the terminal?

---

### Post by suggsville on 2008-12-23
yeah working from terminal, that a bad thing? how else could i attempt to run xorg.conf?

---

### Post by robtg on 2008-12-23
If you're not running the latest version (8.10), try opening a terminal session and type displayconfig-gt.  This should start an application that lets you select your graphics card and monitor resolution.  Unfortunately, this command has been removed in most recent Linux distributions because X11 is supposed to have better monitor detection (to me it doesn't).  I wish Canonical would put it back.  It made monitor resolution problems so easy to solve.

-Rob

---

### Post by coolethan on 2008-12-23
it's 8.10 so there is not displayconfig-gtk. just make sure you type sudo before the comand and it should save it. you could attempt to go to that file directly and open it that way and make the adjustments. go to places--computer--file system--etc--X11 and theres the file called xorg.conf

---

### Post by suggsville on 2008-12-23
It still wont let me save any changes i make, i still do  not have authorization. Is there a way to make it so i do have authorization? Or another xorg.conf unrelated way of getting the resolution sorted ie a SiS Mirage 3 driver?

---

### Post by coolethan on 2008-12-23
i think you need to log in as root. you can do this through the terminal by typing
```
su 
```
or
```
su -
```
the latter is full root, i like to use the first one because it logs me in as root but i'm still loged in as me. root and you are two different users so the things you have on your desktop will not be there for root so the first code gives you root privaleges but doesn't stray away from your user. you need to put in the password for root which should be blank by default and if not then you can change it by going system--admin--users and groups, click unlock and then select root and preferances on the side. hopefully that works, if not you may have to log in to the computer as root from the login screen which by default isn't aloud so system--admin--login window. select the security tab and then check the allow local system admin login box. then log out or switch users and you can login as root but set up a root password first.

---

### Post by suggsville on 2008-12-23
great. i managed to save the new xorg.conf file as a root user. only way to know if it worked, and to see if i did something right, would be to reboot the system. Whats next though if this doesnt work?

---

### Post by suggsville on 2008-12-24
Wonderful. Brilliant. Thank you Mr coolethan. Doing a minor tweak as the root user in the xorg.conf file has sorted the issue by the looks. It may not be exactly what my Vista uses 1280x800, but 1280x768 is good enough! Problem sorted.

---

### Post by coolethan on 2008-12-24
i wish i knew, i could try even setting up a xorg.conf file the way i have for your settings and then send it to you some way. other than that i'm out of ideas.

---

### Post by coolethan on 2008-12-24
> **suggsville said:**
> Wonderful. Brilliant. Thank you Mr coolethan. Doing a minor tweak as the root user in the xorg.conf file has sorted the issue by the looks. It may not be exactly what my Vista uses 1280x800, but 1280x768 is good enough! Problem sorted.
*bows* thank you, thank you, i'll be here all week! glad i could help. mark the thread as solved don't forget.

---

