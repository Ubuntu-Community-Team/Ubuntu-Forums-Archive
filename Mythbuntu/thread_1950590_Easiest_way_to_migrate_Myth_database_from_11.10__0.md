---
title: "Easiest way to migrate Myth database from 11.10 / 0.24.1 to 12.04  / 0.25"
date: 2012-04-01
forum: Mythbuntu
---

### Post by yonkiman on 2012-04-01
I've got a solid, working 10.10 / 0.24.1 system, but I'm ready to try 12.04  / 0.25 when it comes out.  In fact I downloaded a beta release a few weeks ago and tried it out on a spare hard drive...

...and was surprised that the Backup/Restore function in Mythbuntu Control Center appears to have been removed!  That's going to make migrating the database harder.

So I was wondering if anyone had any opinion on what will be the easiest (and hopefully most reliable) way to migrate my shows and settings.

Thanks (and congrats to the 0.25 team!),
Fred

---

### Post by nickrout on 2012-04-01
> **yonkiman said:**
> I've got a solid, working 10.10 / 0.24.1 system, but I'm ready to try 12.04  / 0.25 when it comes out.  In fact I downloaded a beta release a few weeks ago and tried it out on a spare hard drive...

...and was surprised that the Backup/Restore function in Mythbuntu Control Center appears to have been removed!  That's going to make migrating the database harder.

So I was wondering if anyone had any opinion on what will be the easiest (and hopefully most reliable) way to migrate my shows and settings.

Thanks (and congrats to the 0.25 team!),
Fred

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

not been removed from anywhere.

---

### Post by tgm4883 on 2012-04-02
> **yonkiman said:**
> I've got a solid, working 10.10 / 0.24.1 system, but I'm ready to try 12.04  / 0.25 when it comes out.  In fact I downloaded a beta release a few weeks ago and tried it out on a spare hard drive...

...and was surprised that the Backup/Restore function in Mythbuntu Control Center appears to have been removed!  That's going to make migrating the database harder.

So I was wondering if anyone had any opinion on what will be the easiest (and hopefully most reliable) way to migrate my shows and settings.

Thanks (and congrats to the 0.25 team!),
Fred

It hasn't been removed. Can you launch MCC (mythbuntu-control-centre) from the command line and see if there are any error messages? I have a feeling I know the issue and it's just waiting on a new upload to the archive to resolve it.

---

### Post by yonkiman on 2012-04-04
> **tgm4883 said:**
> It hasn't been removed. Can you launch MCC (mythbuntu-control-centre) from the command line and see if there are any error messages? I have a feeling I know the issue and it's just waiting on a new upload to the archive to resolve it.

Interesting.  I'd tried an alpha mythbuntu 12.04, and went all over the MCC several times and couldn't find backup/restore.  I'm downloading beta 2 now and will try it.

---

### Post by nickrout on 2012-04-04
> **yonkiman said:**
> Interesting.  I'd tried an alpha mythbuntu 12.04, and went all over the MCC several times and couldn't find backup/restore.  I'm downloading beta 2 now and will try it.

why not just upgrade?

---

