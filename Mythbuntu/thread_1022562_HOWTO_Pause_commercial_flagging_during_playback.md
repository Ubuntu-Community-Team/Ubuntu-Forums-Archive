---
title: "HOWTO: Pause commercial flagging during playback"
date: 2008-12-26
forum: Mythbuntu
---

### Post by jbrown123 on 2008-12-26
I am using 8.10 Intrepid Mythbuntu.  I have a combined frontend / backend system running on a Dell P4 3.0GHz single-processor box.  I use an HDHomeRun for OTA capture.  I know many people have reported the problem of having jerky playback while commercial flagging is running.  This is especially true when watching HD content.

I was having this problem as well.  I basically have one true HD station that broadcasts in 1080i.  Anytime I watch content from this station and commercial flagging jobs are running, the playback is jerky.  The only way I could find to solve the problem was to pause the commercial flagging jobs.  That is a little tedious to have to pause the jobs, then remember to turn them back on again when you are finished watching videos.  More than once I've come back the next day to find dozens of jobs in the queue because I forgot to restart the commercial flagging jobs.

Well, I finally got fed up enough with the problem to do something about it.  I poked around and could not find anyone who had solved this problem so I set out to do it myself.

Here is the solution I came up with.  I'm sure it is possible to do this more elegantly, but this method works and that's good enough for me at the moment.

