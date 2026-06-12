---
title: "What makes mythfrontend start after boot?"
date: 2011-11-23
forum: Mythbuntu
---

### Post by RideMan on 2011-11-23
Sorry, folks, I'm new at this Linux stuff...

My MythTV system is working remarkably well now.  But there is this one nagging issue...

During the startup process, MySQL starts, Mythbackend starts...and eventually, mythfrontend starts.  Mythfrontend is not a daemon, so I presume there is a startup script someplace that launches mythfrontend.

Unfortunately, the boot process doesn't take long enough, so on system startup, mythfrontend starts, and immediately complains that it can't talk to the backend.  By the time that message appears on the screen, it is able to connect.  So what I want to do is add a brief delay to the mythfrontend startup to give mythbackend a chance to come up.  But I have no idea where to find that script...

Somebody knows this one...

--Dave Althoff, Jr.

---

### Post by nickrout on 2011-11-24
NB this answer is particular to mythbuntu, other systems are different.

/usr/bin/mythfrontend is a wrapper script that sets up some environment, then starts /usr/bin/mythfrontend.real, which is the binary.

(If you are logging in automatically and starting myth, the mechanism is that ~/.config/autostart has an entry mythfrontend.desktop which starts /usr/bin/mythfrontend)

So the script to edit is /usr/bin/mythfrontend. Add a line that says ```
sleep 3
``` somewhere near the top and adjust the "3" until it is long or short enough. (it is the number of seconds).

You could also put code in there to test if the backend is running, and that would be more foolproof, but more complex to write, particularly for a newbie.

---

### Post by Roebi on 2011-11-24
I had the same issue when I set up my MythTV system, and indeed, the 'sleep' trick solved the issue.
I am just curious about the other suggestion – testing if the backend is running. If the test confirms it is, the script can continue. But what if the backend is not running? The first option would to put the script to sleep for a few seconds, and test again for a limited number of times. But eventually, what should the script default to? How do you get out of the script?
You would want the system to stay up, in order to check what the problem is.
What are the options?

Roebi

---

### Post by RideMan on 2011-11-24
Well, that was what I wanted to know.

The problem with the sleep trick is that it will *always* delay the startup of mythfrontend.real, and we really only want to delay startup during system boot, when mythfrontend wins the startup race against mythbackend.

I did a little experimenting, by adding the following code:
```

if [! ps aux | grep '[/]usr/bin/mythbackend']; then
    echo "Waiting 10 seconds to give mythbackend a chance to start..."
    sleep 10
fi

```

What happened was that during startup, the running test passed, and the sleep didn't happen.  Apparently the problem isn't that mythbackend hasn't started yet; the problem is that mythbackend has started (and therefore shows up in ps aux) but hasn't been running long enough to be able to accept the socket connection.  I removed the "if" and that solved the problem (obviously).

It would be nice to refine this a little more, but it seems that attempting to connect to backend would probably take as long as just waiting for it to start, so while that would solve my desire to not just arbitrarily wait every time it starts.  In other words, it's basically not worth the effort to do it any other way.  8-)

Roebi, as for handling the case where the backend is not running...in this particular case, we're trying to solve a specific startup problem in a combined frontend/backend system where frontend wins the startup race with backend.  Because we are handling a specific problem, we simply make the assumption that backend has started, but isn't ready for us yet.  So we just wait a few seconds, then proceed normally, and if backend has failed for some other reason, we fall through the normal startup and get the "can't connect to backend" status warning...only this time it isn't a mere nuisance warning, it actually means something.

Based on what I learned with my experiment, you could have the script check for the backend process and then attempt to start it if it isn't already running.  And again, that could allow for a useful follow-through, perhaps something like this:

```

if [! ps aux | grep '[/]usr/bin/mythbackend']; then
# Hey, backend isn't running!  Maybe we just forgot to restart it after running backend setup or something...
    /usr/bin/mythbackend --logfile /var/log/mythtv/mythbackend.log --user mythtv
fi
#Always delay frontend startup
    sleep 10

```

Thing is, if you start it in the script this way, you don't really want to check to make sure it started (or didn't crash immediately) because if it fails, you don't really want to try again; what you want to do is let it fall through and again, generate the error so you can diagnose and fix it.

In other words, we want to correct for an obvious, known, nuisance problem, but if something more serious happens we don't want to accidentally mask the problem...and frontend already has a nice error trap we can use, we just want it to be meaningful when it fires.

--Dave Althoff, Jr.

---