### Post by yonkiman on 2012-04-04
> **nickrout said:**
> why not just upgrade?
Thanks for the suggestion, but of the 4 or 5 times I've tried to upgrade an Ubuntu distribution, it's worked correctly once.  Except for that one time (and it was not recent - I upgraded my 10.10 "play" system that I experiment with to 11.04 and it wouldn't even boot into a working GUI any more) something pretty major stopped working.

Therefore I have serious doubts I can upgrade from 10.10 to 12.04 (or even 11.04).  I'd much rather do a clean install - I don't use this system for much besides MythTV and a general server for my house.

---

### Post by yonkiman on 2012-04-04
> **tgm4883 said:**
> It hasn't been removed. Can you launch MCC (mythbuntu-control-centre) from the command line and see if there are any error messages? I have a feeling I know the issue and it's just waiting on a new upload to the archive to resolve it.

Yes, I got an error message.  Something about permissions.  So I "sudo" launched it and the Backup and Restore menu was there at the top!

However after I pointed it to the backup file and pressed "Accept" to start the restore, I got the the following error:

```
org.freedesktop.DBus.Python.RuntimeError

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 252, in scriptedchanges
    for item in plugin_dictionary:
RuntimeError: dictionary changed size during iteration
```

Thanks for your help!

---

### Post by tgm4883 on 2012-04-05
> **yonkiman said:**
> Yes, I got an error message.  Something about permissions.  So I "sudo" launched it and the Backup and Restore menu was there at the top!

However after I pointed it to the backup file and pressed "Accept" to start the restore, I got the the following error:

```
org.freedesktop.DBus.Python.RuntimeError

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/MythbuntuControlCentre/backend.py", line 252, in scriptedchanges
    for item in plugin_dictionary:
RuntimeError: dictionary changed size during iteration
```

Thanks for your help!

Yep, thats exactly what I thought. It will be updated in the next upload of mythbuntu-bare

---

### Post by yonkiman on 2012-04-05
> **tgm4883 said:**
> Yep, thats exactly what I thought. It will be updated in the next upload of mythbuntu-bare
Great!  Do you have any estimate when that will be?  I don't want to keep swapping out hard drives to check if it's a month away...

Thanks - I'm looking forward to the upgrade!
-Fred

---

### Post by tgm4883 on 2012-04-05
> **yonkiman said:**
> Great!  Do you have any estimate when that will be?  I don't want to keep swapping out hard drives to check if it's a month away...

Thanks - I'm looking forward to the upgrade!
-Fred

I'm finishing up testing on it and it should be in 12.04 in the next few days. Final Freeze is on the 12th, so it will be before that. I'll look into getting it into our updates PPA for previous versions as well.

---

### Post by JKMB111 on 2012-05-07
Was there resolution on this for 11.10?  I have the same permission issues and would like to backup before moving to 12.04.

---

### Post by nickrout on 2012-05-08
back up using the documented backup tool as described in the wiki.

I don't know how many times I have posted this link, but here it is again.

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by sandbelt on 2012-05-23
> **nickrout said:**
> back up using the documented backup tool as described in the wiki.

I don't know how many times I have posted this link, but here it is again.

[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

I don't know whether you know that the database tables get redesigned from time to time: the designers add more columns every so often. 

I am personally concerned about migrating 10.04 to 12.04 because of this.

---

### Post by nickrout on 2012-05-24
> **sandbelt said:**
> I don't know whether you know that the database tables get redesigned from time to time: the designers add more columns every so often. 

I am personally concerned about migrating 10.04 to 12.04 because of this.

Of course I am aware of that.

If you update mythtv it will automatically update the database when you start the backend, and the frontend tables when you start a frontend.

Sometimes of course it doesn't work right (usually if you get impatient and interrupt the process.) Then you would use the backup that yo made immediately before the upgrade and try again.

Alternatively you can back up the database, reinstall to a new version and then import the backed up database. Again the program will update it. 

I am assuming if you are running 10.04 you are already on 0.24 or 0.25. You can update to 0.25 and stay on 10.04.

---

### Post by Zorbitz on 2012-05-24
I take no responsibility for what happens to others, but in my case it worked fine doing what is said above. I backed up a 10.10 / 0.24 system and installed 12.04 from scratch. Restored the DB, stopped mythbackend and entered mythtv-setup, I was told it needed to convert the db to new format. After that all was good.

---

### Post by nickrout on 2012-05-24
> **Zorbitz said:**
> I take no responsibility for what happens to others, but in my case it worked fine doing what is said above. I backed up a 10.10 / 0.24 system and installed 12.04 from scratch. Restored the DB, stopped mythbackend and entered mythtv-setup, I was told it needed to convert the db to new format. After that all was good.

Of course it was, that is the way it is designed.

To reiterate though, the update can take some time. There is not a lot of feedback in the gui telling you what is going on. Do NOT stop the process part way through or you will end up with a corrupt and unrepairable database. (Of course you will still have the backup and can start again.) Check the logs if it looks "stuck", it is probably still working away.

---

