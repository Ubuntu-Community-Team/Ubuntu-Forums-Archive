---
title: "Scheme issue with latest 2.6 fixes"
date: 2013-01-20
forum: Mythbuntu
---

### Post by rmiddle on 2013-01-20
I upgraded to the latest fixes and now when starting my frontend and secondary backend are failing.  From the logs it keep reporting it can't get the lock to run the scheme update yet all 3 systems are using the same build.  

mythtv_0.26.0+fixes.20130118.8f8274a-0ubuntu0

Has anyone found a workaround for this bug?

Thanks
Robert

---

### Post by BicyclerBoy on 2013-01-20
Schema upgrade:
You must ensure that all FEs & BEs are stopped (& stay stopped).
Then run "mythtv-setup" on master backend.

Can stop backend on a system using upstart:
sudo service mythtv-backend stop

The mechanisms used to launch BE & FE are many & varied..

---

### Post by rmiddle on 2013-01-20
> **BicyclerBoy said:**
> Schema upgrade:
You must ensure that all FEs & BEs are stopped (& stay stopped).
Then run "mythtv-setup" on master backend.

Can stop backend on a system using upstart:
sudo service mythtv-backend stop

The mechanisms used to launch BE & FE are many & varied..

I am running a standard Mythbuntu 10.04 install.  I ran mythtv-setup and both backends are coming up fine now but the front end boots up to a blue screen and just sits there.

I enable verbose logging but I am not seeing anything in the log suggesting what is wrong.

Thanks
Robert

Sorry my mistake.  I am running 12.04 not 10.04.  I am rebuilding the front-end it might be some kind of nvidia driver issue.

---

### Post by BicyclerBoy on 2013-01-21
Is the blue screen the mythtv theme default wallpaper ?

stop/kill any mythfrontend process(es) & then launch from terminal

mythfrontend -v all

Check you don't have some crazy crash-auto-restart script..

Note the logging (rsyslog or syslog) changed in 0.25 & has changed again (slightly) with 0.26.
Probably only matters if you build from source.

But because you are using 0.26+fixes on old 10.04 (so do I) there could be incorrect start up scripts w.r.t. rsyslog-ging etc..

I use the upstart job script & rsyslog setup from mythtv.org:
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
[http://www.mythtv.org/wiki/Simple_rsyslog_Configuration](http://www.mythtv.org/wiki/Simple_rsyslog_Configuration)

The frontend is launched from menu/icon/media-key & start script.

---

### Post by tgm4883 on 2013-01-21
The Ubuntu/Mythbuntu packages don't include 0.26 for 10.04 (build issues). If you guys are building from source, great. If not, where did you get your packages?

[http://www.mythbuntu.org/repos](http://www.mythbuntu.org/repos)

---

