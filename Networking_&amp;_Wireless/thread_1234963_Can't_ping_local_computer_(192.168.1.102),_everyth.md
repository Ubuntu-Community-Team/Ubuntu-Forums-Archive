---
title: "Can't ping local computer (192.168.1.102), everything else fine"
date: 2009-08-08
forum: Networking &amp; Wireless
---

### Post by altonbr on 2009-08-08
I've got something for you networking-heads...

I've got two computers that are perfectly connected to the Internet via a cable modem and router where they both access the Internet fine.

But that can't talk to each other.

Now I'm sure it's my desktop (.100) that is the issue and not my server (.102) because when I shut my desktop down, pings temporarily work.

It's as if something is dropping the connections, but I can't figure out what it is nor do I know where to check.

I uninstalled all suspicious software that might be doing it and after a reboot they still can't talk.

Where can I look?? Please help! :D

---

### Post by khelben1979 on 2009-08-08
Check your settings in the router. Maybe you need to open up some ports?

What is the brand of the router?

---

### Post by T-Train on 2009-08-08
Sorry for the obvious questions.  I would assume this is a firewall issue.

Are both running Ubuntu?

Can you ping the gw and an external address?

---

### Post by Charlietje on 2009-08-08
I agree... Seems firewall issue.

What do you mean by that?
> Now I'm sure it's my desktop (.100) that is the issue and not my server (.102) because when I shut my desktop down, pings temporarily work.

Your question is *Can't ping local computer (192.168.1.102)*
But if you shut down your desktop (.100) ping work?
From where are you pinging when your desktop is shut down?
Do you mean, when your desktop is on, you can't ping your server.
When your desktop is off, you can ping your server...

Regards,
Carl

---

### Post by altonbr on 2009-08-08
> **khelben1979 said:**
> Check your settings in the router. Maybe you need to open up some ports?

What is the brand of the router?

I've reset my router to factory settings and I've been able to ping it before, so I don't think it's the router. I'll explain why in a sec.

> **T-Train said:**
> Sorry for the obvious questions.  I would assume this is a firewall issue.

Are both running Ubuntu?

Can you ping the gw and an external address?

They are both running Ubuntu, yes.

I can ping 192.168.1.1 and google.ca, yes.

> **Charlietje said:**
> I agree... Seems firewall issue.

What do you mean by that?


Your question is *Can't ping local computer (192.168.1.102)*
But if you shut down your desktop (.100) ping work?
From where are you pinging when your desktop is shut down?
Do you mean, when your desktop is on, you can't ping your server.
When your desktop is off, you can ping your server...

Regards,
Carl

I mean when I ping from .102 to .100, the pings don't go through... but as soon as I shut down .100, the pings work temporarily. This means to me that a program is running that is stopping the pings from going through. In fact, I usually ssh to .102 (server) from .100 (desktop) and I tried it both ways and they just can't talk to each other.

I'm pretty good with computers and I don't screw around too much with my installations (I have another installation called Karmic for that ;)) so I don't think it's anything I've installed or done... but it could be.

This is the results of my log from .100 (desktop) looking for instances of '192.168.1.102'

```
$ sudo grep -ri '192.168.1.102' /var/log/
/var/log/auth.log:Aug  8 14:56:04 van-gogh sudo:    brett : TTY=pts/0 ; PWD=/home/brett ; USER=root ; COMMAND=/bin/grep -ri 192.168.1.102 /var
/var/log/auth.log:Aug  8 14:56:13 van-gogh sudo:    brett : TTY=pts/0 ; PWD=/home/brett ; USER=root ; COMMAND=/bin/grep -ri 192.168.1.102 /var/log/
/var/log/ConsoleKit/history:1245097586.312 type=SEAT_SESSION_ADDED : seat-id='Seat4' session-id='Session401' session-type='' session-x11-display='' session-x11-display-device='' session-display-device='/dev/ssh' session-remote-host-name='192.168.1.102' session-is-local=FALSE session-unix-user=1000 session-creation-time='2009-06-15T20:26:26.145615Z'
/var/log/ConsoleKit/history:1245099056.361 type=SEAT_SESSION_REMOVED : seat-id='Seat4' session-id='Session401' session-type='' session-x11-display='' session-x11-display-device='' session-display-device='/dev/ssh' session-remote-host-name='192.168.1.102' session-is-local=FALSE session-unix-user=1000 session-creation-time='2009-06-15T20:26:26.145615Z'

```

---

### Post by Charlietje on 2009-08-09
what is the result of
```
sudo ufw status
```

if it is enabled, try
```
sudo ufw disable
```
and try your ping again


regards
Carl

---

