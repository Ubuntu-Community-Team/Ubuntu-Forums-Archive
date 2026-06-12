---
title: "Mythbackend doesn't start when logging in to xbmc session from boot"
date: 2011-12-28
forum: Mythbuntu
---

### Post by poly_boi on 2011-12-28
Hi all,

I'm running Ubuntu 10.04 with kernel 2.6.38 (so that the driver works for my tuner card). I have set up Ubuntu so it logs straight in to an XBMC session automatically from boot. The problem I'm having is that I have a script set up to launch the MythTV Frontend from xbmc but when launch the MythTV frontend it says the backend isn't running. If I log in to a GNOME session there aren't any problems at all, it's only when I boot straight in to an XBMC session that I have issues. How can I get the backend to run from boot without needing to log in to GNOME or even get it to run when XBMC is launched?

Any help would be much appreciated.

---

### Post by thatguruguy on 2011-12-28
Why not reverse what you're doing, and launch the Myth frontend at boot time, and then call XBMC from the Myth frontend menu?

---

### Post by klc5555 on 2011-12-29
> **poly_boi said:**
> Hi all,

I'm running Ubuntu 10.04 with kernel 2.6.38 (so that the driver works for my tuner card). I have set up Ubuntu so it logs straight in to an XBMC session automatically from boot. The problem I'm having is that I have a script set up to launch the MythTV Frontend from xbmc but when launch the MythTV frontend it says the backend isn't running. If I log in to a GNOME session there aren't any problems at all, it's only when I boot straight in to an XBMC session that I have issues. How can I get the backend to run from boot without needing to log in to GNOME or even get it to run when XBMC is launched?

Any help would be much appreciated.

Mythbackend starts from a startup (init) script and runs as root, so it isn't directly affected by whether you log into gnome or not. Unless when you say  "If I log in to a GNOME session there aren't any problems at all",  you mean that you have start mythbackend manually at that point with something like "sudo mythbackend" from a prompt. That would be a configuration issue. You don't mean you have to start mythbackend manually, do you?

As a first guess, Ubuntu specializes in a fast boot, which frequently causes timing issues for the various components of Mythtv. The frontend may be firing up before the backend has finished initializing. If you can add a "sleep" command for 10 to 30 seconds (this of course can be fine-tuned) in the script that invokes mythfrontend, this usually gives the backend enough time to finish initializing.

---

### Post by poly_boi on 2011-12-29
> **thatguruguy said:**
> Why not reverse what you're doing, and launch the Myth frontend at boot time, and then call XBMC from the Myth frontend menu?

I don't know how to launch a mythtv session and I don't know how to launch xbmc from mythtv frontend but I'm also really happy with the way I have things set up. I prefer using xbmc as my main interface. If I could get mythtv to work properly when logging directly in to an xbmc session I would have the perfect setup.

> **klc5555 said:**
> Mythbackend starts from a startup (init) script and runs as root, so it isn't directly affected by whether you log into gnome or not. Unless when you say  "If I log in to a GNOME session there aren't any problems at all",  you mean that you have start mythbackend manually at that point with something like "sudo mythbackend" from a prompt. That would be a configuration issue. You don't mean you have to start mythbackend manually, do you?

As a first guess, Ubuntu specializes in a fast boot, which frequently causes timing issues for the various components of Mythtv. The frontend may be firing up before the backend has finished initializing. If you can add a "sleep" command for 10 to 30 seconds (this of course can be fine-tuned) in the script that invokes mythfrontend, this usually gives the backend enough time to finish initializing.

The front end doesn't fire up straight away it launches when I run the script from XBMC however I think every time I have tried to launch it, it has been immediately after startup so I'll try waiting 30 seconds or so and see how I go. Thanks for your help.

---

### Post by nickrout on 2011-12-29
Do you have xbmc accessing (and possibly locking) any of the tuners? If so, the backend startup may fail on that account.

---

### Post by klc5555 on 2011-12-31
Also, if you're running xbmc 10.1 (and mythtv 0.23.x or 0.24) you could try using the xbmc addon "mythbox", which seems to be essentially xbmc's drop in replacement for mythfrontend. 

There are some caveats. Mythbox's livetv supposedly doesn't work yet with mythtv 0.24, for example. But if the xbmc addon works for you, then it will likely be better integrated with your preferred xbmc shell than what you're trying to do in invoking a regular mythfrontend session from within xbmc with a script.

---

