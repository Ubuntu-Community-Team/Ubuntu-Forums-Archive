---
title: "Samba server not accessible from WinXP"
date: 2011-02-01
forum: Mythbuntu
---

### Post by Epiphyte on 2011-02-01
I have just replaced the CPU in my Mythbuntu box with a more powerful unit ( it fixed the video stutters on playback).

I have also restored my XP system from a backup. The Samba server is no longer accessible from this machine. It is, however, visible from other computers as part of the MSHOME workgroup (I guess this is the default).

How can I reconfigure the Mythbuntu machine to be part of my workgroup?

P.S. I have enabled NetBIOS over TCP/IP.

---

### Post by nhtrader on 2011-02-04
The place to effect changes to the samba server is in its configuration file:

sudo pico /etc/samba/smb.conf

My advice is to first copy this file before you make any changes. This way if you mess it up you can revert back to the original. It's highly sensitive to changes.

However, any time you make a change to this file you are required to restart the samba server

enter terminal mode
sudo su
 Restart comand: /etc/init.d/samba restart (This one command should do it, but sometimes you need to use stop then start)

Start command: /etc/init.d/samba start
Stop command:/etc/init.d/samba stop

Presuming you are using Mythbuntu, I can tell you that the standard samba config file uses ...

workgroup = MSHOME

Plus within the smb.conf is a parameter for the location of samba's log. Viewing this log file may provide you with a clue. Secondly, you could increase the level of logging entries if you need it. Plenty of resources explaining howto smb.conf

---

### Post by newlinux on 2011-02-04
Just an FYI, Ubuntu is using upstart and moving away from init scripts. The proper way to restart samba in later versions of ubuntu is

sudo service smbd restart

if for some reason samba isn't already running, this won't work. you would need to use just:
sudo service smbd start

you can stop it by doing the following
sudo service smbd stop


(or even sudo restart smbd)
But as said above, change the workgroup to be the same as your win computers, restart samba and that should hopefully get you going.

---

