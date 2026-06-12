---
title: "MythTV Frontend - Wrong package - Whoops!"
date: 2007-05-16
forum: Multimedia &amp; Video
---

### Post by pommattski on 2007-05-16
I've gone and created a problem for myself...

I have Feisty running with a MythTV Frontend and Backend on one machine, and wanted to install a MythTV frontend on my main desktop machine which is already running Feisty.

It should have been  easy, and it was... It's just that I installed (using apt-get install) ubuntu-mythtv-frontend instead of simply mythtv-frontend.

ubuntu-mythtv-frontend has installed and configured the frontend correctly, and it works, but it starts MythTV at login, and has also setup the MythTV user to login automatically.

Can I simply apt-get remove ubuntu-mythtv-frontend?... will it remove and reconfigure everything as-was?... or will I end up in a big mess?

Thanks for any advice,
Matt

---

### Post by NT4usB on 2007-05-16
You could uninstall it.
Or,  just set it up to run as your user.
I fumbled through the process when I added a Edgy box to my network and pointed it at my Dapper Mythbox.
You'll need to move and/or edit mysql.txt, fix some permissions and group issues,  but it can be done...
You'll have to do some of this anyway to get any install of myth to run as another user.

---

### Post by pommattski on 2007-05-17
Thanks, NT4usB...

OK.  If I'm quick, and log myself in before the mythtv user automatically logs in, I can use the MythTV front end because I'm in the mythtv group.... So I guess I can leave that side of things as they are.
The big issue, though, is that the frontend starts automatically, even before user login.  This is a problem because the remote backend/server is not always be running, therefore the frontend, unable to connect to the backend/database, automatically starts the frontend setup procedure (asking for db details etc...).

So...  what I need to do is:
1.  Stop the frontend from starting automatically.
2.  Stop the mythtv user logging in automatically.
I'm a bit of a newbie at this stuff, so if anyone can point my in the right direction, that'd by great.

Cheers, 
Matt.

---

### Post by Titus A Duxass on 2007-05-17
What you need to do is something along the lines of:

1. Remove the installed ubuntu-myth-frontend
2. Install the normal frontend
3. Forget about auto-logins

You should then be able to log-out as normal user, login as user mythtv and start the frontend from the command line.

You may want to set mythtv password to something you can remember and I think you will have to run mythtv-setup as user mythtv.

---

### Post by pommattski on 2007-05-17
Cheers Titus.

Looks as though I was worrying about nothing...

Removing ubuntu-mythtv-frontend removed the auto-login.
I then removed mythtv-frontend and mythtv-common which were also installed originally by the above meta-package. Searching packages.ubuntu.com helped me identify other files installed by the package, which I then deleted... Rebooted.... All gone.
Installed the standard mythtvfrontend again, configured, and its behaving just right now. 
Sorted. 

Just for additional information:  When the frontend is started by a normal user, it gives you the option of adding that user to the mythtv group, making logging in as user mythtv unnecessary; in fact there is no user called mythtv on this installation

---

