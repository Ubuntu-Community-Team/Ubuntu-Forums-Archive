---
title: "jack error no run"
date: 2011-05-10
forum: Multimedia Software
---

### Post by stephenstop on 2011-05-10
p, li { white-space: pre-wrap; } I was wondering what this means and how i could fix it.I would appreciate the help.





Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]06:02:25.226 JACK was started with PID=2032.[/COLOR]
 [COLOR=#999999]06:02:25.255 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]06:02:25.256 Post-shutdown script...[/COLOR]
 [COLOR=#990099]06:02:25.258 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]06:02:25.688 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#FF0000]06:02:27.355 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]

---

