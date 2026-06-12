---
title: "Recordings folder issue, backend won't start-Please help"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by dannyboy79 on 2007-05-27
I was hoping some1 could help. I have used mythtv-setup and done everything correctly, I thought. I want to use a different folder than /var/lib/mythtv and the backend isn't starting because it says this error:

2007-05-27 18:50:04.315 Using runtime prefix = /usr
2007-05-27 18:50:04.698 New DB connection, total: 1
2007-05-27 18:50:04.806 Connected to database 'mythconverg' at host: localhost
2007-05-27 18:50:04.836 Current Schema Version: 1160
Starting up as the master server.
2007-05-27 18:50:04.955 New DB connection, total: 2
2007-05-27 18:50:04.974 Connected to database 'mythconverg' at host: localhost
2007-05-27 18:50:05.014 EITHelper: localtime offset -5:00:00
2007-05-27 18:50:05.050 New DB connection, total: 3
2007-05-27 18:50:05.062 Connected to database 'mythconverg' at host: localhost
2007-05-27 18:50:05.303 New DB scheduler connection
2007-05-27 18:50:05.314 Connected to database 'mythconverg' at host: localhost
2007-05-27 18:50:05.330 Main::Starting HttXServer
2007-05-27 18:50:05.367 Main::Registering HttXStatus Extension
2007-05-27 18:50:05.439 mythbackend version: 0.20.20060828-3 URL:[www.mythtv.org](www.mythtv.org)
2007-05-27 18:50:05.449 Enabled verbose msgs: important general
/media/400gb/mythtv/recordings/nfslockfile.lock: Permission denied
Unable to open lockfile!
Be sure that '/media/400gb/mythtv/recordings' exists and that both
the directory and that file are writeable by this user.

I have made sure that the folder mythtv folder I am trying to use has the same permissions and owner as /var/lib/mythtv as well as the folder within that called recordings. Here are the ls -la results for the 2 folders.

drwxr-xr-x 3 root root 4096 2007-05-26 23:59 mythtv

drwxrwsr-x 2 mythtv mythtv 4096 2007-05-27 00:10 recordings

Yes I have tried restarting the bacnend as well as the machine but to no avail. Can some1 help me please?

---

### Post by dannyboy79 on 2007-05-28
polite bump. Can anyone please help?

I have realized that the original mythtv folder for recordings was /var/lib/mythtv and NOT the recordings folder within that so I changed the folder within the setup and reran the setup which then redid the mythfilldatabase thingy and it still doesn't work. I also did the troublshotting about permissions here; [https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting](https://help.ubuntu.com/community/MythTV/Install/Feisty/Troubleshooting)
and at the bottom it talks about the bacnend not starting and folder permissions and I did all that. Here is the commands I used:
sudo chown mythtv.mythtv /media/400gb/mythtv
sudo chmod u=rwx,g=rwxs,o=rx /media/400gb/mythtv
Also, when I try to restart the backend, I get this:
Restarting MythTV server: mythbackend No /usr/bin/mythbackend found running; none killed.
.
.

and I am guessing because it's not being started. I looked in /usr/bin/ and the file is there.
and still can't start the backend. 

Here are the permissions and owner of the /media/400gb/mythtv folder again:
drwxrwsr-x  3 mythtv mythtv 4096 2007-05-27 22:17 mythtv

I can't believe that I am the first person to use a folder other than the default. Hopefully someone can answer this sooner or later please.

UPDATE: The permissions on the /media/400gb folder were previously rwx for the owner and that was it so I chnaged it to be the same as /var/lib and now it works!!! YEAH. I wasn't aware that a folder up from the folder it needed to be written to had to be writable as well but I guess that does make sence. TO SHAY!!! I guess if you just keep trying you'll get it yourself eventaully.

---

