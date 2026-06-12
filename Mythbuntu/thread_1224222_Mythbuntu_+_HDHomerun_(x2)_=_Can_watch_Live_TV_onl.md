---
title: "Mythbuntu + HDHomerun (x2) = Can watch Live TV only once per reboot"
date: 2009-07-27
forum: Mythbuntu
---

### Post by sydneysuder on 2009-07-27
Hi,

After much mucking about with Myth on OSX and getting nowhere due to that port's lack of support for the HDHR DVBT version I sequestered a machine from work for testing purposes.

I installed and updated to the latest (as it is required for the DVBT HDHR to work properly). That all went quite well. I have Myth recognize the 4 tuners (2 for each HDHR) , I can watch liveTV and recordings... except that there are couple of problems:

1. I cannot record anything (scheduled) unless I leave the frontend watching liveTV. That is, If I schedule a recording for 5:00 pm I have to start the frontend and start watching liveTV (on any channel not necessarily the one I am going to tape) BEFORE 5:00 pm. If I don't do this it will create a recording of 0MB (which is useless)
2. If I start watching liveTV on the master backend (with frontend) and then exit LiveTV by pressing the ESC key (takes me back to the menu) I cannot go back into LiveTV unless I REBOOT the system.   Re-starting the tuners doesn't work, Logging out doesn't work, re-running myth setup doesn't work, only rebooting the machine works.
3. For some reason Myth gradually locks all the tuners on the two HDHRs. Even if I am not watching liveTV the first LED on the first tuner will come shortly after starting the front end. After a few minutes the same happens on tuner 1, then the same cycle repeats on the other HDHR.  This happens whether or not  I am watching liveTV or recording anything (manually or scheduled) . If I try to use any of the tuners with the hdhomerun_config_gui and VLC from another computer It fails and the MythTv machine needs to be rebooted as per item 2 above.
4. I can't watch LiveTV on a frontend OSX install. It is the latest build (July 6 09) downloaded from sniderpad.  I get an error on the log "Can't open file myth://" and the frontend just hangs needing to be manually terminated. As a side-effect the myth backend needs to be rebooted because it exhibits the symptoms described in item 2 above.

Any help with the above is greately appreciated.

Cheers.

P.S. I know you'll ask me for the logs. I will procure them once the scheduled recordings I have for tonight are finished. I don't want to touch the machine until that is done.

---

### Post by sydneysuder on 2009-07-28
OK Here are the logs

[http://mythbuntu.pastebin.com/f1416cb79](http://mythbuntu.pastebin.com/f1416cb79)

The logs are from :

1. Reboot the computer
2. Go to watch live tv
3. change channel a couple of times.
4. Pres esc to go back to menu
5. Press "watch live tv"

You can see that at 07:07.03 I pressed esc. After that it won't get back into live TV

Any ideas?

---

### Post by Mister.Vash on 2009-07-28
Not sure if this is the cause of the issue or just a symptom, but the lines that stick out are:
HDHRRec(1): AdjustFilters() no pmt or no pat


Can you take a look at changing these settings and see if this works for you?
[http://www.mailinglistarchive.com/mythtv-dev@mythtv.org/msg13138.html](http://www.mailinglistarchive.com/mythtv-dev@mythtv.org/msg13138.html)

---

### Post by sydneysuder on 2009-07-30
Thanks mate, changing that setting fixed all my issues!

I have another issue but I may start a different thread for that.

---

### Post by sydneysuder on 2009-07-30
Just for the heck of it I just tried using a frontend from work via VPN.  The connection speed is not good but being able to watch TV on my computer at work (even if in 10 second intervals) had a geek factor I could not resist! (Until the boss showed up :-()

---

