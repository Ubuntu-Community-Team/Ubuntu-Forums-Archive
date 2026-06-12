---
title: "Installed MythTV: can't find master backend-server issue"
date: 2007-02-11
forum: Multimedia &amp; Video
---

### Post by billdotson on 2007-02-11
I have MythTV frontend, backend, database installed along with themes and all the plugins.  I have no TV Tuner as of right now but I have MySQL and MythTV installed.  

When I am in MythTV it says cannot connect to the master backend-server is the IP address correct in the setup menu.  The IP in the setup is 127.0.0.1 which is what I need it to be (my PC) I cannot see guides and I have tried doing the following in the console to populate the database

gksudo gnome-terminal
/etc/cron.daily/mythtv-backend

and sudo /etc/cron.daily/mythtv-backend

but with both I get 

Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

How do I get this MythTV setup? I would like to have it running by the time my TV tuner comes in the mail (3 days)

---

### Post by Titus A Duxass on 2007-02-11
> I have no TV Tuner as of right now - That is probably the root of the problem.

I have a myth box where I do not need the TV Tuner, so I removed it post myth installation.  I get exactly the same problems. If I replace the TV Tuner the problem goes away.

Unless we can find a way of fooling myth I think we are stuck with this.

---

### Post by billdotson on 2007-02-11
hmm ok I guess when I get mine in the mail and if that doesn't fix it I will post again about the issue

---

### Post by Kerry Lange on 2007-03-02
I'm not so sure the issue is the lack of a TV tuner.  I've got a Hauppauge PVR 500 and I can watch TV using VLC Media Player.

However, when trying to get MythTV working I'm getting the same "cannot connect to backend server" message.  It's asking me to check the IP address as well.

---

### Post by Panhead Bill on 2007-03-03
I just updated edgy per the update manager, and now my mythtv setup gives the same error.  it was working just prior to the update.

---

### Post by hotani on 2007-03-25
Mine just started doing this. I do not want/need a tv tuner. All I want to do is watch videos. MythTV is unusable because as soon as it is opened, I get an error message about not being able to connect to the backend server. As soon as I clear this, it comes back again. 

MythTV is dead on my box now, and I did not even change anything. I have been using it for over a year and now I can't. MySQL is running, the user 'mythtv' is there and working fine--I don't even know if that is necessary. 

Is there a fix for this? Also, I can't find mythtv-setup anywhere on my system. I don't even know where to start to try and fix this. Doing it from mythfrontend is impossible because of the error itself. Brilliant.

---

### Post by Kent84 on 2007-08-31
I had same problem but fixed it. Even if backend server is running on same PC as frontend, i.e. IP is set to 127.0.0.1, firewall needs to be pinholed or turned off. It worked for me.

---

