---
title: "Pausing the job queue?"
date: 2016-09-10
forum: Mythbuntu
---

### Post by SagaciousKJB on 2016-09-10
I setup about 160 recordings in my job queue to transcode, but I need to restart the computer that mythbackend is on. I know that if I restart it, it is going to destroy one of the recordings. I am wondering if there is a way to pause the remaining queue, and let the currently running jobs finish and then shut down? I was really hoping there was an actual feature for this somewhere in myth that I am not finding, but I did think of a way that I might be able to script it...

1. Query jobqueue table in the DB to find all jobs with "Queued" status and replace that to "Pause"
2. Check every 1s if there are still any jobs labeled "Running"
3. Once no jobs are found "Running", shutdown
4. Once we want to resume, do 1 again but switch "Pause" to "Queued"

I can probably figure out the SQL and stuff to do this, I know it's not very complex ( though I don't really know the first thing about SQL ), but I am just wondering if altering these spots in the jobqueue database will actually have the effect I'm anticipating of controlling the queue? I know from the jobqueue menu the user can select to pause or run, restart, etc. the jobs but I don't know if this only effects the DB or if there is other processing triggers going on--maybe a PID is killed here or there, not sure.

Edit:

Well I guess the SQL I needed was simple enough to learn in a few minutes, so I whipped up a bash script, it seems to modify the database the way I want ( confirmed with phpmyadmin and a duplicate DB for testing) but I am still hesitant to try this as I'm not sure that directly modifying the database to control the queue is a good idea? I'm pretty sure there's no caveats I'm over looking, but hey that's the point of asking.

```
#!/bin/bash

QUEUED=1
PENDING=2
STARTING=3
RUNNING=4
STOPPED=5
PAUSED=6
RETRY=7
ERRORING=8
ABORTING=9
DONE=256
FINISHED=272
ABORTED=288
ERRORED=304
CANCELLED=320
DB_USER='mythtv'
DB_PASS=''
DB='mythtesting'
COMMAND=$1

if [ $1 = "Pause" ] ; then
	mysql --user=$DB_USER --password=$DB_PASS $DB << EOF
		UPDATE jobqueue SET status=$PAUSED WHERE status=$QUEUED;
EOF
	while : ; do
        	if pidof mythtranscode ; then
                	echo "Running transcodes (PIDs above)";
			sleep 1m;
	        else
        	        echo "Can now shut down";
	                exit 0;
		fi
	done
elif [ $1 = "Run" ] ; then
	mysql --user=$DB_USER --password=$DB_PASS $DB << EOF
		UPDATE jobqueue SET status=$QUEUED WHERE status=$PAUSED;
EOF
else
	echo "Tell me to run or pause";
	exit 1;
fi
```

---

