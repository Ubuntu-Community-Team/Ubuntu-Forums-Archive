---
title: "Backend Stopping"
date: 2008-11-28
forum: Mythbuntu
---

### Post by uncle hammy on 2008-11-28
I have had 3 instances now where my backend just stops.  When it happens, I get the "Cannot find backend is your ip correct" message from the frontend.  MySQL is still running, and if I go into the MCC on the backend machine and go to Set Up MythTV, then exit out of that, it's back to normal...obviously because that astop and restarts the backend service.  However, while the backend is down, recording get missed, which causes low waf.  The only thing I have noticed is that the 3 instances seem to have been evenly spaced by 7 days, which led me to wonder if it was a dhcp issue because that's my lease time on my dhcp server.  However, I set my backend with a static ip and now, 7 days later it's happened again.

Anybody have any idea what could be going on, and how I could start to track it down?

As a temporary "fix", I thought of maybe trying to come up with a script that would run every 15 minutes and maybe do something like a pgrep on mythbackend and if no pid is returned, restart it.  However, my Linux experience is rather limited, so I don't really no where to begin to do such a thing.  So any help there would be greatly appreciated too.

Thanks,
Scott

---

### Post by ian dobson on 2008-11-28
Hi,

I've written this script to restart the backend when it dies:-

#!/bin/bash
```

##################################################
#
#  Check status of the mythtv backend and
#  restart it if it hasn't done anything for 15 minutes
#  (c) dobs
##################################################


while [ 1 == 1 ]
do
   chk=`ps -A |  grep "mythbackend"`
   if [ "$chk" == "" ]; then
      /etc/init.d/mythtv-backend stop >>/dev/null
      sleep 5
      /etc/init.d/mythtv-backend start >>/dev/null
      datum=`date`
      echo $datum  restarting mythtv-backend >> /var/log/myth-watch.log
   fi

   sleep 30
done

``` 

Hope this Helps
Ian Dobson

---

### Post by uncle hammy on 2008-11-28
Cool, now, can you tell me where to save it, and how to get it to start running at boot up?

Thanks!

---

### Post by ian dobson on 2008-11-29
Hi,

Here's how to install/setup the script.

save the script to /usr/bin
set it to executable with  chmod +x /usr/bin/chk_myth.sh
now go to /etc/init.d with cd /etc/init.d
now create the following script called chk_myth.sh

```
 
#!/bin/sh

chk_myth_start() {
 /data/bin/chk_myth.sh   </dev/null  >/dev/null 2>&1 &
 echo Starting myth watch
}

chk_myth_stop() {
 echo Stopping myth watch
 killall -9 chk_myth.sh
}

chk_myth_restart() {
  chk_myth_stop
  sleep 1
  chk_myth_start
}


case "$1" in
  'start')
    chk_myth_start
    ;;
  'stop')
    chk_myth_stop
    ;;
  'restart')
    chk_myth_restart
    ;;
  *)
    echo "usage $0 start|stop|restart" ;;
    esac
exit 0

```

Now we need to create the links in the correct run level to actually start the script.

ln -s  /etc/init.d/chk_myth.sh /etc/rc2.d/S97watch-myth


To test that is works just try a  /etc/init.d/chk_myth.sh start

Regards
Ian Dobson

---

### Post by uncle hammy on 2008-11-29
OK, I copied & pasted your first script into mousepad and saved it as chk_myth.sh in /usr/bin.  I added the "#!/bin/bash" part that is actually out of the code block at the top of the script, is that correct?

Then I copied & pasted your second script and saved it as chk_myth.sh in /etc/init.d.  

I did the chmod to make the first script executable, and ln command to create the symbolic link.  However, when I did /etc/init.d/chk_myth start all I see is the cursor sitting at a blank line that's it.  In other words, it looks like it's doing something, but I don't see the "starting myth-watch" like I would expect from the echo command in the second script.  Same goes for stopping.

I restarted the machine, and nothing seemed to hang or error during boot.  However, I don't really know if the scripts are working or working correctly.

---

### Post by uncle hammy on 2008-11-29
Could it be that you had me svae the script to /usr/bin yet in your second script in the start section you have...

**/data**/bin/chk_myth.sh

?

---

### Post by ian dobson on 2008-11-29
Hi,

Yep your right it should be 

/usr/bin/chk_myth.sh   

and not

/data/bin/chk_myth.sh   

if you do a ps -A |grep chk_myth.sh   as root ou should see the script/pid.

Regards
Ian Dobson

---

### Post by uncle hammy on 2008-11-29
Well, I changed the /data part in the start section, and I still have the same results.

If I go /etc/init.d/chk_myth start (or stop) I just get a cursor on an empty line that I have to ctrl+c to get back to a prompt.  ps -A |grep chk_myth.sh comes back with nothing at all.  Another strange thing is, if I go sudo /etc/init.d/chk_myth.sh start I get a command not found error, yet if I cd to /etc/init.d and go chk_myth.sh start it goes to the blank line.

SOrry to be a pain, but I seem to have something quite wrong.  Could it have something to do with me copying and pasting your scripts into mousepad?  Or perhaps that I added the #!/bin/bash to the top of the first script?  I am including my exact scripts as they currently sit.

/usr/bin/chk_myth.sh...
```

#!/bin/bash

##################################################
#
#  Check status of the mythtv backend and
#  restart it if it hasn't done anything for 15 minutes
#  (c) dobs
##################################################


while [ 1 == 1 ]
do
   chk=`ps -A |  grep "mythbackend"`
   if [ "$chk" == "" ]; then
      /etc/init.d/mythtv-backend stop >>/dev/null
      sleep 5
      /etc/init.d/mythtv-backend start >>/dev/null
      datum=`date`
      echo $datum  restarting mythtv-backend >> /var/log/myth-watch.log
   fi

   sleep 30
done

```

