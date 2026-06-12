---
title: "irexec running duplacates"
date: 2010-01-19
forum: Mythbuntu
---

### Post by nrune on 2010-01-19
I am trying to run boxee along side mythtv 0.22 so I am using irexec to run two scripts. The problem is that irexec runs the script twice, which hangs boxee and runs two mythfrontends. 

.lircrc
```
begin
    prog = irexec
    button = Clear
    config = start-mythtv
end

begin
    prog = irexec
    button = Enter
    config = start-boxee
end


```

start-mythtv
```
#!/bin/sh

# see if boxee is running
if ps ax | grep -v grep | grep Boxee > /dev/null
then
    #I prefer to manually exit the app it is safer
    #If you do too then uncomment the bottom line
    # echo "Boxee end is running, please exit it first..." > /dev/null
    #and comment out the lines marked with "#<---this"

    #if it is kill it and start mythfrontend
    echo "Killing boxee..." > /dev/null    #<---this
    pkill Boxee                                   #<---this
    `/usr/bin/mythfrontend &`              #<---this
else
    #if not check if mythfrontend is running
    if ps ax | grep -v grep | grep mythfrontend.real > /dev/null
    then
        echo "Mythfrontend already running..." > /dev/null
    else
        # if not running start it up
        `/usr/bin/mythfrontend &`
    fi
fi


```

Start boxee
```
#!/bin/sh

# see if mythfrontend is running
if ps ax | grep -v grep | grep mythfrontend.real > /dev/null
then
    #I prefer to manually exit the app it is safer
    #If you do too then uncomment the bottom line
    # echo "Mythfront end is running, please exit it first..." > /dev/null
    #and comment out the lines marked with "#<---this"

    #if it is kill it and start boxee
    echo "Killing mythfrontend..." > /dev/null    #<---this
    pkill mythfrontend                                   #<---this
    `/opt/boxee/run-boxee-desktop &`             #<---this
else
    #if not check if boxee is running
    if ps ax | grep -v grep | grep Boxee > /dev/null
    then
        echo "Boxee already running..." > /dev/null
    else
        # if not running start it up
        `/opt/boxee/run-boxee-desktop &`
    fi
fi

```

So irexec is running each script twice per button press.  Any way to fix this?

---

### Post by laceration on 2010-01-20
Remote signals are repeating, that is probably your problem.
put 
    repeat = 0
    delay = 0
within each .lircrc block.  I have had similar problems, but haven't messed around with the delay value.  It might be a good idea to put 1 there.

---

### Post by nrune on 2010-01-20
Adding the repeat and delay fixed the mythtv script, but the start boxee script is still running twioc with two copies of the program running. I increased the delay to no effect, start-boxee still runs twice. 

Thanks for your help.

---

### Post by SiHa on 2010-01-20
Have you got two instances of irexec running?

> ps -A|grep irexec

Have you though about adding Boxee to the menu? It's very simple, and Boxee just opens up over Mythfrontend. When you exit Boxee, your frontend is back.

I used these two threads: [[COLOR="Blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1336974&highlight=boxee+menu) and [[COLOR="blue"]_here_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1336974&highlight=boxee+menu).

And added
```
<button>
<type>TV_WATCH_RECORDINGS</type>
<text>Launch Boxee</text>
<action>EXEC /opt/boxee/run-boxee-desktop</action>
</button>

```
To /usr/share/mythtv/themes/defaultmenu/library.xml, then copied the file to ~/.mythtv/

Mind you, I only really wanted Boxee for BBC iPlayer, but then realised how much better looking other media centres were than Myth.

So now I use xbmc (with iPlayerV2 plugin) for iPlayer, Music and Videos, and Mythtv for LiveTV / recording. Even my wife said "ooh, that looks nice!" (She's never really liked Myth)

---

### Post by nrune on 2010-01-20
I suppose that is what I am going to have to do as I can not get it to work right with irexec. 

Thanks

---

### Post by laceration on 2010-01-20
Your remote blasts a signal, and even though the program is instructed not to repeat the signal, it interprets multiple signals within microseconds.  A simple solution may be to weaken the ir signal by not  pointing the remote directly at the ir receiver or place it further away. Another way to try would be putting some like this in your script:
```

if [ -z $(cat startingprogam) ]
then
echo 1 > startingprogam
else
exit
fi

#at the end of the script
sleep 1
: > startingprogam

```
of course this would have to execute before the ir signal repeats, so it might not work.  Also, your script would be more concise if you used pgrep.

---

### Post by indulis on 2010-02-06
LIRC is supposed to stop this "doubling up" of signals by the DELAY and REPEAT stanzas, but it does not work with irexec for some reason.  What a pain- just wasted a couple of hours on finding this out :-(

---

