---
title: "Problem getting past login screen"
date: 2006-07-28
forum: Multimedia &amp; Video
---

### Post by brownbear on 2006-07-28
Once I enter my username/password into the box the screen goes blank.  There's only a mouse cursor.  However I can log in on the command line...  so I've tried to reconfigure my xorg by doing ```
sudo dpkg-reconfigure xserver-xorg
```, and I've tried ```
sudo dpkg-reconfigure --all
```.  Upon completion they didn't seem to do anything.  I also tried changing /etc/X11/xorg.conf The section Device has a variable Driver which currently says *nvidia*.  I changed that to nv but the system complained a lot.  I couldn't even see the login screen when I did that.  So I changed that back to nvidia.  

Can anyone work out how to solve this problem?

distro = ubuntu 6.06
cpu = p4 1.5
ram = 512mb
gpu = 64mb geforce 3

Thanks in advance,
bb.

---

### Post by FenrisAbraxas on 2006-07-28
> **brownbear said:**
> Once I enter my username/password into the box the screen goes blank.  There's only a mouse cursor.  However I can log in on the command line...  so I've tried to reconfigure my xorg by doing ```
sudo dpkg-reconfigure xserver-xorg
```, and I've tried ```
sudo dpkg-reconfigure --all
```.  Upon completion they didn't seem to do anything.  I also tried changing /etc/X11/xorg.conf The section Device has a variable Driver which currently says *nvidia*.  I changed that to nv but the system complained a lot.  I couldn't even see the login screen when I did that.  So I changed that back to nvidia.  

Can anyone work out how to solve this problem?

distro = ubuntu 6.06
cpu = p4 1.5
ram = 512mb
gpu = 64mb geforce 3

Thanks in advance,
bb.

try sudo /etc/init.d/gdm restart and check dmesg.

Another thing you can do is 

startx 

and see the output

What DE are you using gnome? kde?

---

### Post by heimo on 2006-07-28
> **brownbear said:**
>   I changed that to nv but the system complained a lot.


Try if changing it to *vesa* works.

---

### Post by brownbear on 2006-07-28
> **FenrisAbraxas said:**
> try sudo /etc/init.d/gdm restart and check dmesg.I've done /etc/init.d/gdm restart pre logging in - it doesn't appear to help.  However once the screen goes blank, if I type that in from the command line it takes me back to the login screen.

I'm also not sure how to check 'dmesg.'  How would I do that on the command line?
> **FenrisAbraxas said:**
> 
Another thing you can do is 

startx 

and see the output Here is the output from typing startx:
xauth: creating new authority file /home/harsha/.serverauth.6404

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.
Xlib: connection to ":0.0" refused by server
Xlib: Invalid MIT-MAGIC-COOKIE-1 key giving up
xinit: unable to connect to X server
xinit: No such process (errno 3): Server error.


> **FenrisAbraxas said:**
> What DE are you using gnome? kde?I'm not sure what a DE is or how to find that out?

> **heimo said:**
> Try if changing it to *vesa* works.When I did that and went back to the f7 screen the monitor was sort of 'off.'  I could hear the static and there was no signal at all.  So I changed it back to nvidia.


General apologies for my lack of understanding.  

Thanks for trying,
bb

---

### Post by Yokabi on 2006-07-31
sorry to report i have the same problem...
i can only access my desktop by pressing ESC at boot and then running safe mode then typing in "startx" - that will only give me root user profile and not mine...help needed


EDIT: found the problem...zero disk space...now everythings back as it was before

---

