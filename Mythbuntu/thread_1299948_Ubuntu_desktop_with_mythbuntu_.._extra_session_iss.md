---
title: "Ubuntu desktop with mythbuntu .. extra session issue"
date: 2009-10-24
forum: Mythbuntu
---

### Post by AJ1000 on 2009-10-24
I tried to make a clean installation of the Mythbuntu 9.10 Release Candidate, and installed the ubuntu desktop from the Mythbuntu Control Center. The issue is that it produces an extra session.

How do I get rid of the extra session?

Here is the output of ck-list-sessions:

Session1:
	unix-user = '103'
	realname = '(null)'
	seat = 'Seat1'
	session-type = ''
	active = FALSE
	x11-display = ''
	x11-display-device = ''
	display-device = '/dev/???'
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-10-24T17:05:24.110037Z'
	login-session-id = ''
Session4:
	unix-user = '1000'
	realname = 'owner'
	seat = 'Seat1'
	session-type = ''
	active = TRUE
	x11-display = ':0'
	x11-display-device = '/dev/tty7'
	display-device = ''
	remote-host-name = ''
	is-local = TRUE
	on-since = '2009-10-24T17:06:38.167940Z'
	login-session-id = ''

Session1 should not there (it was not there in 9.04, or the upgrade I did from 9.04 to 9.10).

The reason I need to get rid of the session is otherwise, when shutting down or restarting, I get the following PolicyKit error:

'System Policy prevents stopping the system when other users are logged in'

How do I get rid of the extra session?

---

### Post by al_do_at_work on 2009-10-26
try this, it worked for me

create a new file with:
[FONT=monospace]
[/FONT]sudo nano /var/lib/polkit-1/localauthority/50-local.d/shutdown.pkla

paste inside this:

[system shutdown privs]
Identity=unix-group:**users <-- your users group here**
Action=org.freedesktop.consolekit.system.stop-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

then create this too:
sudo nano /var/lib/polkit-1/localauthority/50-local.d/restart.pkla

and paste this:

[system restart privs]
Identity=unix-group:**users <-- your users group here**
Action=org.freedesktop.consolekit.system.restart-multiple-users
ResultAny=no
ResultInactive=no
ResultActive=yes

taken from: [http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Granting_Shutdown.2FRestart_Privileges_to_Users](http://wiki.archlinux.org/index.php/Gnome_2.28_Changes#Granting_Shutdown.2FRestart_Privileges_to_Users)

---

### Post by AJ1000 on 2009-10-26
Is there a way of identifying the users group? The above sessions were made by the mythbuntu installation.

---

### Post by AJ1000 on 2009-10-26
Thanks, it works. The users group was mythtv

---

### Post by johnnybirdman on 2009-10-29
> **al_do_at_work said:**
> try this, it worked for me


worked great, thanks.  Had this issue on a fresh install.  Should this be considered a bug? On a fresh install what 'other' user is running?

J.

---

### Post by AJ1000 on 2009-10-29
Yes, I think this is a bug. The other user is user 103 - which is the mythtv group.

---

### Post by hoffman462 on 2009-11-01
Does anyone know how to get rid of the session? or is it required for Myth to operate?

---

### Post by AJ1000 on 2009-11-01
I think it is required now as myth backend is part of the mythtv group

---

### Post by Bage2010 on 2010-01-20
Hi

just wanted to say this post was really helpful. Have been running karmic exactly a week now and got this problem after installing Mythtv.

cheers

---

### Post by skorpio11 on 2010-02-02
Just wanted to say thanks as well. Maybe this should be a sticky some place.

---