/etc/init.d/chk_myth.sh...
```

#!/bin/sh

chk_myth_start() {
 /usr/bin/chk_myth.sh   </dev/null  >/dev/null 2>&1 &
 echo Starting myth watch
}

chk_myth_stop() {
 echo Stopping myth watch
 killall -9 chk_myth.sh
}

chk_myth_restart() {
  chk_myth_stop
  sleep 1
  chk_myth_start
}


case "$1" in
  'start')
    chk_myth_start
    ;;
  'stop')
    chk_myth_stop
    ;;
  'restart')
    chk_myth_restart
    ;;
  *)
    echo "usage $0 start|stop|restart" ;;
    esac
exit 0

```

---

### Post by ian dobson on 2008-11-29
Hi,

Try adding a debug message at the start of the script just after the #!/bin/bash something like echo bla bla bla.

If you want to run a script in the current directory you need to include ./ at the front. So:

cd /etc/init.d
./chk_myth.sh

Regards
Ian Dobson

---

### Post by uncle hammy on 2008-11-29
OK, I added echo blah blah blah to script 1.  Then I went to /etc/init.d and simply did sudo myth_chk.sh to execute script 2 with no stop or start.  The result was "blah blah blah" being spit out on the screen then an empty line while the script was executing.  I guess this makes sense since script 1 is an endless loop ( 1 always equals 1), so it would be stuck doing that.  So that tells me that the script 2 is calling script 1 and is working, kind of, I think.

I am thinking that perhaps your script 2 is why I am seeing the empty line, because you have your "echo Starting myth watch" after the actual call to start the script which sticks it into the endless loop before the echo can execute?

That still doesn't explain why the stop command also doesn't display the echo and goes to an empty line.  It also doesn't explain why I get no pid when I do the grep...

Just as an aside, if I find that what I've done so far is causing me some major issues, how can I undo the "ln -s /etc/init.d/chk_myth.sh /etc/rc2.d/S97watch-myth" part to turn it off at boot until we get it fixed?

---

### Post by uncle hammy on 2008-11-30
OK, I modified my 1st script like so to do some checking...

```

#!/bin/bash

##################################################
#
#  Check status of the mythtv backend and
#  restart it if it hasn't done anything for 15 minutes
#  (c) dobs
##################################################

datum=`date`
echo $datum  Starting Myth-Watch >> /var/log/myth-watch.log

while [ 1 == 1 ]
do

   datum=`date`
   echo $datum  Checking status >> /var/log/myth-watch.log

   chk=`ps -A |  grep "mythbackend"`
   if [ "$chk" == "" ]; then
      /etc/init.d/mythtv-backend stop >>/dev/null
      sleep 5
      /etc/init.d/mythtv-backend start >>/dev/null
      datum=`date`
      echo $datum  restarting mythtv-backend >> /var/log/myth-watch.log
   fi

   sleep 30
done

```

and then I went to /etc/init.d and started script 1 using script 2... "chk_myth.sh" no start or stop.  As expected the terminal screen dropped to a blank line while executing, and /var/log/myth-watch.log had an entry for "Starting Myth-Watch", and then entries every 30 seconds for "checking status" until I hit ctrl+c to stop the script; so far so good.

Then, I restarted the machine, and the log file has no new entries.  So, from this I glean that actual watch script is working correctly, but it is not being started at boot up.  So my question is, how can I get script 1 to start running at log in?

Thanks,
Scott

---

### Post by uncle hammy on 2008-11-30
SUCCESS!!  

I didn't give up, and I started messing around.  I discovered that a big part of my problem was the fact that both scripts were named "chk_myth.sh".  So even when I was in /etc/init.d when I called "chk_myth.sh start" it was acutally running the /usr/bin/chk_myth.sh script directly.  I renamed the init.d script to simply "watch-myth" and then "./watch-myth start" worked!  I got the "Starting Watch Myth" echo, and was able to pgrep the chk_myth.sh pid.

Next, I deleted the S97watch-myth simlink out of /etc/rc2.d, because it still was not starting at boot.  

I then ran "update-rc.d /etc/init.d/watch-myth defaults 97" which didn't work quite as I hoped, because it added a simlink into /etc/rc0.d - /etc/rc6.d (I'll need to review how to only add it to run level 2).  However I rebooted and low and behold, "pgrep chk_myth.sh" turned up a pid, and there was a "Starting Myth Watch" entry in /var/log/myth-watch.log!  So, finally I deleted all the simlinks accept for in /etc/rc2.d and rebooted...with same results!

As a final test, I "/etc/init.d/mythtv-backend stop" to shut down the backend service.  Continually checking with "pgrep mythbackend" showed no pid for 30 seconds, then suddenly it was back!

Thanks for all your help getting me going!

Scott

---

### Post by SiHa on 2009-03-08
Just wanted to say 'Thanks'.
Lately, the backend has been going away for no reason that I'm clever enough to fathom, leading to a rapidly plummeting WAF. I remembered reading this thread last year and thought I'd give it a go.

Following posts #2 & #4, and ensuring the two scripts have different names, it now seems to be working flawlessley. I rebooted, stopped mythtv-backend, and 30 seconds later, there it was again!

One year into the MythTV experience, and I think I'm nearly there. I'm dreading March 25th, all DVB-T channels on Rowridge are being shuffled so I'll have to rescan :frown:

Thanks again.

---

### Post by toorima on 2009-03-08
Another option to keep services up is to use monit, there is a guide on the forum here how to set it up and monitor mythtv.

---

### Post by SiHa on 2009-03-08
Thanks, I'll have a look.

---

