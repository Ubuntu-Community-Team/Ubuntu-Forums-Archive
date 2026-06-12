---
title: "Multi VNC Session Security"
date: 2010-09-09
forum: Networking &amp; Wireless
---

### Post by BiffHenderson on 2010-09-09
I have an SSH server setup with port forwarding enabled.  I successfully have 3 users created on the box, and all the users can authenticate to the SSH host.  I've changed the permissions on all three accounts to prevent them from viewing the /home/ folders of other users.  It is also possible to bind a port on localhost to a remote port through the SSH tunnel and open any one of three VNC sessions.  Everything is working perfectly, almost.  

I have a very general question about VNC security.  Basically, I have three different VNC displays that can be accessed through the SSH tunnel operating on ports 5901, 5902, and 5903 or displays :1, :2, and :3.  Each VNC session requires a password, however a username is not required.  When the VNC server starts up (/etc/init.d/vncserver start) the script uses 'su' to switch between users to ensure that each gnome-session is started independent of the other.  I believe that it creates a unique .Xauthority session for each user that starts a display, hence the reason a username is not required (just a host:display) to access the remote interface once you have authenticated to the SSH server.

My only concern with this setup is that any user authenticated to the SSH host can access the VNC session of any other user (provided they know the password for the given display).  I'm curious if there is any way to provide more granular security for VNC connections?  

Here i my current setup: 

SSH Users:
user1
user2
user3

VNC Sessions 
user1:1, user2:2, user3:3

The issue is that if i authenticate with user1 (via SSH), i can still setup the port forwarding (using ssh -L) to access the display of user2:2 provided i know the password (which I do because I created al the accounts).  Is there anyway to outright deny this level of access and restrict user1 to only being allowed to view the session of user1 and nobody else.  I'm not sure if I'm even using the correct terminology.  I'm quite new to Ubuntu administration, and up until a week ago had never attempted to setup a VNC server.  I know I'm being overly paranoid, but I would rest easier knowing that users are restricted to their own VNC session by more than just an 8 character password.

---

