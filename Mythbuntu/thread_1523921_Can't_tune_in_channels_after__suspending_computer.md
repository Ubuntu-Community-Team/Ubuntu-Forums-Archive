---
title: "Can't tune in channels after  suspending computer"
date: 2010-07-04
forum: Mythbuntu
---

### Post by themrfreeze on 2010-07-04
Hi all.

I just built a new HTPC system using Mythbuntu 10.04, a GigaByte AMD motherboard, and the HD-5500 ATSC tuner card from my old HTPC rig (built about 18 months ago).  It worked pretty decently out of the box, but I just discovered an odd problem.

The computer suspends (S3 mode) and wakes up fine, but once it wakes up, MythTV can no longer tune in TV channels.  When it tries, the five signal letters you see on screen (LAMGV) only come up as L----.  Rebooting the computer fixes the problem, but I really want to be able to suspend the computer.

Has anybody come across this particular problem before?  I saw a few threads that suggested that when waking up, the tuner card's driver might not be loading before MythTV, but I don't know if that problem would be responsible for the tuning issue.  I also don't know enough about how Linux loads drivers to troubleshoot this.

TIA for any info you can provide.

Chris

---

### Post by ian dobson on 2010-07-04
Hi,

What happens if you restart mythbackend? Does it find the tuners?

What happens if you unload then reload the tuner card drivers then restart the mythtvbackend? Does it find the tuners?

Do you see any stranged messages in the system log when you wake up the box?

Regards
Ian Dobson

---

### Post by themrfreeze on 2010-07-04
I tried restarting Mythbackend by going into the backend config program, then exiting from it.  Didn't help.

I found an old thread on the pcHDTV forum about the same basic problem, and a reply said this:

> 
You have to tell it to remove the kernel modules before suspending and reload them upon resuming. This is how to do it on sidux; ubu may be the same:

Create a file /etc/pm/config.d/unload_modules containing this:

Code:

SUSPEND_MODULES="cx88_dvb cx8802 cx8800 cx88xx"


Make it executable:

Code:

chmod 755 /etc/pm/config.d/unload_modules



I tried doing this, but it didn't seem to help either.  Tried executing this manually, the running the backend setup again to restart mythbackend.  No go.

I looked through the syslog and the pm_suspend log for anything related to cx88 or hd5500, and didn't see anything that looked obviously like a failure.  Then again, my troubleshooting skills are a little weak when it comes to Linux.

I don't know how to unload/reload a driver manually, but if somebody can give me some instructions, I'll see what happens.

Thanks!

---

### Post by matt06 on 2010-07-05
I have this problem with live tv and digital tuners on my *frontend only* after suspending and waking.  I don't suspend or wake my backend so I can't speak of that.

Last time I investigated the only thing of note was "SwitchTo() not switching to current" in the frontend log.  IIRC, the backend gave no hints in the log.  I rarely use live tv so it's not a big enough issue for me to poke around anymore.

---

### Post by nickrout on 2010-07-05
> **themrfreeze said:**
> I tried restarting Mythbackend by going into the backend config program, then exiting from it.  Didn't help.

I found an old thread on the pcHDTV forum about the same basic problem, and a reply said this:



I tried doing this, but it didn't seem to help either.  Tried executing this manually, the running the backend setup again to restart mythbackend.  No go.

I looked through the syslog and the pm_suspend log for anything related to cx88 or hd5500, and didn't see anything that looked obviously like a failure.  Then again, my troubleshooting skills are a little weak when it comes to Linux.

I don't know how to unload/reload a driver manually, but if somebody can give me some instructions, I'll see what happens.

Thanks!

After you have suspended and woken up, and the backend is not working right, try manually removing and reloading the drivers:

```
sudo modprobe -r cx88_dvb cx8802 cx8800 cx88xx
sudo modprobe cx88_dvb cx8802 cx8800 cx88xx
```

(Not sure if you can do it all on one line like that you MAY need to do them one at a time)

See if it then works. If it does, it indicates that the drivers need reloading after a suspend, and you are on the right track. 

If not the error message might tell us something. In fact before you do anything you should look at /var/log/mythtv/mythbackend.log :)

---

### Post by themrfreeze on 2010-07-05
> **nickrout said:**
> After you have suspended and woken up, and the backend is not working right, try manually removing and reloading the drivers:

```
sudo modprobe -r cx88_dvb cx8802 cx8800 cx88xx
sudo modprobe cx88_dvb cx8802 cx8800 cx88xx
```


Okay, here's what happened.

I suspended and woke the computer back up.  MythTV would not tune channels.

I then terminated mythbackend by running the backend setup program.

Then I switched over to a terminal window, and issued the two commands above.  The modprobe -r worked fine.  When I issued the second command, I got this error:

> 
[randomnumbers.randomnumbers] cx88_dvb: Unknown parameter "cx8802"
FATAL: Error inserting cx88_dvb (/lib/modules/2.6.32-23-generic/kernel/drivers/media/video/cx88/cx88-dvb.ko): Unknown symbol in module, or unknown parameter (see dmsg)


I then issue the command a second time, and now no error is generated.

If I then quit the backend setup and try to watch TV, it now works.

I looked through the mythbackend.log, and am seeing some errors about it being unable to open the DVB frontend device due to a fatal error or too many attempts.  It also says that no valid capture cards are defined in the database.
  
