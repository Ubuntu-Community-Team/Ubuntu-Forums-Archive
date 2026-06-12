---
title: "Watch TV ... All tuners are currently busy"
date: 2014-05-31
forum: Mythbuntu
---

### Post by seanjohnson20 on 2014-05-31
This appears to be a common problem, but I still haven't found a solution.

Backend is configured with HDHR Prime tuners, SchedulesDirect and FIOS cable card and running without errors.  Front end connects to DB.  Select Watch TV and I get "All tuners are currently busy."  When in fact none of the 3 are being used.  MythWeb shows listings and schedules recordings.

[COLOR=#000000][FONT=verdana]NUC Intel® Core™ i3-4010U 8 GB HDHR Prime MythBuntu 14.04

Logs:   [/FONT][/COLOR]http://pastebin.com/yRCHEuAy

Any ideas?  I'm thinking it must be something in how I set up the tuners on the backend.

---

### Post by blm-ubunet on 2014-05-31
lines 777 778 suggests tuners are not configured.

I'm have trouble trying to figure out which set of log belongs to the master BE with tuners.
You have posted mythtv-setup logs are from the MBE ?
Can you log in to the MBE as mythtv or "sean" ?

Can we just concentrate on MBE only?
Can you run mythfrontend on the MBE?
Can you log into MBE as user "mythtv" & stop the BE & run mythtv-setup?

Do you have multiple (& different) copies of /home/<user>/.mythtv/config.xml ?
(there's a fallback default copy in /etc/mythtv/ or similar)

mythbackend runs as user "mythtv" (& yours is).
Your logs show mythfilldatabase running as user "sean".
I assume that is because you ran it from terminal (manually).
Logging in as "mythtv" allows you to easily check it works as BE user.

Note that mythbuntu installs wrappers script around the real "mythtv-setup" executable just to make it more difficult.

---

### Post by seanjohnson20 on 2014-05-31
Thanks for your reply.

Using MythTv Backend setup -- the 3 HDHRPrime tuners appear to be configured and connected to my SchedDir acct and channels look right.

The Logs came from the MythBuntu Control Centre tool that generates logs and sends them to pastebin.  I just enabled all.  Not knowing what to grab.  I knew I wanted at least the Backend and Frontend.

"[COLOR=#000000]Can you run mythfrontend on the MBE?"[/COLOR]   I can launch mythfront via the cmd line or the MythTV Frontend app.  Not entirely sure what you are asking here.

Also, both frontend and backend are on the same machine, no slaves. 
 
User name in the /etc/mythtv/config is mythtv. Frontend user id is mythtv and gives no errors.  I log into my NUC as sean, but the mythtv login is unchanged from the install. 

This is a fresh install of Mythbuntu so I could be sure there weren't other weird mysql db entries from past attempts.   
The mythfill db was from the prompt after closing/restarting backend. So I guess it used my logged in 'sean' user name with that command.

So are you suggesting I log into the desktop as mythtv?  I think mythtv creates a mythtv user with su privileges if I recall.  I guess I'm not clear on the logging in as mythtv part.

thanks,

sean


Here is a new log grabber of just the Backend.log   [http://pastebin.com/mxUvaE9j](http://pastebin.com/mxUvaE9j)

I see what you mean about the logs suggesting the tuners are not configured.  Strange, not sure what more I could do to fix that.  Followed same procedure on a previous machine where it worked.

---

### Post by blm-ubunet on 2014-05-31
Sorry I thought there was 2 PCs a MBE & NUC FE box..

If you login as user "sean" then if you run:
- mythfrontend
- mythfilldatabase
- etc
will run as user "sean" (not "mythtv")
This means that the "same" path leads to different config.xml file because of different home folders.
(It is possible that wrapper scripts or other cmd line options can be used to launch app as any user.)

Do you run mythtv-setup from terminal or from MCC?
Try from user "sean":
```
mythtv-setup --user mythtv
```
Do the tuners appear okay ?
Errors in the stdout/err in terminal window (<alt>+<tab>)?

If you start mythbackend via upstart it runs as user "mythtv".
AFAIK The default mythbuntu install expects FE user to be "mythtv".

Running mythfilldatabase as FE users (or worse root) can cause temporary/cache file permissions problems.
If your config.xml files (for all users) are sorted then you can run FE or mythfilldatabase as any user.

I would guess that your tuner problems are caused by mythtv-setup having been run with a different config.xml (to the BE user "mythtv") &/or localhostname.
Localhostname (if non blank) replaces hostname & is used to name the profile (inc tuners).

---

### Post by seanjohnson20 on 2014-06-01
Yes, I see
both the mythtv and sean homes have .mythtv/config.xml with the same user info.
If I run your code and startbackend and run mythfilldb, then start FE in terminal it launches the Mythtv app and WatchTV works.

Thanks for your help with this.



Now when I stop app and restart from Unity Mythtv Frontend icon it launches and works.  So was it just populating the db from mythtv user that made the difference?

---

### Post by blm-ubunet on 2014-06-01
So you re-added the tuners with "mythtv-setup --user mythtv" ?

Or just running MFD (mythfilldatabase) as "mythtv" user login?


The BE should run as "mythtv" & it does from the default upstart-job script.
mythfilldatabase is run automatically (if configured) by the BE as "mythtv".

I *did* think that mythtv-setup changed itself to run as user "mythtv" but now I'm not so sure.
If it does not then running mythtv-setup as user mythtv could have changed permissions/ownership of some structure related to the network tuners & this would have allowed BE to access tuners..

---

### Post by seanjohnson20 on 2014-06-02
No, didn't change the tuners, just ran your code which prompted dialogs:  Start backend and Mythfilldb.
Then I started mythfrontend with terminal.

But now when I go to Frontend it flashes Please Wait and returns me to the menu.

---

### Post by blm-ubunet on 2014-06-02
Turns out mythtv-setup does not accept "--user" option...
It won't run as another user on my PC..

The mythbuntu setup wrapper script probably just ignored the "--user" &/or errored out.
So all that *might* have happened is that the BE was started up..

mythtv-setup should prompt about stopping mythbackend..

Check the status of running service (should be auto started on boot)
```
sudo service mythtv-backend status
```

I have a habit of executing this cmd line before (the real*) mythtv-setup:
sudo service mythtv-backend stop

Ubuntu mythtv requires user to run this afterwards to restart BE (or reboot):
```
sudo service mythtv-backend start
```
**Does that cmd get your FE working okay ?**

Plain mythtv works that way..AFAIK mythbuntu does its own thing.

(the real*) - Mythbuntu wraps the real mythtv-setup with a script that could restart BE..
I can not find mythbuntu packaging source code to find details.

---

### Post by seanjohnson20 on 2014-06-02
yes mythtv backend service is running.
just applied some ubuntu updates and restarted and immediately ran MythTV from unity search MythTVFE -- watchtv is working again.
would like to understand what causes those failures though before I inflict this system on my wife.  :)

---

### Post by blm-ubunet on 2014-06-02
A simple explanation could be the BE started up before mysql &/or network interfaces were up.
This problem does not occur if you stop/start MBE manually (because other services are up).
(symptoms seem more like network & networked tuners)
 
To test this you need to check the service status of mythtv-backend next time you reboot & have problem.

There is special mention of this:
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

---

### Post by seanjohnson20 on 2014-06-02
Ok, I'll do some more testing along those lines.  Thanks for all your help.

---

