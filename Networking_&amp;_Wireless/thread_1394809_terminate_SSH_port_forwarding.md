---
title: "terminate SSH port forwarding"
date: 2010-01-31
forum: Networking &amp; Wireless
---

### Post by nunojpg on 2010-01-31
I have a script to establish a reverse tunnel with other machine, like:

```
#!/bin/sh /etc/rc.common

cmd="ssh -N -R *:3005:127.0.0.1:3010 user@hostname"
retrydelay="10"
{                                                                                   
   while true
   do
	eval "$cmd"
	sleep $retrydelay
   done
} &
echo $! >> /tmp/run/sshtunnel.pids
```

My problem is to stop the tunnel. If I just kill the PID at sshtunnel.pids, ssh does not release the ports at the server side, so any new connection will fail for several minutes.

Is there any way to signal SSH to exit gracefully?

Regards,
Nuno

---

### Post by Lars Noodén on 2010-01-31
> **nunojpg said:**
> If I just kill the PID at sshtunnel.pids, ssh does not release the ports at the server side, so any new connection will fail for several minutes.

Is there any way to signal SSH to exit gracefully?


You probably could use [trap](http://www.shelldorado.com/goodcoding/tempfiles.html) to jump to a cleanup subroutine upon receiving one of the signals, such as HUP or EXIT.

To do that, make a routine that does the cleanup you want, then use trap in your script to use that routine.  AFAIK the routine can be in your script.

```

#!/bin/sh /etc/rc.common

we_are_done_for_now () {
  /bin/rm -f /tmp/run/sshtunnel.pids
}

trap "we_are_done_for_now" 0 1 2 3 15

cmd="ssh -N -R *:3005:127.0.0.1:3010 user@hostname"
retrydelay="10"
{                                                                                   
   while true
   do
	eval "$cmd"
	sleep $retrydelay
   done
} &
echo $! >> /tmp/run/sshtunnel.pids


```

I haven't tested the above.  However, I've done things exactly like it with perl scripts, so getting it to work in shell scripts is just a matter of tweaking.

---

### Post by nunojpg on 2010-01-31
That's not the question exactally. I would like to know how to signal that to ssh, on the process that is called in 'eval "$cmd"'.

Regard

---

### Post by Lars Noodén on 2010-01-31
> **nunojpg said:**
> I would like to know how to signal that to ssh, on the process that is called in 'eval "$cmd"'.


eval won't make its own process, $cmd will, using kill or pkill should do what you want.

Using [pkill](http://linux.die.net/man/1/pkill), the **-x** argument means an exact match so that you only kill ssh and not ssh-agent for example.  but if you have more than one instance of ssh for that user, you will kill those too.  For [kill](http://linux.die.net/man/1/kill), you have to know the exact pid for that instance of ssh.

If that process is launched under a unique groupname, it is easier to catch:
```

ps -O 'pid, ppid, user, **group**, command'-w 

```

You can use [sg](http://linux.die.net/man/1/sg) or newgrp to set the group name for the ssh process.  

You can use  [awk](http://www.ibm.com/developerworks/library/l-awk1.html) to grab the pid of the process you wish to kill based on a particular combination of user or group.


```

# show the pid
ps ax o 'pid euser egroup command' \
| awk '$2 ~ /nunojpg/ && $3 ~ /tunnelers/ && $4 == "ssh" {print $1}'


# or just kill it
kill -HUP \
**`**ps ax o 'pid euser egroup command' \
| awk '$2 ~ /nunojpg/ && $3 ~ /tunnelers/ && $4 == "ssh" {print $1}'**`**

```

---

### Post by nunojpg on 2010-02-01
Thanks for the answer.

> eval won't make its own process, $cmd will, using kill or pkill should do what you want.

First of all, what do you mean with this? Eval and $cmd will do the same except for variable expansion, I think...

About the original problem: 

After a really stupid long attempt, I managed to do it.

I used a trap, but the first step is to put ssh running in the background, otherwise it will block any trap for being evaluated.

That is achieved just by adding "& wait"

```
eval "$cmd" & wait
```

Then I could easily trap to kill $(jobs -p).

Regards

---

### Post by nunojpg on 2010-02-11
Actually things were not working.

When using newgrp I have to specify by myself a group name? So if I have a random number of process starting in parallel, will I need to first create a group for each?
Isn't possible to just tell "put this on a unused group please!"?

Thanks,
Nuno

---

