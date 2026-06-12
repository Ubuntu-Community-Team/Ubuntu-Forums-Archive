---
title: "Need some guidance with VNC4Server"
date: 2013-05-21
forum: Networking &amp; Wireless
---

### Post by DarkApollo on 2013-05-21
Im not really new to Ubuntu, but I am new to the server side of things and I need some help with a few programs, and before I go mucking about on my production server I want some extra guidance. I have read though every forum post that google would bring up, and every FAQ/ how-to guide that I can find, but none answer my questions because they pertain to different services or programs, or I just do not have the xxxxx.conf files that they are calling for to edit.

A few weeks ago I set up a Ubuntu Server, and since my other admins are beyond novice to Linux, I installed xubuntu desk top. I installed VNC4server and use tightVNC from my windows 7 laptop to access the GUI when I need to. Here are the issues I am running into with that. 
To start the server I HAVE to type (through my ssh tunnel):
> user@userlocation~:$ sudo vncserver

New 'labs.userlocaton.net:1 (root)' desktop is labs.userlocation.net:1

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/labs.userlocation.net:1.log

Fine, great, wonderful, except for the (root). I do not want my other admins having access to /root when they are in the GUI. I trust them not to muck up a Windows Server enviro, but some of them know too little about Linux to not break it. 

If I type:
> user@userlocation~:$ vncserver
vncserver: Wrong type or access mode of /home/user/.vnc.

Now, I have tried to use 'su', I have tried to edit the .conf files, I have tried to change permissions on the /.vnc etc.. Nothing is allowing me to run vncserver from the user prompt with out SUDO, and I think that is the root cause (pun intended). 

Aside from that, it has also developed a horrible authentication kick back. For the past 2 weeks, VNCServer was auto starting when ever the server was rebooted (which was about once a day since things were getting updated and installed), now that Redmine is up and running and the reboots are as few as possible, VNCServer is no longer autostarting (even though it is in the .rc) and every session needs to be -kill and restarted or it will give an authentication error. This never happened in the past two weeks and only started on monday morning when I got a frantic phone call from my web admin. Having un-did all of my changes trying to get vnc to NOT start as root, I doubt that is the cause. TightVNC is just not asking for the login permissions unless the vncserver session is killed and restarted.

---

### Post by steeldriver on 2013-05-21
Maybe invoking vncserver with sudo has caused your ~/.vnc files to be owned by root? here are the ownerships and permissions on mine

```
$ ls -ld ~/.vnc
drwxr-xr-x 2 user user 4096 May 21 16:27 /home/user/.vnc
$ 
$ ls -l ~/.vnc
total 32
-rw-rw-r-- 1 user user 9304 May 21 09:41 my-server:5.log
-rw-rw-r-- 1 user user    6 May 16 12:00 my-server:5.pid
-rw------- 1 user user    8 May 25  2012 passwd
-rwxr-xr-x 1 user user  940 May 16 11:58 xstartup


```

---

### Post by DarkApollo on 2013-05-21
Thats what I was thinking too.. 
On mine it seems to be owned by root in user group. I have tried to change the permissions but then I get the .Xauthority error. 
Unless I was on the right track and just needed to follow through with permissions changing. 
```
user@labs:~$ ls -ld ~/.vnc
drwxrwxr-x 2 root user 4096 May 21 16:27 /home/user/.vnc

user@labs:~$ ls -l ~/.vnc
total 28
-rw-r--r-- 1 root root 7534 May 21 16:54 labs.userlocation.net:1.log
-rw-r--r-- 1 root root    5 May 21 16:27 labs.userlocation.net:1.pid
-rw-r--r-- 1 root root 1035 May 21 11:51 labs.userlocation.net:2.log
-rw-r--r-- 1 root root 1035 May 21 16:05 labs.userlocation.net:3.log
-rw------- 1 root user    8 May 20 17:20 passwd
-rwxrwxr-x 1 root user  360 May 14 17:22 xstartup


```

-=EDIT=-
I went and:
```

user@labs:~/.vnc$ sudo chown -R user /home/user/.vnc
user@labs:~/.vnc$ vncserver
xauth:  /home/user/.Xauthority not writable, changes will be ignored

New 'labs.userlocation.net:2 (user)' desktop is labs.userlocation.net:2

Starting applications specified in /home/user/.vnc/xstartup
Log file is /home/user/.vnc/labs.userlocation.net:2.log

```

Now its rejecting my connection to 5902. The port is open (5901, 2, 3 are open to listening).

---

### Post by steeldriver on 2013-05-21
... likely because X (as invoked by sudo vncserver) also created a root owned ~/.Xauthority file - that should be

```
$ ls -l ~/.Xauthority
-rw------- 1 user user 639 May 21 16:23 /home/user/.Xauthority

```

You can safely delete it if it's become root owned - it will be recreated with the correct ownership / permissions when you successfully invoke vncserver as user

---

### Post by DarkApollo on 2013-05-21
Ah, this is the issue I had the last time I had set the permissions to the user. Now I get a grey screen with an X for a cursor.

---

### Post by steeldriver on 2013-05-21
That's likely to do with your ~/.vnc/xstartup file - if it can't start your chosen session it may be falling back to something like a solid gray xsetroot plus default x-window-manager.

Remember VNC performance tends to suffer with heavyweight desktops - I never got the 3d Ubuntu session to work at all, ubuntu-2d works OK on my small LAN - but for my work server I stick with xfce or openbox

---

### Post by DarkApollo on 2013-05-21
Which is strange because it worked when started as SUDO under user, just changing the permissions should not have effected the xstartup. I checked the /etc/hosts and that is correct with 127.0.0.1 localhost <computer name>


I removed the xstartup file and reran the vncserver to generate a new  one. It came up with an options screen the first run through, I killed  it, then edited the file, and it is giving the same issue.

Steel, I know youve dealt with that before because one of the previous threads dealing with the issue I have bookmarked and you have a lot of posts in that one. Most of the suggestions add a gnome desktop in the mix. I dont really want to add another desktop GUI to the server, last time I did that the server locked up trying to display a GUI and corrupted the user directories. 

-=EDIT=-
Could it be because /etc/X11/Xserver is owned by root?

-=EDIT 2=-
My .log file
```

Xvnc Free Edition 4.1.1 - built Feb  5 2012 20:04:02
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc


Tue May 21 20:28:08 2013
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
Option "--login" is no longer supported in this version of gnome-terminal; you might want to create a profile with the desir$

(x-window-manager:3127): xfwm4-WARNING **: The display does not support the XRender extension.

(x-window-manager:3127): xfwm4-WARNING **: The display does not support the XComposite extension.

(x-window-manager:3127): xfwm4-WARNING **: The display does not support the XDamage extension.

(x-window-manager:3127): xfwm4-WARNING **: The display does not support the XFixes extension.

(x-window-manager:3127): xfwm4-WARNING **: Compositing manager disabled.

(x-window-manager:3127): xfwm4-CRITICAL **: Xfconf could not be initialized

(x-window-manager:3127): xfwm4-WARNING **: Missing data from default files

Tue May 21 20:28:28 2013
 Connections: accepted: 0.0.0.0::38143
 SConnection: Client needs protocol version 3.3


```

That last section is not (x-window-manager) is not in the last log file created while it was root.

---

