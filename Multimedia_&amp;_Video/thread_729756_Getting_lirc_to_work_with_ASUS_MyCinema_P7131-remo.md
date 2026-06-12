---
title: "Getting lirc to work with ASUS MyCinema P7131-remote??"
date: 2008-03-20
forum: Multimedia &amp; Video
---

### Post by doubledouce on 2008-03-20
Hi!

I'm setting up a freevo system to use with my TV. Everything is working, but I'm having a really hard time with the remote. I've google'd and searched for many, many, maaaany hours now, but I can't find a solution.

The driver for the card is listed when I "lsmod" so it seems to be working. I've looked at the remote using my camera and I can see the ir-light so the remote is working too. I also have "lirc_serial" and "lirc_dev" started. But if I try to test the remote using "sudo irrecord -d /dev/lirc0 /tmp/my_remote" it doesn't register any signals and end up saying 
"irrecord: no data for 10 secs, aborting
irrecord: gap not found, can't continue"

It's driving me crasy not being able to get this up and running. :(

Have anyone here successfully managed to use the remote that comes with the ASUS MyCinema P7131?? And could you please post how you did it?? :)

---

### Post by bve on 2008-05-18
copied to [http://ubuntuforums.org/showthread.php?p=4986557#post4986557](http://ubuntuforums.org/showthread.php?p=4986557#post4986557) since this is an archived forum.

I'm in the same boat with the ASUS MyCinema P7131 remote.

What I am finding is lirc doesn't like the code for the enter button.

When I try irw it just dies with no output and lircd crashes, I know this because /etc/init.d/lirc restart fails when stopping.
```

burke@orion:~$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s):LIRC [fail] 
 * Loading LIRC modules [ OK ] 
 * Starting remote control daemon(s) :LIRC [ OK ] 
burke@orion:~$ 

```

This shows up in the syslog
```

May 17 20:36:56 orion lircd-0.8.3pre1[7400]: invalid code found for lirc.conf: Enter
May 17 20:36:56 orion lircd-0.8.3pre1[7401]: lircd(userspace) ready
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: accepted new client on /dev/lircd
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: initializing '/dev/lirc0'
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: unable to open '/dev/lirc0'
May 17 20:39:51 orion lircd-0.8.3pre1[7401]: caught signal

```

The enter code in the config file is:
```

Enter                    0x8001001C

```

Anyone know what it should be? For now I have just removed it to test,  I still need to deal with the below error.

Also there is obviously a problem with my /dev/lirc0 - it doesn't exist
```

May 17 21:53:20 orion lircd-0.8.3pre1[5306]: accepted new client on /dev/lircd
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: initializing '/dev/lirc0'
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: unable to open '/dev/lirc0'
May 17 21:53:20 orion lircd-0.8.3pre1[5306]: caught signal

```

Any help is appreciated.

Thanks in advance
Burke

---

### Post by bve on 2008-06-15
to the OP visit the thread here for a solution [http://ubuntuforums.org/showthread.php?p=4986557#post4986557](http://ubuntuforums.org/showthread.php?p=4986557#post4986557)

---

