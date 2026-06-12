---
title: "Mythbuntu not starting - loads to user desktop only"
date: 2008-04-24
forum: Mythbuntu
---

### Post by Trimble Epic on 2008-04-24
Well, I really screwed something up this time...  It's probably something really simple like a checkbox or something...

So, I was tweaking my mapped drives for MythVideo today.  I got it working all nice like I wanted.  Then, after restarting the box once or twice, the update manager inticed me to click it.  I let it update.  It's probably been 3-5 months since I last let it update.

So, I just ran the basic updates - I didn't click the "new dist" button (yet).  After the updates ran, I restarted the box (just to make sure the mappings in /etc/fstab worked as expected.  To my surprise, Myth did not come up... instead, it just loaded to desktop.

I probably should have stopped there, but I figured maybe I needed to do the 8.04 update, since the button was sitting there calling to me.  So, I let it update.  I probably should have just left well enough alone, but I did the update.  sigh.

Ok, so now, it reboots into a different desktop.  Now I have 4 icons that I didn't have before (yeah, not surprised).  Also, VNC no longer works, so I guess I'm going to have to either fix everything via shell, or go dig up the mouse and keyboard for the box.  sigh.

Ok, so, where should I start looking to resolve the problem of Myth not loading?

---

### Post by laga on 2008-04-25
Look in /var/log/mythtv/mythfrontend.log. Regarding VNC, you just need to reconfigure it in the control centre.

If you've got another linux box, you can just run "ssh -X -Y IP-of-your-mythtv-computer", then start mythbuntu-control-centre and it'll pop up on your screen.

---

### Post by Trimble Epic on 2008-04-25
Ok.. when I check that log file, all I see is the following:

Starting mythfrontend.real..

and multiple lines of it.  That doesn't help much?

I fixed VNC by reconfiguring it after hooking up a real keyboard and mouse long enough to fix it.  Now, also in MCC, I look at Artwork & Login Behavior.  The Automatic Login checkmark is set, but if I clear it and apply, it says there are no changes to apply.  If I set it again, and apply, there are still no changes to apply.  Where is the underlying config setting for that? (or is there one?)

---

### Post by Trimble Epic on 2008-04-25
Ok, from the desktop, when I click Applications > Multimedia > MythTV Frontend then absolutely nothing happens.

---

### Post by laga on 2008-04-25
Can you start "mythfrontend" in a terminal and shows up the output?

---

### Post by Trimble Epic on 2008-04-25
Nope.

Here's what I see in terminal window:

/usr/bin/mythfrontend/real: symbol lookup error: /usr/lib/libmythavcodec-0.21.so.0: undefined symbol: faacDecOpen

and the log continues to show only: "Starting mythfrontend.real.." over and over.

help!

---

### Post by laga on 2008-04-26
Interesting, something is wrong with the libraries. Can you show me the output the following command: ```
 apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
```

Thanks!

---

### Post by diehard999 on 2008-04-26
Hello, I have got the same problem, here is the output of my system:

```

apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
libmyth-0.21-0:
  Installiert:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Mögliche Pakete:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Versions-Tabelle:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/multiverse Packages
mythtv-frontend:
  Installiert:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Mögliche Pakete:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Versions-Tabelle:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/multiverse Packages
mythtv-common:
  Installiert:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Mögliche Pakete:0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Versions-Tabelle:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://archive.ubuntu.com hardy/multiverse Packages

```

Edit:

I just noticed that mythbackend is not running, and if I try to start it I get the same messages as when starting mythfrontend:

```

sudo mythbackend start
mythbackend: symbol lookup error: /usr/lib/libmythavcodec-0.21.so.0: undefined symbol: faacDecOpen

```

---

### Post by beazizo on 2008-04-26
Same problem here after upgrade to 8.04 although my apt-cache output looks slightly different from previous post:

