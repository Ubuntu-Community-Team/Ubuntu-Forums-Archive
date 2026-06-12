---
title: "Mythbackend start stop not working?"
date: 2012-03-19
forum: Mythbuntu
---

### Post by uncle hammy on 2012-03-19
I am running 11.10 with 0.25 installed via Mythbuntu repos.  It doesn't appear that the mythtv-backend start stop script is working.

The upstart is clearly being called at boot up (mythbackend starts).  However, if I try to stop it it doesn't.  SO I get something like this....

reboot
pgrep mythbackend -> 2611
sudo service mythtv-backend stop -> "mythbackend stopping waiting"
sudo mythtv-backend start -> "instance started 2932"
pgrep mythbackend -> 2611 (not 2932)

I can also sudo kill 2611 til the cows come home and it won't die.

The other thing I am seeing is that if I go to Settings -> Mythbackend Setup, enter my password to stop mythbackend, I still always get the "Mythbackend is running" warning.  I click "stop and continue" and then do my thing and close out.  pgrep mythbackend gives a new pid from the original.

This is a completely fresh install of 11.10 as of Saturday morning.

Anyone have any ideas on how to fix the service start stop issue?

Thanks

---

### Post by BicyclerBoy on 2012-03-20
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)

Are you sure the backend is being started by upstart job?

If the myth install path does not match the upstart job configuration then you might get some of your symptoms. The old init runlevel scripts could still be in place.

Check /etc/init/mythtv-backend.conf contents match the install paths.
which mythbackend

Hard to believe mythbuntu packages would have that wrong tho..

---

### Post by uncle hammy on 2012-03-20
I am reasonably certain it is.  If I comment out all of  /etc/init/mythtv-backend.conf, mythbackend does not start at boot up....or with the service call.

---

### Post by BicyclerBoy on 2012-03-20
I have to admit...al-tho I am using upstart to start mythbackend mythtv-0.25 on lucid, I never tried to service stop the backend.
This was forgotten in the relief of getting the backend working again.

Maybe the upstart job definition has no provision for stopping except on shutdown..

Edit: Have tested the service stop & start of mythbackend using upstart job configuration as linked to on the mythtv.org website.
Both stop & start work as intended.

---

