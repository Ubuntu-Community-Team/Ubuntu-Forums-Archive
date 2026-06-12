---
title: "What would be the best way to restart gdm if mythfrontend crashes?"
date: 2008-06-26
forum: Mythbuntu
---

### Post by finn on 2008-06-26
Hi all,

I have been running myth for quite a while, but only installed mythbuntu 8.04 yesterday.  

What would be the easiest way to have gdm restart if the mythfrontend process stops?  I ask because i'm often away on work trips, and need the TV to be self-healing if it crashes.

cheers,
Finn.

---

### Post by ian dobson on 2008-06-26
Hi,

I wrote this scrpt a while back to restart the MythFrontend when it dies. Hope you can make some use of it.

```

#! /bin/bash
# Provides:          check if the Myth-Frontend is still running
# Short-Description: if it dies restart it
# Author:            Ian Dobson (i.dobson {at} planet-ian.com
sleep 60  #Startup delay
while [ "1" != "0" ]; do
   Active=`ps -A| grep "mythfrontend"`
   if [ "$Active" == "" ]; then
      killall -15 gdm
      echo  "mythfrontend  Dead" > /var/log/mythtv/frontend.log
      sleep 5  #delay after killing gdm
      /etc/init.d/gdm start
     sleep 15  #delay after stopping/restarting gdm
   fi
   sleep 30    #check if the frontend is dead every 30 seconds
done

```

Just create an init script that calls this bash "program". You might need to adjust the 5 second delay, based on how quickly killall kills all gdm processes and how long linux takes to lean up the mess left behind.

Regards
Ian Dobson

---

### Post by uopjohnson on 2008-06-26
There used to be a nice guide on wilsonet.com for writing a script with irexec that would allow gdm to be restarted from the remote control, you might want to check that out.  I have separate frontends so I haven't used it in a while, I just tell my wife to hit the power button on the frontend to shut the system down and then hit it again to start it up.  That generally heals all wounds, and has very few ways to mess it up.  Not a good idea though with a combined backend becuase you will drop active recordings.

---

### Post by finn on 2008-06-26
Thanks for the hints, I'll give that bash script a go.  I had been mucking about with monit, which I now successfully have keeping my ssh server, mysql and backend running.

---

### Post by finn on 2008-08-17
I found this page recently: [http://www.vf.utwente.nl/~czenkom/mythht.html](http://www.vf.utwente.nl/~czenkom/mythht.html)

So, what i did was add this line to my user's crontab:
```
* * * * * pidof mythfrontend.real 2>&1 > /dev/null || ( export DISPLAY=":0.0" && mythfrontend --service 2>&1 > /dev/null & )
```

The changes are required as with mythbuntu the process name for the frontend is mythfrontend.real, and the way that mythfrontend is launched is with the --service option.

This combined with monit making sure that gdm, mysql, mythbackend and ssh keep running should mean that everything just keeps on working.  Here is my monitrc file contents for making the services stay up:
```

# Monitoring GDM
check process gdm with pidfile /var/run/gdm.pid
start program = "/etc/init.d/gdm start"
stop program = "/etc/init.d/gdm stop"
if 5 restarts within 5 cycles then timeout
group server

# Monitoring MythTV Service
check process mythtv with pidfile /var/run/mythtv/mythbackend.pid
start program = "/etc/init.d/mythtv-backend restart"
stop program = "/etc/init.d/mythtv-backend stop"
if failed port 6544 then restart
if 5 restarts within 5 cycles then timeout
group server

# Monitoring Mysql Service
check process mysql with pidfile /var/run/mysqld/mysqld.pid
group database
start program = "/etc/init.d/mysql start"
stop program = "/etc/init.d/mysql stop"
if failed host 127.0.0.1 port 3306 then restart
if 5 restarts within 5 cycles then timeout
group server

#Monitoring ssh Service
check process sshd with pidfile /var/run/sshd.pid
start program "/etc/init.d/ssh start"
stop program "/etc/init.d/ssh stop"
if failed port 22 protocol ssh then restart
if 5 restarts within 5 cycles then timeout
group server

```

---

