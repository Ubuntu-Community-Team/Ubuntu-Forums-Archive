---
title: "telnet via ssh on APC UPS"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by decoherence on 2011-01-12
I have some APC UPS devices that I'm trying to log in to. They are currently configured to use telnet -- as a safety precaution, they can only be accessed from our 'bounce' machine. So because I want to do this from a script, I'm doing it like this

ssh decoherence@bouncemachine telnet stupidAPCdevice

This works fine on all the other devices I'm trying this on (Cisco gear, mostly) but the APC won't take any input. I get the login prompt but when I type in my username, ssh echoes it but the APC doesn't appear to ever receive it. It just hangs there at the username prompt.

I'm guessing that its telnet implementation is a bit weird (seriously, all the management stuff on APC gear really sucks but anyway...)

Anyway, I'm just wondering if there are any simple flags I can pass to telnet to make it cooperate. The man page talks about a 'mode' command that lets you fiddle with LINEMODE which sounds like it might be promising but I don't know how to set that in the command line as opposed to interactively.

Any suggestions?

Thanks!

---

### Post by decoherence on 2011-01-13
Ah ha! SSH needed the -t option!


     -t      Force pseudo-tty allocation.  This can be used to execute
             arbitrary screen-based programs on a remote machine, which
             can be very useful, e.g. when implementing menu services.
             Multiple -t options force tty allocation, even if ssh has
             no local tty.

Now it works!

---

