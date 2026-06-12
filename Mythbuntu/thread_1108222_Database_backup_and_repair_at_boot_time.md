---
title: "Database backup and repair at boot time"
date: 2009-03-27
forum: Mythbuntu
---

### Post by stevanbt on 2009-03-27
Hi,
I'd like to backup and repair (if necessary) my mythtv database at boot time.  What is the best way of doing this - I think I need to do any work on the database before mythbackend starts.

Thanks, Steve.

---

### Post by stevanbt on 2009-03-30
Hi,
I kind-of sorted this, it doesn't work quite like I'd hoped but it does the job.

I copied the mythconverg_backup.pl script to /usr/bin and allowed it to be executed.  I edited the /etc/init.d/mythtv-backend and added a couple of lines in the 'start' code (see lines from #sb start to #sb end).  So this means that whenever the mythtv backend is started it does a db backup (max of 20 rotations) and analyse/repair of the db.  Not to everyone's taste I guess.

```

  start)
	if [ -e $RUNDIR/$NAME.pid ]; then
		PIDDIR=/proc/$(cat $RUNDIR/$NAME.pid)
		if [ -d ${RUNDIR} -a "$(readlink -f ${RUNDIR}/exe)" = "${DAEMON}" ]; then
			log_success_msg "$DESC already started; use restart instead."
			exit 1
		else
			log_success_msg "Removing stale PID file $RUNDIR/$NAME"
			rm -f $RUNDIR/$NAME.pid
		fi
	fi
	prime_firewire

        #sb start - backup database
[B]        SB_LOG='/var/log/mythtv/sbt001.log'
        /usr/bin/mythconverg_backup.pl --rotate 20  >> ${SB_LOG}
        echo "SB backed up database on `date`"  >> ${SB_LOG} 
        
        echo "Started db optimise on `date`"  >> ${SB_LOG}
        /usr/share/doc/mythtv-backend/contrib/optimize_mythdb.pl   >> ${SB_LOG}
        echo "Finished db optimise on `date`"  >> ${SB_LOG}
        [/B]
        #sb end
	log_daemon_msg "Starting $DESC: $NAME "
	start-stop-daemon --start --pidfile $RUNDIR/$NAME.pid \
		--chuid $USER --nicelevel $NICE --exec $DAEMON -- $ARGS
	log_end_msg $?
	;;

```

Thanks, Steve.

---