```
apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
libmyth-0.21-0:
  Installed: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
mythtv-frontend:
  Installed: 0.21.0+fixes16838-0ubuntu3
  Candidate: 0.21.0+fixes16838-0ubuntu3
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status
mythtv-common:
  Installed: 0.21.0+fixes16838-0ubuntu3
  Candidate: 0.21.0+fixes16838-0ubuntu3
  Version table:
 *** 0.21.0+fixes16838-0ubuntu3 0
        500 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/multiverse Packages
        100 /var/lib/dpkg/status
```

---

### Post by Trimble Epic on 2008-04-26
> **laga said:**
> Interesting, something is wrong with the libraries. Can you show me the output the following command: ```
 apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
```

Thanks!

ok!

```
trimble@Mythbuntu:~$ apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
libmyth-0.21-0:
  Installed: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://mirror.cs.umn.edu hardy/multiverse Packages
mythtv-frontend:
  Installed: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://mirror.cs.umn.edu hardy/multiverse Packages
mythtv-common:
  Installed: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://mirror.cs.umn.edu hardy/multiverse Packages
trimble@Mythbuntu:~$ trimble@Mythbuntu:~$ apt-cache policy libmyth-0.21-0 mythtv-frontend mythtv-common
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://mirror.cs.umn.edu hardy/multiverse Packages
mythtv-common:
  Installed: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Candidate: 0.21.0+fixes17120-0ubuntu0+mythbuntu2
  Version table:
 *** 0.21.0+fixes17120-0ubuntu0+mythbuntu2 0
        100 /var/lib/dpkg/status
     0.21.0+fixes16838-0ubuntu3 0
        500 http://mirror.cs.umn.edu hardy/multiverse Packages
trimble@Mythbuntu:~$
```

---

### Post by Notlef on 2008-04-26
> **Trimble Epic said:**
> Nope.

Here's what I see in terminal window:

/usr/bin/mythfrontend/real: symbol lookup error: /usr/lib/libmythavcodec-0.21.so.0: undefined symbol: faacDecOpen

and the log continues to show only: "Starting mythfrontend.real.." over and over.

help!

I was having the exact same problem, but after some help from laga in #ubuntu-mythtv over at irc.freenode.net it now runs perfectly again. What I was told to try was to downgrade my mythtv by running the following command:
sudo aptitude install mythtv-common=0.21.0+fixes16838-0ubuntu3 mythtv-frontend=0.21.0+fixes16838-0ubuntu3 libmyth-0.21-0=0.21.0+fixes16838-0ubuntu3

after downgrading the backend started itself and I can run the frontend again.

the problem was probably caused by me running weekly builds prior to the update, traces of that could be found in the form of this line in sources.list: # deb [http://ppa.launchpad.net/mythbuntu/ubuntu](http://ppa.launchpad.net/mythbuntu/ubuntu) gutsy main restricted universe multiverse

---

### Post by laga on 2008-04-26
Right, thanks Notlef for helping me figure this one out.

If you're using the weekly builds on Gutsy and upgrade to Hardy using update-manager, the PPA for the weekly builds will be disabled in your sources.list. That means that MythTV won't be upgraded because the version number in the weekly fixes for Gutsy is higher than the version number for the normal builds in the Hardy archives. :(

I'll push new weekly fixes builds in a few minutes to make sure the version number for Hardy is higher. Once you re-enable the weekly fixes repo for Hardy, an upgrade should be available.

Another option is downgrading the MythTV packages, see Notlef's posting.

---

### Post by Trimble Epic on 2008-04-28
Ok, well, I entered the magic-super-voodoo-command-from-hell from above, and now I can start front end.  However, front-end can't find back end.  So, I fired up MCC and found that the "role" for backend had been removed.  So, I re-added the backend server role, and restarted.  Still nothing.  I tried going into Mythtv backend setup, and it wanted to upgrade the database.  It failed with that saying that some sql field was not expected.

In the end, I gave up and downloaded a new ISO of 8.04, and I'm reinstalling from scratch.  I tend to obsess over clean installs on my appliance machines anyway. :P

---

