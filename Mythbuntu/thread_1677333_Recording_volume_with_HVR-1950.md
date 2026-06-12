---
title: "Recording volume with HVR-1950"
date: 2011-01-28
forum: Mythbuntu
---

### Post by bcg30506 on 2011-01-28
My Hauppauge USB analog tuner records the volume way too loud, so much so that the sound ends up distorted on several shows.  I found that while it is recording, I can change it to make it just the right levels with:
```
v4l2-ctl -c volume=57000 -d /dev/video2
```
Is there a way to make this permanent or tell mythbackend to set this each time it starts using this device?

---

### Post by nickrout on 2011-01-28
try putting that line in /etc/rc.local so that it is executed on boot.

---

### Post by bcg30506 on 2011-02-07
The rc.local idea did not work as mythbackend is setting the high volume when it starts recording with that device, regardless of my volume setting for playback in frontend using the mixer.

I found a solution though.  I do it in the change channel external script that the backend calls when changing channels or starting a recording on that tuner.  But because there is a delay when it sets the volume, I had to build in a delay by using 2 scripts with one returning immediately so the frontend response is not slowed down.  Then after the timeout of 5 seconds (which seems to cover most cases) the 2nd script lowers the recording volume.

Here they are, starting with the master script that is placed in the change channel external command field in the card setup for mythbackend:
```
#!/bin/bash
# setRecVol
doSetRecVol &
```
```
#!/bin/bash
# doSetRecVol
sleep 5
v4l2-ctl -c volume=57000 -d /dev/video2
```
Hopefully this idea will help out others.

---

### Post by bcg30506 on 2011-02-08
Ugh.  I spoke too soon.  I tested it only when starting to watch live TV and never actually tried to change channels.  The problem is, it doesn't.

When I try to change channels, mythtv thinks the channel changes and updates the filename and start channel in the database, but never physically changes the frequency of the tuner, so you still end up watching the original station even though the Info button says you are watching the new one.

So I guess if you use a channel change script, it expects it to actually change the channel, (as it probably should).  Doh!

So are there any other options to lower the recording volume for this device after mythbackend has started recording?  Anything done before mythbackend's capturing process begins will be overridden by something in myth that sets it.

---

### Post by nickrout on 2011-02-08
run it via a cron script every 10 seconds.

---

### Post by bcg30506 on 2011-02-08
> **nickrout said:**
> run it via a cron script every 10 seconds.

This sounds like a great idea.  Thanks!  I only have 2 questions:

1. What is the overhead with doing so?  Will we notice it while recording or using the frontend?

2. How do I do this?  Not very experienced with cron jobs.

---

### Post by bcg30506 on 2011-02-08
Reading up on cron and it seems it can only run jobs in increments of one minute.  Not bad, but that could mean a recording is too loud for a full minute then suddenly gets quieter.  Plus, my test crontab I created never executed my script in 2 minutes that I watched it.

I found this at another site ([http://serverfault.com/questions/49082/can-i-run-a-cron-job-more-frequently-than-every-minute]("http://serverfault.com/questions/49082/can-i-run-a-cron-job-more-frequently-than-every-minute")) :
```
nohup watch -n 10 --precise /usr/local/bin/setRecVol >/dev/null &
```
to misuse the watch command to run a command every so many seconds.  Pretty slick and it seems to work.  However, I'm not sure of its performance penalty and how to set it up to start by itself.  Can the exact above command simply be placed inside /etc/rc.local?

---

### Post by nickrout on 2011-02-08
yes it could be placed in rc.local.

Take a look at top to see if there is any undue overhead.

As far as cron is concerned, there was a problem with my pvr150 card that required a similar command to be run. To make it run I had a cron job that ran every minute. The cron job ran through a loop 6 times, onl every loop it executed the required command, slept 10 seconds, then looped back. Something like this:

```
for i `seq 1 10`; 
do
/usr/bin/v4l2-ctl -c volume=57000 -d /dev/video2
/bin/sleep 10
done

```

Other thing about cron jobs you have to know is that they start without any environment, so they do not have a PATH set. This means you need to specify a full path to your executables - ie /usr/bin/v4l-ctl as you see in my script above.

---

### Post by bcg30506 on 2011-02-08
I see what you mean about the loop with sleep.  Noted for future reference.  My script seems to be working well with watch currently.  I've added it to rc.local but won't know if that works until the next reboot.  I started watching TV and it was loud for about 2-3 seconds then dropped to normal levels.

Thanks for all your help!

---

### Post by nickrout on 2011-02-08
no problems :)

---

