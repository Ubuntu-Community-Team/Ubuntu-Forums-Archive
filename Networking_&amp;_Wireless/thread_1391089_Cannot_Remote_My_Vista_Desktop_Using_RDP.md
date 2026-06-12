---
title: "Cannot Remote My Vista Desktop Using RDP"
date: 2010-01-26
forum: Networking &amp; Wireless
---

### Post by sdbpastor on 2010-01-26
i am a new user to Ubuntu and Linux for that matter. I am using ubuntu 9.10. I want to remote from my Ubuntu machine into my Vista desktop (Vista Ultimate).

i can do so with ease using the various Ubuntu application through vnc. However, whenever I try to do so through RDP I am unable to do so. When I try to remote into the Vista machine through RDP it will launch the Vista login screen where I enter my user name and password. It always comes back saying that the password is incorrect even though the login is the same that is used to login everyday. 

It doesn't seem to be a firewall problem because I disabled it and get the same results. I also get the same results when using either a wired connection or a wireless connection on the Ubuntu machine.

My normal network consists of the Ubunu notebook, my Vista Ultimate  Desktop (wired to the router) and my Vista Ultimate  Tablet PC on a wireless connection.

I might mention that I can remote using RDP from my Ubuntu notebook into into the Vista Tablet PC with no problem. But not the so with the Desktop. Always fails telling me that I am using an incorrect password. I am the only user on either Vista machine and as far as I can tell everything is set the same on both Vista systems (securrity, remote, etc.) unless I am missing something, which I apparently am.

Not sure if it makes any difference but the Tablet pc has always run Vista but the Desktop was orriginally an XP and for the life of me  I can't remember if I did an upgrade to Vista Ultimate or a clean install since it has been a year or so.

Any ideas why I can't connect to the desktop.

Thanks,
Michael

---

### Post by earthpigg on 2010-01-26
any problems connecting if you set the target computer to login automatically without requiring a password? (not as a solution, but try it temporarily to narrow down possible issues)

is the target login account an admin account? is it on the tablet computer?

does one computer have a software firewall setup, but not the other?

its good that you have two vista computers to work with. it will help us narrow this down quicker. basically, we need to identify what is ***different*** between the two computers at the software level.

---

### Post by sdbpastor on 2010-01-26
> **earthpigg said:**
> any problems connecting if you set the target computer to login automatically without requiring a password? (not as a solution, but try it temporarily to narrow down possible issues)

**I am not at home right now but will check it later.**

is the target login account an admin account? is it on the tablet computer?

**Both Vista machine have only one user account and it is set as administrator on both.**

does one computer have a software firewall setup, but not the other?

**Both Vista computers have firewalls. I have disabled the one on te desktop with no change.**

its good that you have two vista computers to work with. it will help us narrow this down quicker. basically, we need to identify what is ***different*** between the two computers at the software level.

[B]Thanks,
michael[/B]

---

### Post by sdbpastor on 2010-01-27
Earthpigg,

I removed the password from my user account on the vista desktop and rebooted the system. Attempts to remote into the desktop vista still brings up a login screen showing the correct username and asking for a password just as before. Since I removed the password I just hit enter and it comes back and says that the password is incorrect, just as before.

I might add that before I did this I tried to establish a remote desktop connection between the vista tabletpc and the vista desktop with no luck. I have tried this in both  directions to no avail. Cannot remote into or from the desktop. I can still use both VNC and RDP to remote into the desktop from Ubuntu though.

At present I cannot do  any side-by-side comparisons betwen the two vista machines because the power cord connector on the tabletpc quit working and I can no longer power it on since the battery is dead so until I can get that fixed I can only trouble shoot on the desktop.

Michael

---

