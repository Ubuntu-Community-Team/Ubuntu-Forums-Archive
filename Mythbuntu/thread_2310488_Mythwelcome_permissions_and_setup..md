---
title: "Mythwelcome permissions and setup."
date: 2016-01-19
forum: Mythbuntu
---

### Post by Paul_Hey on 2016-01-19
I'm trying to setup a backend only system, with multiple Kodi frontends.  I am using the current mythbuntu 14.04 iso, with .27 updates.

I have tried to setup mythwelcome in order to shut the backend down when idle - ie no frontends connected and not recording.

My first question is this...  if mythwelcome calls the mythshutdown command, then I should in theory be able to call the mythshutdown command from the terminal using the followin

```
mythshutdown -x
```

But all I get is:

```

myth@myth-OptiPlex-745:~$ mythshutdown -x
OK to shutdown
Error: no daily wakeup times are set
Error: no recording time is set
Error: no wake up time set and no scheduled program
everything looks fine, shutting down ...
..
.
shutting down ...

```

Then the system continues happily as if nothing has happened, but if I enter:

```
sudo mythshutdown -x
```

The backend shuts down.

I'm guessing this is a permission problem.  I have added the line:

```
%mythtv localhost = NOPASSWD: /usr/bin/mythshutdown
```

to /etc/sudoers.tmp, however this does not seem to have worked.  Is %mythtv the correct user?

Along with this, I am unable to even get the countdown timer to start, but thought I should concentrate on one thing at a time!

---

### Post by Paul_Hey on 2016-01-21
I was totally overthinking this.  I just needed the correct shutdown command in the backend setup, no need for mythwelcome on a backend only machine.

---

