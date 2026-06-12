---
title: "Running remote programs for a long time"
date: 2010-03-14
forum: Networking &amp; Wireless
---

### Post by Choragos on 2010-03-14
Hello.  I suspect this has been posted before, but I'm new enough to the OS to lack the proper vocab for a proper search.

In any case, I'm basically trying to run programs remotely at work (from home) that will run for a long time.  I first ssh into the appropriate network, then ssh into the individual machine.  This works great and I can run programs no problem.  The issue is that these programs can run for days or weeks, and the network kicks me out after some period of time due to inactivity.

Is there a way to start a program on a remote machine then terminate the connection but have it keep running?

Thanks a bunch.

---

### Post by reyals140 on 2010-03-14
[http://wiki.linuxquestions.org/wiki/Using_SSH](http://wiki.linuxquestions.org/wiki/Using_SSH)

Last section

It's what I do.

---

### Post by Choragos on 2010-03-14
Brilliant.  Thanks.

---

### Post by Choragos on 2010-03-14
Oops, I spoke too soon.  The wiki suggested I use the "screen" command, but that was unrecognized by the system.  However, I'm not using putty, I'm just ssh-ing from the terminal.  Any thoughts?
Thanks!

---

### Post by reyals140 on 2010-03-14
Well it's a linux command not putty so

sudo apt-get install screen

ought to fix you up since it sounds like it's not installed

---

### Post by jiggz88 on 2010-03-14
Two ways you could do this, screen or console return(aka '&'). If you do the screen method, you can come back to it and view its progress, if you use the console return method, you lose all output unless you pipe it to a file or recording device.

Normally screen works fine and is your main thing to do but if your really not that concerned with viewing the output at any given moment live, then you could do the console return.

screen
> 
 $ screen -d -R [COLOR="Red"]-screen name-[/COLOR] -t [COLOR="Red"]-Title bar text-[/COLOR]
 $ [COLOR="Red"]-command-[/COLOR]
ctrl+A ctrl+D to exit screen

console command return
> 
 $ [COLOR="Red"]-command-[/COLOR] > [COLOR="Red"]-path to logfile-[/COLOR] 2> [COLOR="Red"]-path to errorfile-[/COLOR] &


---

### Post by Choragos on 2010-03-14
<------- idiot.  Of course I need to install it.

Thanks!

---

