---
title: "mythtv backend not loading at startup"
date: 2010-07-15
forum: Mythbuntu
---

### Post by cedyathome on 2010-07-15
..or using the "sudo start mythtv-backend" command.
this is the mythtv backend log entry

> 2010-07-15 14:04:32.137 mythbackend version:  branches/release-0-23-fixes [25333] [www.mythtv.org]("http://www.mythtv.org/")
2010-07-15 14:04:32.137  Using runtime prefix = /usr
2010-07-15 14:04:32.190 Using  configuration directory = /.mythtv
2010-07-15 14:04:32.235 Cannot  locate your home directory. Please set the environment variable HOME
2010-07-15  14:04:32.279 Failed to init MythContext, exiting.This started after I upgraded to Mythbuntu 10.04 today. (After running a very stable build for almost 6 months!)

I tried
> export HOME=/home/mythuser/   (substituting mythuser with my user name)and it still doesn't work!

I can use "mythbackend" at the command prompt and it starts right up! But, even if I use "mythbackend &" it wont' run in the background.

Am I doing something wrong? What broke? I'm hopeless with permissions if that's what's wrong here.

I also have an issue with an "Exception in Capture State of plugin Mirobridge.conf" when I try to run the log grabber. I haven't tried to chase that down yet.

Thank you.

---

### Post by nickrout on 2010-07-16
This problem I think is cured by going to a more recent version of mythtv. The 10.04 version is beta and you should enable the autobuilds [http://www.mythbuntu.org/auto-builds](http://www.mythbuntu.org/auto-builds)

Make sure you choose 0.23, if you choose 0.24 you will get trunk, which is cool if you want to test unstable code :)

0.23 will get you 0.23-fixes. I am pretty sure this will fix(es) your problem.

---

### Post by cedyathome on 2010-07-17
Thank you. I already have autobuilds on for .23 & is current as far as I can tell. See backend log above.

---

### Post by nickrout on 2010-07-18
> **cedyathome said:**
> Thank you. I already have autobuilds on for .23 & is current as far as I can tell. See backend log above.

OK well for a start the backend should run as suer mythtv.

check /etc/init/mythtv-backend.conf. Mine looks like this:

> # MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script


do you have the USER=mythtv line?

---

### Post by kilmarnock on 2010-08-05
same crap here. after the last update, it began again. 

init.d/mythbackend:

HOME=/home/mythtv
export HOME
`export HOME=/home/mythtv`

...

start)
cd /home/mythtv
mythbackend --user mythtv -p /var/run/mythbackend.pid -l /var/log/mythtv/mythbackend.log -d &

...

2010-08-05 21:42:20.342 Using runtime prefix = /usr
2010-08-05 21:42:20.375 Using configuration directory = /.mythtv
2010-08-05 21:42:20.438 Cannot locate your home directory. Please set the environment variable HOME
2010-08-05 21:42:20.484 Failed to init MythContext, exiting.

AND IT IS _NOT_ USING /.mythtv. /.mythtv is an exact copy. it is not using it.

Sorry for getting loud, but I am really pissed. The bug is only after a reboot. Thousand times reboot. 
The following thread is an old discussion of the same problem:

[http://irclogs.ubuntu.com/2010/05/22/%23ubuntu-mythtv.html](http://irclogs.ubuntu.com/2010/05/22/%23ubuntu-mythtv.html)

Guess who is that poor guy :((

Felix

---

### Post by nickrout on 2010-08-05
have you even read my post? (the one above your most recent post)

---

### Post by kilmarnock on 2010-08-06
I have that line, thank you

---

### Post by cedyathome on 2010-08-31
I came back to this again. I too use the Avenard repos & don't know how to go about going back to auto builds.

However, I FOUND the problem. There was an extra space in the file /etc/init/mythtv-backend.conf. In the test -f line, my file had a ". /" instead of "./" for the file after &&. See below.

Now to figure out how to have it fixed for good.

Anyone know how to move from the Avenard repo back to autobuilds?
> 
  # MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && **[COLOR=Magenta]. /[/COLOR]**etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script


---

### Post by tgm4883 on 2010-08-31
> **cedyathome said:**
> I came back to this again. I too use the Avenard repos & don't know how to go about going back to auto builds.

However, I FOUND the problem. There was an extra space in the file /etc/init/mythtv-backend.conf. In the test -f line, my file had a ". /" instead of "./" for the file after &&. See below.

Now to figure out how to have it fixed for good.

Anyone know how to move from the Avenard repo back to autobuilds?

Thats not an extra space, it's supposed to be there.

Can you attach your /etc/default/mythtv-backend file

---

### Post by cedyathome on 2010-08-31
oops. But removing the space made it work. Thanks for looking into it.
This is a copy/paste of my /etc/default/mythtv-backend.

# User as which to run
USER=mythtv

# Replace all arguments to mythtv-backend
ARGS="--logfile /var/log/mythtv/mythbackend.log"

---

### Post by tgm4883 on 2010-08-31
> **cedyathome said:**
> oops. But removing the space made it work. Thanks for looking into it.
This is a copy/paste of my /etc/default/mythtv-backend.

# User as which to run
USER=mythtv

# Replace all arguments to mythtv-backend
ARGS="--logfile /var/log/mythtv/mythbackend.log"

Deleting that file should make it work as well.

---

### Post by cedyathome on 2010-08-31
Thank you.
Could you explain why?

---

### Post by tgm4883 on 2010-08-31
Because we don't use that file anymore.

What the extra space does is it tells it to source that file, so essentially what you did by deleting the space was delete the file.

---

