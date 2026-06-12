---
title: "Frontend not starting any longer"
date: 2014-03-01
forum: Mythbuntu
---

### Post by jrockinl on 2014-03-01
Using MythTV 0.27.  I have 1 backend with 4 frontends.  One of the frontends basically hung up once when I selected the wrong menu item in MythVideo.    The item was changing the view and I hit the one that said "....  slow".  The window went to complete blue (which was the background of the theme I was using) and stayed there all night.  I killed (xkill) the window the next morning when it still didn't respond.  Going back into the frontend, the window would show the background for 1.2 second, then the whole window would disappear and try to reopen, going into an endless loop of crash, restart, crash restart...

I started it from a terminal and saw something along the lines of "waiting for lock" scrolling in the terminal.  I saw some tips somewhere where I could reset he frontend database with "mythfrontend --reset".  I did that and from then on, I got the background of the default theme (tan) and then crash, reset, crash, reset,... 

Now I think whatever is causing the problems must be on the backend database because I "sudo apt-get purge mythtv" and then re-installed and the problem was still there.  Next I did a freash install of linux and mythtv and the problem still shows up.  The other 3 frontends are working without any trouble.  How would I clear our any frontend information residing in the backend database?  If it wouldn't be there, what else could keep the problem going though a complete install?

---

### Post by blm-ubunet on 2014-03-02
That slow option was most likely the view the uses direct file/folder scanning/access.

Possible cause:
Do you have any samba/nfs/cifs file/folders shared from the backend(s) to the problem FE ?
The FE video folders path/list must not overlap/contain any files from the defined storage groups (BE).
Media files in defined BE video storage groups are available to FE via streaming mythprotocol.

Find cause:
start the FE from terminal with:
mythfrontend -v all --loglevel=debug > problemFElog.txt
then read or post the logfile..

Ugly workaround:
Try starting problem frontend as a new FE identity by setting/changing the localhostname.

I'm sure it will be possible to craft an SQL cmd to reconfigure the FE mythvideo settings..I'll try to come up with a tested soln..

---

### Post by jrockinl on 2014-03-02
Thanks for the ideas.

I do use nfs for movies I have stored on a NAS but that is only being mounted on the backend.  I did think about changing the network address of my remote frontend but never thought about just changing the name of it.  Ultimately, I didn't change the network because that would have lead to having to make changes on many other machines so I tried another option first.

The other idea was rebooting the backend and that got me passed the issue on the remote frontend.  I should have thought of this idea much sooner but oh well, things are great again now.

---

