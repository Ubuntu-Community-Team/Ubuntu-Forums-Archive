---
title: "Restarting the front end via a script and remote"
date: 2009-11-04
forum: Mythbuntu
---

### Post by gwagchunks on 2009-11-04
Hello Everyone

I'm stuck again! I want to use a button on my remote to restart the front end if it locks up / needs restarting. I don't have a problem with assigning the script to lirc and myth, just can't get my head around the script! I have copied this script from somewhere I googled:

```

#!/bin/bash
PROG=mythfrontend
RUNNING=`ps -e | grep -c $PROG`

if [ `echo $DISPLAY | grep -c "0"` -ge 1 ]
then
	if [ $RUNNING -ge 1]
	then	
		killall $PROG
	else
	( $PROG & )
	fi
fi
exit 0


```

I have made it executable and assigned it to my remote control. When I run it from a terminal it doesn't shut down the front end, just starts a another one. If I run killall -r mythfrontend from the terminal it kills the frontend. if I change the script to use killall -r $PROG or killall -r mythfrontend it still does not work, just starts another front end. Any ideas please? 

Thanks as aways

---

### Post by SiHa on 2009-11-05
From memory, the killall command needs to be > killall -r mythfrontend.real. Mythfrontend is merely the wrapper that runs the file mythfrontend.real.

I'm sure that's what I have in my script to do just what you're trying to do.

---

### Post by gwagchunks on 2009-11-05
> **SiHa said:**
> From memory, the killall command needs to be . Mythfrontend is merely the wrapper that runs the file mythfrontend.real.

I'm sure that's what I have in my script to do just what you're trying to do.

Thanks for the reply SiHa. I'll change the script tonight when I get in front of the box and see if that works. Like I say, killall -r mythfrontend works from the terminal, not in the script. I was wondering if it was a permissions thing or something. One of these days (years) I will know what I'm doing!

---

### Post by mythding on 2009-11-05
> **SiHa said:**
> From memory, the killall command needs to be . Mythfrontend is merely the wrapper that runs the file mythfrontend.real.

I'm sure that's what I have in my script to do just what you're trying to do.

I have a script to do the same thing and this is how I do it. It works great.

---

### Post by gwagchunks on 2009-11-05
Hi Guys

I'm still having no luck. Could one of you kind people post a copy of your script so I can try it? I still cannot get mine to work. I have tried changing the line to " killall -r mythfrontend " and " killall mythfrontend " and all other combinations (mythfrontend.real) etc. If I run the command killall -r mythfrontend from a terminal, it will kill off the frontend fine. When I run it in the script, it just starts another frontend and does not kill the current running frontend. Will I ever understand myth and linux?! :D

---

### Post by Neon Dusk on 2009-11-05
The script I use is :-

```

#!/bin/sh
FRONTRUNNING=0;
WELCOMERUNNING=0;
 
for x in `ps -C mythfrontend.re | grep -v PID` end; do
    test $x != 'mythfrontend.re' && continue
    FRONTRUNNING=1;
done

for x in `ps -C mythwelcome | grep -v PID` end; do
    test $x != 'mythwelcome' && continue
    WELCOMERUNNING=1;
done
 
if [ $FRONTRUNNING = 1 ]; then
  #kill the process
   kill -9 `ps -aef | grep 'mythfrontend.re' | grep -v grep | awk '{print $2}'`
fi
  
if [ $WELCOMERUNNING = 1 ]; then
  #kill the process
   kill -9 `ps -aef | grep 'mythwelcome' | grep -v grep | awk '{print $2}'`
fi


#start frontend
`mythfrontend --service &`


```

---

### Post by uncle hammy on 2009-11-05
Here's my script.  Note, this actually restarts the frontend (kills it, then relaunches it).  Though you could exclude the very last line to stop the re-launch.  It's named /usr/local/bin/restart_myth.sh
```

#!/bin/sh
MYTHEXISTS=`/bin/ps -e | grep mythfrontend | grep -v grep | awk '{print $1}'`;

if [ "$MYTHEXISTS" != "" ]; then
        for MYTHPROCESS in `/bin/ps -e | grep mythfrontend | grep -v grep | awk '{print $1}'`
        do
                echo $MYTHPROCESS;
                kill -9 $MYTHPROCESS;
        done
fi 

DISPLAY=:0 mythfrontend &

```
My .lircrc file...
```

#Custom lircrc generated via mythbuntu-lirc-generator
#All application specific lircrc files are within ~/.lirc
include ~/.lirc/mythtv 
include ~/.lirc/mplayer 
include ~/.lirc/xine 
include ~/.lirc/vlc 
include ~/.lirc/xmame 
include ~/.lirc/xmess 
include ~/.lirc/totem 
include ~/.lirc/elisa 

#Power Button
begin
remote=mceusb
prog=irexec
button=Power
repeat=0
delay=0
config=/usr/local/bin/restart_myth.sh
end

```
FInally, I have irexec starting at boot by adding an entry to APPLICATIONS>SETTINGS>SESSION AND STARTUP>APPLICATION AUTOSTART that runs the command 
```
/usr/bin/irexec -d ~/.lircrc
```