So, it seems like the driver isn't loading correctly.  I guess the question is whether it's simply not loading before mythtv wakes up, or whether it *is* trying to load before mythtv, but the error seen when issuing the modprobe command is actually the problem.

---

### Post by nickrout on 2010-07-06
1. you may not need to stop the backend; and

2. you may need to fine tune the modprobe command, do ```
lsmod|grep cx88
```

Note which is the first line in the response (this will be the last module loaded and if you remove it it should remove anything else it depends on. When you reload it, it should load it's dependencies. You can then just modprobe -r that particular module and modprobe it back again)

---

### Post by themrfreeze on 2010-07-06
I did the lsmod command, and the first line is 'cx88_dvb'.  Tried removing and reinstalling this driver with mythTV running, and it didn't work.  Did it with the backend disabled, and it worked.

So, it looks like it's a matter of figuring out how to get this driver to load before the backend loads.  Obviously works okay when rebooting, but not when waking up.

---

### Post by ian dobson on 2010-07-06
Hi,

Your running mythbuntu 10.04 right. If so why not just edit the startup scripts for myth-backend so that it unloads then loads the required drivers.

The configuration script is in the /etc/init directory and called something like mythtv-backend.conf and just add something like this:-

```
pre-start script
  rmmod cx88_dvb
  sleep 5
  modprobe cx88_dvb
  sleep 5
end script
```

The pre-start script is called before mythtv is started and in this case it kills the cx88 driver, waits abit, starts it and waits abit more before myth-backend is started.


Regards
Ian Dobson

---

### Post by themrfreeze on 2010-07-06
Thanks Ian.  I added the code you suggested, but the addition appears to prevent the backend from starting at all.

---

### Post by ian dobson on 2010-07-06
Hi,

When you try and manually start mythtv-backend what do you see:-

stop  mythtv-backend
start mythtv-backend

All this pre-start script does is stop the cx driver wait abit then restart it, it shouldn't stop the backend from starting.

Heres my startup script:-

```

# MythTV Backend service

description     "MythTV Backend"
author          "Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

pre-start script
    # wait for listen on port 80
    while ! nc -q0 localhost 80 </dev/null >/dev/null 2>&1; do
        sleep 1;
    done
end script

script
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script

```
Regards
Ian Dobson

---

### Post by themrfreeze on 2010-07-06
Okay, this is getting a bit weird.  And I really appreciate all the help.

With the original myth-backend.conf file in place, I put the computer to sleep, then wake it back up.  If I stop and restart the mythtv-backend (using sudo), it's still not capable of tuning.
 
I re-added the script you posted earlier to the myth-backend.conf file after the 'respawn' line (I had it before that line earlier, which may have been wrong).  If I put the computer to sleep and wake it up, it still won't tune channels.  However, if I stop and restart mythtv-backend now (again using sudo), it will tune channels.  

When I restart mythtv-backend, I get "mythtv-backend start/running, process <some number>".  So, it appears to be doing what it should.

Here's what the mythtv-backend.conf file now looks like:
> 
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on starting shutdown

#expect fork
respawn

pre-start script
rmmod cx88_dvb
sleep 5
modprobe cx88_dvb
sleep 5
end script

script
        USER=mythtv
        ARGS="--logfile /var/log/mythtv/mythbackend.log --user $USER"
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend $ARGS
end script


I guess the question is why the conf file works when the stop/restart is done manually, but not when the computer wakes up.  Is it possible that the cx88-dvb driver *has* to be stopped and started using sudo?

---

### Post by ian dobson on 2010-07-06
OK,

Now I think I understand whats going on. You suspend your box and when you wake it up the system thinks that lo is already up and myth-backend is already running, so upstart doesn't restart it.

What you need to do is stop myth-backend when you suspend and start it when you wake up. 

I don't use suspend/resume so I'm not sure where you should add the start/stop commands. Could you try just stopping the myth-backend process with stop mythtv-backend then suspending and waking up again, just to see if the startup script works correctly.

Regards
Ian Dobson

---

### Post by themrfreeze on 2010-07-07
If I manually stop mythtv-backend, then suspend the computer, then wake it up, mythtv-backend doesn't automatically start...it has to be done manually.

Kinda makes sense....if suspend didn't shut it down, then waking shouldn't automatically start it up.

The process number for mythtv-backend is the same before and after sleeping the computer, but I'm not sure if that means that it's not stopping before sleep, or whether the OS is assigning the same process number after the computer wakes and the backend is restarted.

I guess the next step is to figure out how sleep mode works, and determine whether the OS is stopping the backend process before sleep or not.  If it isn't, it sounds like we need to force it to.

---

### Post by themrfreeze on 2010-07-07
Okay, I've made some progress.

The directory /etc/pm/sleep.d is where a user can place scripts that run when you sleep/hibernate/wake the computer.  I placed a script in this directory called "66_mythbackend_stopstart", which contains this:

> 
#!/bin/sh

# Stop mythtv-backend before suspend, and restart after resuming

case "$1" in
	suspend)
		modprobe -r cx88_dvb
		sleep 1
		stop mythtv-backend
		sleep 1
		;;
	resume)
		modprobe cx88_dvb
		sleep 1
		start mythtv-backend
		sleep 1
		;;
esac


With this script in place, the TV tuning now works after a suspend.  However, now the backend doesn't seem to start automatically upon reboot.  Not sure why that is.

EDIT:  Hmmm, now it works fine after a power cycle.  Go figure.  In any case, adding the script has fixed the problem.  Thanks everybody for helping with this!

---

