---
title: "Working firestarter with moblock (blockcontrol)"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by excel28 on 2009-05-06
I finally have a valid setup where I have a IP blocker and firewall.  I installed firestarter and blockcontrol.  I tried to use guarddog but I could not verify that my setup was working correctly.

Anyways... installed normally, and everything is good.  But if I restart (or stop and start) firestarter, I want to make sure blockcontrol is still valid, so I always had to issue the command in a terminal.  But now, I don't have to.

Edit /etc/firestarter/firestarter.sh with your editor, then find the function start_firewall() and add the lines that are marked with ">"...

```
start_firewall () {
	lock_firestarter
	source /etc/firestarter/firewall 2>&1
	retval=$?
	if [ $retval -eq 0 ]; then
		echo "Firewall started"
>		if [ -x /etc/init.d/blockcontrol ]; then
>			/etc/init.d/blockcontrol restart
>		fi;
	else
		echo "Firewall not started"
		unlock_firestarter
	exit $retval
fi
}

```

---

### Post by jre on 2009-05-07
Nice. (But I think I've read that firestarter is deprecated and ufw should be used instead.)

Anyway, that part might be improved by using this code:
```
if [ -x /usr/bin/blockcontrol ] ; then
        blockcontrol status > /dev/null
        [ "$?" -eq 0 ] && blockcontrol restart
fi
```

So I use blockcontrol directly, not the init file (the init file first checks some stuff and afterwards simply executes blockcontrol with the argument, so we save some steps here).
Further I check if blockcontrol is currently running with status. If yes, then the return code is 0 and I do the restart. This allows to keep blockcontrol stopped manually.

Anybody using ufw to check where the code should be placed there?

BTW, since blockcontrol 1.4 there's a watchdog which checks every 5 minutes if some iptables rules are still present and the daemon is responsive. Otherwise it also restarts blockcontrol. But that's just a workaround in blockcontrol, while the correct solution is as you did it in the "other" application that messes up blockcontrol's iptables rules.

---

### Post by meganox on 2009-06-11
Best place to put this code is in /etc/firestarter/user-post - that's what it's for!

Edit: actually you also need to restart moblock when the firewall is stopped, so you have to edit firestarter.sh anyway.

---

### Post by meganox on 2009-06-11
Here's a patch that adds the necessary hooks to firestarter.sh

The commands to restart moblock are in user-post and user-stop.  They are run after firestarter has finished its changes to iptables.  

If you wanted to keep moblock in step with firestarter you could edit user-stop and change "blockcontrol restart" to "blockcontrol stop".  

There's also a user-status file as well which causes moblock to report its status after firestarter if you run ./firestarter.sh status.  

To apply the patch copy it to /etc/firestarter and cd to that directory, then run
```
 # sudo patch -p2 < fs-moblock.patch.txt
```

---

