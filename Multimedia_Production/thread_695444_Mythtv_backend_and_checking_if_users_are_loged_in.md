---
title: "Mythtv backend and checking if users are loged in"
date: 2008-02-13
forum: Multimedia Production
---

### Post by spylvas on 2008-02-13
Hi,

I am planning to have my mythtv backend running on my set up which I am using as my desktop and found quite good instructions to do that from here: [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

Everything seems to work right away when I did settings, but today (next day) I have experienced some unexpected shutdowns while I am actually logged in and using my desktop. Like middle of browsing or something.

To check if somebody is logged in I used script from here:
[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#head-26487f9f4d21757d2cfd3cfb223e1ba34fbe8fb7](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake#head-26487f9f4d21757d2cfd3cfb223e1ba34fbe8fb7)

i don't have any idea what script is really doing so I don't know where to start investigating why it failed to see that I am actually logged in.

Way I like to set up this is that if I actually log out from desktop it will shutdown in x minutes if there is no other connections going on.

I also planning to start using this as a fileserver and upnp server and would like to be able to check if any of those are connected at the moment. 

So is there easy way to see if somebody is logged on locally or remote? Or if I am using right script to do that how to investigate further and find out why it doesn't seem to work always.

-S

---

### Post by oscarsfriend on 2008-02-13
Hi,

That script checks for remote logins (as it says).  If you login locally it won't work.  Assuming you only need to login locally you could use something like this (which is what I used to use):

```

#!/bin/bash
if last | head | grep -q "still logged in"
then
   exit 1
else
   exit 0
fi

```

Quick explanation: "last" lists the content of a file that contains details of users logged in, shutdowns, reboots, etc.  The result is passed to "head", which strips off the top few lines of the output, and passes it to grep, which searches for the matching text.  This is all combined with an if-else to return a 1 or 0, which mythbackend uses to decide whether to shutdown or not.

Unfortunately the above script has a major flaw (as presumably does the original).  It turns out that once a month the file listed by last is cleared, even if you are logged in.  This would cause my machine (a combined desktop-frontend-backend) to shutdown when I was logged in and doing something.  So I replaced the script with something like the following:

```

#!/bin/sh

if [ "`users`" ]
then
  exit 1
else
   exit 0
fi

```

The command "users" reports who is logged in (at least locally, I don't know about remote logins, as I don't do that), regardless of the contents of the file listed by last.  This has worked perfectly for me ever since (about 8 months now).   (Actually I use a more complex version of that script, so that it doesn't shutdown while grabbing the TV listings, but the above should work fine).

---

### Post by theacoustician on 2008-02-13
The answer above it seems solid, but I wanted to make you aware that there's a whole subforum dedicated to Mythbuntu here([http://ubuntuforums.org/forumdisplay.php?f=301](http://ubuntuforums.org/forumdisplay.php?f=301)).  Some of the devs even pop in from time to time.  Nothing wrong with posting it here, but I noticed that you seem new here and may not have found that yet.

---

### Post by spylvas on 2008-02-14
I realized that I am posting to wrong forum, but it was a bit too late and could cancel it anymore. Anyhow, I have started new thread here: [http://ubuntuforums.org/showthread.php?p=4328452#post4328452](http://ubuntuforums.org/showthread.php?p=4328452#post4328452)

For some reason proposed solution didn't work out for me!!!

---

