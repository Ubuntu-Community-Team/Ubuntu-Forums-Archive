---
title: "mythfrontend_restart -- a script to restart the frontend when button is pressed"
date: 2008-04-25
forum: Mythbuntu
---

### Post by grytpype on 2008-04-25
Hello all... I was just fiddling around with my MCE remote and I came up with this little script to restart mythfrontend when the PC Power button is pressed.  I'm sure you could modify it to suit your own needs.  Hope people find it useful!

```
!/bin/sh
#
# mythfrontend_restart
# by grytpype on mythbuntu forums
#
# Monitors keypresses from the MCE remote control
# Restarts mythfrontend when PC Power button is pressed
#

while true; do
    irw | grep -m 1 Power
    /etc/init.d/gdm restart
    sleep 5
done

```

---

### Post by laga on 2008-04-25
Hello,

that script sounds useful! However, it might be a bit more efficient to use irexec to execute a script instead of polling irw every 5s. Of course, irexec needs be run as root if you want to restart gdm. I've got a script which will restart the Frontend for me, but it's on a different computer so I'll have to post it later.

---

### Post by Nikas on 2008-04-25
I have this in my lircrc-file:

#       Go
##      Start frontend with remote control.
begin
prog = irexec
button = GO
config = DISPLAY=:0 mythfrontend &
end

So, in case of crash or something like that... my "Go/Home"-button starts the frontend again. :)

---

### Post by grytpype on 2008-04-25
> **laga said:**
> Hello,

that script sounds useful! However, it might be a bit more efficient to use irexec to execute a script instead of polling irw every 5s. Of course, irexec needs be run as root if you want to restart gdm. I've got a script which will restart the Frontend for me, but it's on a different computer so I'll have to post it later.

Thanks for the comments!

If I understand how my script is working, irw is not being polled every five seconds.  Rather, it is listening to the LIRC socket and piping its output to grep.  When grep sees the "Power" button output from irw, it exits and the script proceeds to the next line, which restarts the X server.  The "sleep 5" is there just so I don't have an infinite loop that could potentially take all the CPU if something goes wrong.

I didn't know about irexec when I wrote the script, that looks like a good method as well

---

### Post by laga on 2008-04-25
> **grytpype said:**
> Thanks for the comments!

If I understand how my script is working, irw is not being polled every five seconds.  Rather, it is listening to the LIRC socket and piping its output to grep.  When grep sees the "Power" button output from irw, it exits and the script proceeds to the next line, which restarts the X server. 

Doh! You're right! Sorry for the confusion :)

---

### Post by bergersau on 2010-05-06
Thanks grytpype,

Excellent script.

All I had to do to get it to work for me was change the first line to
```
#! /bin/bash 
```

and chmod +x it.

:biggrin:

---

