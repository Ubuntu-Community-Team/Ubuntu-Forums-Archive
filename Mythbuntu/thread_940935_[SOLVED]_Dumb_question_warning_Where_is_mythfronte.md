---
title: "[SOLVED] Dumb question warning: Where is mythfrontend.log?"
date: 2008-10-07
forum: Mythbuntu
---

### Post by SiHa on 2008-10-07
I know, I know.

I've been meddling with Myth now for about four months, have a BE/FE + remote FE system all happily working, and have done a fair bit if debugging to get there.

...but I still can't find my frontend log:oops: I'm running Mythbuntu 8.04.1 i386, and I thought the logfiles should be in /var/log/mythtv. 

But they aren't.

Someone? Please?

TIA,

Simon

Edit: This is on the remote frontend FWIW.

---

### Post by newlinux on 2008-10-07
If you run mythfrontend from the menu that's where it will be (/var/log/mythtv). If you run it commandline by default it won't create a log file. If you run it with the --service option commandline it will create that log file by default (and it reads the options in /etc/mythtv/session-settings). Or you could use the -l option to specify to put the logfile wherever you want.

---

### Post by volkswagner on 2008-10-07
/var/log/mythtv/frontend.log

---

### Post by volkswagner on 2008-10-07
/var/log/mythtv/mythfrontend.log

---

### Post by SiHa on 2008-10-07
Volkswagner, thanks (twice!), but it's not there:

```
frontend@frontend-desktop:~$ ls -al /var/log/mythtv
ls: cannot access /var/log/mythtv: No such file or directory
```

Newlinux:I'm running a regular mythbuntu install, with autologin enabled. There is no logfile in the above location (hell the location deosn't even exist, there's no /var/log/mythtv!), even if I start mythfrontend from the menu.

I added the following:```
 MYTHFRONTEND_OPTS="--logfile /var/log/mythtv/mythfrontend.log"
``` to the end of /etc/mythtv/session-settings, and now Mythtv won't start, either after an autologin, or from the menu.

If I run from the commandline, Myth starts OK, but I don't get a log - even if I specify one:```
mythfrontend -l /var/log/mythtv/mythfrontend.log
```

After a bit of playing it seems that it is a permissions problem: I've created /var/log/mythtv, and chmod 777'ed it. Now if I run from the commandline as above, I do get a logfile, but Myth still refuses to start with the above line in session-settings. Remove the line, and it starts again.

?? Confused

---

### Post by newlinux on 2008-10-07
odd, my frontend and backend logs are in:

/var/log/mythtv/

and are rotated with logrotate daily. That should have been setup for you when you installed - I didn't do anything special to get mine there.

As for the MYTHFRONTEND_OPTS issue, see:

[http://ubuntuforums.org/showthread.php?t=909532](http://ubuntuforums.org/showthread.php?t=909532)

I guess I'm not the only one who has this problem. I think it's a bug. No one responded, so i thought it might be something weird I did.

---

### Post by newlinux on 2008-10-07
BTW, you shouldn't need to add a --logfile option to MYTHFRONTEND_OPTS when using --service with mythfrontend. When you use the --service option it *should* automatically use the --logfile /var/log/mythtv/mythfrontend.log by default (that's what the code in /usr/bin/mythfrontend indicates). So now that you have the directory setup (/var/log/mythtv) if you just commented out MYTHFRONTEND_OPTS line again it would write log file with --service (which is the option the autologin will use).

---

### Post by SiHa on 2008-10-08
Hmm, thanks, something to look at tonight then.

The last thing I tried last night before giving up and going to bed was exactly as you suggested - I commented out the MYTHFRONTEND_OPTS line again. Myth now starts OK, but I still have no logfile.

Also, I didn't think to look in /usr/bin/mythfrontend. Is that where I should look to check that Myth is running with the --service option, after autologin? 

Thanks for your help so far, I think I'm nearly there...

---

### Post by newlinux on 2008-10-08
/usr/bin/mythfrontend is a wrapper script that launches mythfrontend.real with the appropriate options based on the options you pass it. Looking at it won't tell you if autologin is calling mythfrontend with the --service option or not.

Maybe the autologin process isn't running with the --service (or -l) option. Are you running Gnome, KDE or XFCE? You should look to see whatever is calling mythfrontend is calling it with the --service option when you login. I think these places are different depending on which desktop you are using. 

When you run mythfrontend from the commandline with the --service option does it now use a logfile in /var/log/mythtv/mythfrontend.log? Just making sure that's working. If it is, it is almost definitely that the autologin mythfrontend isn't being spawned with the --service option. After you login what does:

```

ps aux | grep mythfrontend

```
return? It should return a process that looks something like:

/usr/bin/mythfrontend.real --logfile /var/log/mythtv/mythfrontend.log --verbose osd,idle,playback

(the --verbose osd,idle,playback is what I have MYTHFRONTEND_OPTS set to, so for you this should be different even if it is using --service option--or nothing if you commented out that part).

---

### Post by SiHa on 2008-10-08
Well, what do you know. I just checked /var/log/mythtv and there's a logfile! I guess I didn't check properly last night  after all.

Which is a good thing, because I wouldn't have a clue where to start looking to check if the Mythv is being called with the --service option at autologin.(I'm using the XFCE desktop, I think - vanilla Mythbuntu install).

So, it looks like it was simply that the install did not create /var/log/mythtv, so there was nowhere for the logfile to go! I've just installed another frontend on a spare partition on this (Windows) machine - I'll have a look there - perhaps there's a bug to file (my first!).

Finally - your other post pointed me in the right direction:
```
MYTHFRONTEND_OPTS="--logfile /var/log/mythtv/mythfrontend.log"
```
should have been```
MYTHFRONTEND_OPTS= --logfile "/var/log/mythtv/mythfrontend.log"
```

So I think you're right another (minor) bug / typo in session-settings.

Thanks,

Simon

---

### Post by SiHa on 2008-10-09
Bug #280792 submitted

---