---

### Post by laffinet on 2009-11-05
I am using this script:

```
#!/bin/sh
# Script to start/stop MythTV
#

LOG=/var/log/mythtv/mythfrontend.log
MYTH=$(pidof mythfrontend.real)

if [ -z $MYTH ]; then
   echo Starting mythfrontend, remote power ON >> $LOG
   mythfrontend &
   xset s off
   xset -dpms
else
   echo Stopping mythfrontend, remote power OFF >> $LOG
   kill $MYTH
   xset s on
   xset +dpms
fi
```

It checks if mythfrontend is running. If not, it starts it. If it is, it stops it. Pretty much like an on/off toggle switch.

I use the power button on my remote for it:

```
begin
  prog = irexec
  button = power
  config = path_to_script./MythTV
end
```

---

### Post by azmyth on 2009-11-05
PROG=mythfrontend

I think you need to change this to

PROG=mythfrontend.real

Without the .real, your script is getting a not started frontend (0) in if [ $RUNNING -ge 1] so it just fires up another frontend instead of killing the frontend.

---

### Post by gwagchunks on 2009-11-06
Wow! Thanks everyone for taking the time to post up your scripts and advise... I really do appreciate it. :D

I'll give these a go tonight and let you know how I get on.

Thanks again everyone!

---

### Post by prudentius on 2009-11-07
> **laffinet said:**
> I am using this script:

I am happy to hear that it still works for you (see [original]("http://ubuntuforums.org/showthread.php?t=1072905&page=2") def's and some background)

Somehow, with the update to ubuntu 9.10 my irexec stopped working - I can't start it anymore as I get
```
irexec: could not connect to socket
```

My IRTrans server however is running, and I can use my remote in mythtv... Any ideas?

---

### Post by SiHa on 2009-11-07
This is my Mythrestart script:```
#!/bin/bash
#
# Script to restart Mythfrontend when it's hung.
# This should be called from irexec

killall mythfrontend.real
sleep 1
mythfrontend &

```

~/.lirc/irexec```
begin
    remote = lircd.conf
    prog = irexec
    button = Power
    config = sudo /usr/sbin/pm-suspend
    repeat = 0
    delay = 0
end

begin
    remote = lircd.conf
    prog = irexec
    button = Blue
    config = /usr/sbin/Mythrestart
    repeat = 0
    delay = 0
end
```

and /etc/rc.local```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

killall -9 irexec
irexec -d /home/frontend/.lirc/irexec

exit 0

```

The last is a bit of a bodge. Once you've run irexec once, it will auto-start, but doesn't load the lirc config. I couldn't find where it was auto-started (checked in rc*n*.d, don't know where else to look), so I just kill it and restart.

---

### Post by gwagchunks on 2009-11-07
Thanks for the replies everyone. I have tried a couple of the scripts. The killall -r mythfrontend.real seems to do the trick. I noticed a strange thing that happens though. If I run it once, it kills the frontend and starts another fine. If I do it again, it kills the front end and then start 2 frontends. If I run it again it stops the frontends and then starts 4 frontends and so on and so on until the box would eventually crash due to loads of frontends running. I'll keep running through the replies and try each script to see what works best.

---

### Post by laffinet on 2009-11-08
> **prudentius said:**
> I am happy to hear that it still works for you (see [original]("http://ubuntuforums.org/showthread.php?t=1072905&page=2") def's and some background)

Somehow, with the update to ubuntu 9.10 my irexec stopped working - I can't start it anymore as I get
```
irexec: could not connect to socket
```

My IRTrans server however is running, and I can use my remote in mythtv... Any ideas?

I'm still running 9.04. So far I don't really see the benefit of switching to 9.10 (happy to be told otherwise :D), other than lots of work.
Plus I see too many posts that report problems wiht 8.10, so I guess I wait until I somehow change my mind and think 9.10 (and 0.22) is a step forward.

---