First, I must give credit where credit is due.  I could not have solved this problem without the fine information contained in this post: [http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

I took this as a basis and made my own tool, pausecommflag, that is a derivative of this work.  I strongly encourage you to read the above post to get some additional background before proceeding.

Here's the basic plan.  We need to pause the commercial flagging processes when we are watching video and then resume them when we quit watching video.  Seems simple enough and maybe, one day, this will be an option in Myth.  For the moment, let's try to solve the problem from 'outside the box'.

How can we tell when we are watching video?  One simple way is to look at the CPU utilization of the frontend process (mythfrontend.real).  If it is above a certain threashold (40% in my case) then we need to pause the commercial flagging jobs.

Next problem, how do we pause the commercial flagging jobs?  Well, I'm sure there is some internal way to do it because the option is offered from the system status page.  However, I was too lazy to figure that out, so I used the Linux STOP signal instead.

Lastly, how do we restart the commercial flagging jobs?  Well, since we put them to sleep by sending the STOP signal, we have to  resume them with the CONT signal.

Sounds simple enough.  Now let's get down to brass tacks and build some code.

For most of the following steps you will need to be root.  Instead of typing **sudo** in front of everything, I went the dangerous route and did **sudo -s**

I know that's "against the rules" but it sure was easier for me!

First we need a daemon that will check the CPU usage every so often.  I use the following code:

```
#!/bin/bash
# ==============================================================
# Limit MythCommFlag from running during video playback
# ==============================================================
# adapted from http://ubuntuforums.org/showthread.php?t=992706

# Variables
CPU_LIMIT=40        # Maximum mythfrontend CPU consumption before shutting down commercial flagging
DAEMON_INTERVAL=3   # Daemon check interval (seconds)

while sleep $DAEMON_INTERVAL
do
        if [ $(top -bn1 | gawk 'NR>6 && $12 ~ /mythfrontend/ {print $9}') -gt $CPU_LIMIT ]; then
                for i in $(top -b -n1 | gawk 'NR>6 && $12 ~ /mythcommflag/ && $9>0 {print $1}')         # Violating PIDs
                do
                        # echo Sleeping $i
                        kill -stop $i &   # sleep active commercial flagging
                done
        else
                # wake up sleeping commercial flagging operations
                for i in $(top -b -n1 | gawk 'NR>6 && $12 ~ /mythcommflag/ && $9<1 {print $1}')         # Sleeping PIDs
                do
                        # echo Waking $i
                        kill -cont $i &   # sleep active commercial flagging
                done
        fi
done

```

Save the code above into **/root/pausecommflag_daemon.sh**

Make sure this is owned by root (**chown root:root /root/pausecommflag_daemon.sh**.  Also make sure it is executable (**chmod 755 /root/pausecommflag_daemon.sh**).

That has the daemon, now we need a way to run it as a service.  So, copy the following code into **/etc/init.d/pausecommflag**

```
#!/bin/sh
#
# Script to start CPU limit daemon
#
set -e
. /lib/lsb/init-functions
case "$1" in
start)
nohup /root/pausecommflag_daemon.sh &
;;
stop)
ps -eo pid,args | gawk '$3=="/root/pausecommflag_daemon.sh"  {print $1}' | xargs kill   # kill daemon
killall -s CONT mythcommflag    # resume any paused commercial flagging
;;
restart)
ps -eo pid,args | gawk '$3=="/root/pausecommflag_daemon.sh"  {print $1}' | xargs kill   # kill daemon
killall -s CONT mythcommflag    # resume any paused commercial flagging
sleep 5
/root/pausecommflag_daemon.sh &
;;
status)
ps -eo pid,args | gawk '$3=="/root/pausecommflag_daemon.sh"  {print}' | wc -l | gawk '{ if ($1 == 1) print " * pausecommflag daemon is running"; else print " * pausecommflag daemon is NOT running" }'
;;
esac
exit 0

```

You need to make sure this is owned by root and executable as well.  Do the same steps as before (**chown root:root /etc/init.d/pausecommflag** and **chmod 755 /etc/init.d/pausecommflag**).

Now install your new daemon as a service:
**update-rc.d pausecommflag defaults**

At this point you can reboot if you want.  The service should start automatically.  However, you can just start it manually now and all should be well.

```
cd /etc/init.d
service pausecommflag start
```

You can check that everything is working by running **top** in a terminal (I connect in from another machine via SSH) and seeing that the commercial flagging jobs are running.  Then start watching a video and within a few seconds (3 seconds by default) you should see the commercial flagging jobs (mythcommflag) disappear from the list.  They should reappear within a few seconds after you stop watching video.

Depending on your processor and other factors you may need to adjust the two variables at the top of the script (/root/pausecommflag_daemon.sh).  The **CPU_LIMIT** determines  what percentage of the CPU the front end process must use before it kills the commercial flagging.  If the front end is above this percentage, commercial flagging is turned off (paused), if it is below this percentage, commercial flagging is resumed.

The **DAEMON_INTERVAL** determines how often the system checks to see if it needs to pause or resume commercial flagging.  You can increase this delay if you want it to check less often.  I would not suggest making it much shorter than the default of 3 seconds for performance reasons.

I hope you find the above information useful.  I am certainly open to suggestions for improvement.  If someone wants to figure out and/or build a tool to pause and resume commercial flagging using the existing Myth messaging system, that would be better.

Thanks,

- James

---

### Post by jboehm on 2008-12-27
Great job on the HOWTO.  While this might be added to mythtv someday, I kind of doubt it.  Processor tech is quickly out pacing mythtv's needs, especially with nVidia's new VDPAU driver.  I recently upgraded from a P4 3.2 to a C2D 2.67.  I used to be able to commflag 1 show and watch one HD show at the same time under mythtv .20.  Now I can commflag 2HD shows and 2SD shows while watching 1 HD show under mythbuntu 8.10 on the C2D.

In both systems I used this commflag command.  You will probably need to install ionice.

ionice -n 7 nice -n 19 mythcommflag -j %JOBID% -V %VERBOSELEVEL%

You might try comflagging 2HD shows by default and pausing one or both when needed (when you not watching.)  Your system should be able to handle this. You should also be able to change JobQueueCPU to 2.  Which means there is no auto pausing or NICing of jobqueue items.  They will run at full speed and nice and ionice, in the command, will handle thread competition.

If you are using CPU freq scaling you will need to tweak the scaler so that it includes NICEd tasks in it calculation, otherwise it will slow down the cpu even when commflag jobs should be running all out.

Great job,
Jon

PS.  You should consider adding your howto to the mythtv wiki.

---

### Post by jbrown123 on 2008-12-27
Thanks for the kind words.  It was just a frustration for me that finally bubbled to the top of the "DO IT" list.  I figured I'd give back, in my own little way, to the community that made MythTV available to me.

I've thought about putting a copy in the Myth Wiki.  Thanks for the encouragement.  I think it needs to be 'prettied up' a bit before it hits the wiki though.

I sure wish the Myth developers would put this in as an option (pause commercial flagging during playback).  That would make life much easier for lots of folks.  While I realize that there is always new hardware coming out, not everyone upgrades immediately.  Lots of folks build a Myth box from the stuff that is laying around.  Because of that, it will be many years before 'everyone' has hardware good enough to play back full HD (1080i) and do something else at the same time.  This is complicated by the US change to ATSC/HDTV in Feb 2009.  This will simply create more users that have the HDTV playback problems.

FYI, I've already installed the daemon that changes the nice value on mythcommflag to 19.  That made no difference in how my frontend performed.

Thanks,

- James

---

### Post by itlarson on 2009-02-07
Thanks for this.  I've never used the commercial flagging because of this problem.  I don't know why it isn't built into mythtv.

---

### Post by jbrown123 on 2009-02-12
I found that I had the same playback problems when using MPlayer to watch video files.  So, I updated the daemon to watch for both mythfrontend and mplayer.  Here is the new daemon.  

If you already installed the old daemon using the previous instructions, just copy this over /root/pausecommflag_daemon.sh.  If you are installing for the first time, just use this daemon instead of the original version (follow all the other instructions, just substitute this code for the daemon code).

```

#!/bin/bash
# ==============================================================
# Limit MythCommFlag from running during video playback
# ==============================================================
# adapted from [http://ubuntuforums.org/showthread.php?t=992706](http://ubuntuforums.org/showthread.php?t=992706)

# Variables
CPU_LIMIT=40        # Maximum mythfrontend CPU consumption before shutting down commercial flagging
DAEMON_INTERVAL=3   # Daemon check interval (seconds)

while sleep $DAEMON_INTERVAL
do
	# necessary to do the +0 trick to force there to be a value even when MPLAYER or MYTHFRONTEND
	# are not running
	(( MYTHFRONTEND=$(top -bn1 | gawk 'NR>6 && $12 ~ /mythfrontend/ {print $9}') + 0 ))
	(( MPLAYER=$(top -bn1 | gawk 'NR>6 && $12 ~ /mplayer/ {print $9}') + 0 ))
	
	#echo Myth = $MYTHFRONTEND
	#echo MPlayer = $MPLAYER

	if [ $MYTHFRONTEND -gt $CPU_LIMIT -o $MPLAYER -gt $CPU_LIMIT ]; then
		for i in $(top -b -n1 | gawk 'NR>6 && $12 ~ /mythcommflag/ && $9>0 {print $1}')         # Violating PIDs
		do
			# echo Sleeping $i
			kill -stop $i &   # sleep active commercial flagging
		done
	else
		# wake up sleeping commercial flagging operations
		for i in $(top -b -n1 | gawk 'NR>6 && $12 ~ /mythcommflag/ && $9<1 {print $1}')         # Sleeping PIDs
		do
			# echo Waking $i
			kill -cont $i &   # wake sleeping commercial flagging
		done	
	fi
done

```

Now that we have the new daemon in place, we need to kick-start it.

If the old daemon is already running, you will need to stop it first with **sudo /etc/init.d/pausecommflag stop**.

To start the new daemon use **sudo /etc/init.d/pausecommflag start**.

If you don't do these steps, the new daemon will not be active until you reboot.

I hope others find this information useful.  It certainly improves my viewing!

---

