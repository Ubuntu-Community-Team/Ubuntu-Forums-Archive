---
title: "Run script before shutdown (pre-shutdown check)"
date: 2012-01-12
forum: Mythbuntu
---

### Post by adamup on 2012-01-12
Hi all,

I'm running mythbuntu 10.10 on a combined FE/BE. I use mythwelcome to shutdown and wakeup the system for recordings. Works like a charm, except...

I also have a manual script that I wrote to grab listings and insert them via mythfilldatabase. The script works great -- I used to have it in the /etc/cron.daily directory and it ran automatically daily. However, my system is pretty slow and if mythfilldatabase happened to run while playing back a recording, playback would get very choppy.

So I'd like to change when I run the script to update listings before shutdown...that way it won't interfere with playback. Per this wiki page: [http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Shutdown.2FWakeup_Options](http://www.mythtv.org/wiki/User_Manual:Detailed_configuration_Backend#Shutdown.2FWakeup_Options), there seems to be "Pre Shutdown check command" that should allow you to run a script before shutting down the machine. I copied the example script and modified it for my use and entered the path in that field, but can't seem to get it to run before myth shuts down. Does anyone have experience doing this? Or have any ideas on getting it to work?

Thanks

---

