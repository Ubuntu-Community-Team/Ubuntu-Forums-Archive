---
title: "[SOLVED] Start mythtv with home button mce-remote"
date: 2008-03-16
forum: Mythbuntu
---

### Post by Awperator on 2008-03-16
Nevermind please delete. I think I found the problem. Going to try it now.

I was editing the wrong lircrc.
I need to edit /home/user/.lircrc, not /home/user/.mythtv/lircrc
***************************************************************
Hello.

I just need one more thing to work correctly before my system is functional. All I want to do is have the green 'Home' button start mythtv. I am trying to do that with irexec.
I went to my home directory, went to my .mythtv folder, and then from there added this code to lircrc
```

begin
    prog = irexec
    button = Home
    config = mythfrontend --service
end

```

irw lists the home button as 'Home'

I have the mceusb remote. I cannot get this to work. I don't even think irexec is running (I check by going to the system monitor and listing all processes and dependencies.)

Even if I go to the terminal and I run irexec, the home button does not launch mythtv.

Please help me. Thank you for your time.

---

### Post by superm1 on 2008-03-16
FWIW, this behavior has changed for Hardy.  All config files live in ~/.lirc from now on.

---

### Post by rothgar on 2009-10-31
I know this thread is really old but it didn't seem right to open a whole new thread for the same issue. I have a StreamZap remote and would like to do the same thing with the RED button. I have verified that the RED button does register as "RED" with irw but whenever I push red nothing happens.
Has this changed since this thread was originally posted?

Everything else opens just fine. Maybe I am just putting this config in the wrong file.

Please let me know if there is a different way to get this working now with Mythbuntu 9.10.

Thanks

---

### Post by superm1 on 2009-10-31
Same thing as before.  If you run mythbuntu-lirc-generator, it will generate a bunch of stuff in ~/.lircrc and ~/.lirc/*

Find the file in ~/.lirc/ corresponding to the app your are wanting to set.  See if your button is mentioned there.  If it's not, add another block for your button.

---

### Post by rothgar on 2009-10-31
Thanks for the help superm1 (you have helped me a lot in the past). I got it figured out and it wasn't exactly intuitive. The reason it wasn't launching for me is because irexec wasn't running (and isn't set to autostart). I had to go to the settings -> sessions and add the program to run at startup "irexec" without quotes is all I used.
Now when the computer turns on irexec starts in the background and pushing the RED button starts "mythfrontend --service"
This is just in case the frontend crashes or I am doing something else and need a quick way to start it.

The only problem with this setup is it would be possible to start 2 or more frontends at the same time. To stop that from happening you will need to create a script and have irexec run the script instead of mythfrontend directly.

Here is the script I found which should be able to do this.
```

#!/bin/bash
PROG=mythfrontend
STATUS=`ps -e | grep $PROG | grep -v grep | wc -l | awk '{print $1}'`

if [ `echo $DISPLAY | grep -c ":0"` -ge 1 ]
then
    if [ $STATUS -eq 0 ]
    then
        ( $PROG & )
    fi
fi
exit 0
```

This script didn't work exactly for me but it is a good start. I modified it to just be

```

#!/bin/bash
PROG=mythfrontend
STATUS=`ps -e | grep $PROG | grep -v grep | wc -l | awk '{print $1}'`

if [ $STATUS ]
    then
        ( $PROG --service & )
fi
exit 0
```

Now save that in /usr/local/bin and give it execute permissions.

If you are just trying to get the frontend to restart if it crashes you should check out this thread in the mailing list too. [http://www.mail-archive.com/mythtv-users@mythtv.org/msg01917.html](http://www.mail-archive.com/mythtv-users@mythtv.org/msg01917.html)


I hope this helps someone in the future.

---

### Post by superm1 on 2009-10-31
Actually for 9.10+ it shouldn't be possible to start two mythfrontends.  The second invokation is supposed to just bring the window on top using wmctrl.

---

### Post by stonebit on 2009-12-24
I'm using mythbuntu 9.10. I have put irexec in the sessions startup. The script is not working. It's weird though. I can run the script and call just mythfrontend with Alt-F2, but pushing the button doesn't do anything. Any ideas?

>edit:

In settings > sessions, the command 'irexec -d /home/[user]/.lircrc' has to be added... not just 'irexec'.
Also, the button press action for irexec needs to be in ~/.lircrc (just to clairfy).
And last: on the 'config =' line, make it 'config = mythfrontend &'. A script is not necessary. The & lets irexec accept other commands instead of waiting for the command to exit, which i think would prevent myth from receiving commands. This further allows you to add a power button reset command for the pc or a suspend / resume script which will resume with myth running.

---

### Post by orduek on 2009-12-27
I'm a bit confused.
I want to add a button that allows me to kill mythfronend and restart it.
I made a script :
something like that:
killall mythfrontend

mythfrontend.

but, when I'm in mythtv - pressing the button doesn't kill it. it seems the irexec is waiting for mythfrontend to close before processing the rest of the orders.
how can I fix it?

---

### Post by nickrout on 2009-12-27
> **orduek said:**
> I'm a bit confused.
I want to add a button that allows me to kill mythfronend and restart it.
I made a script :
something like that:
killall mythfrontend

mythfrontend.

but, when I'm in mythtv - pressing the button doesn't kill it. it seems the irexec is waiting for mythfrontend to close before processing the rest of the orders.
how can I fix it?

if you look at the output of ps ax you will see there is no mythfrontend to kill. It is mythfrontend.real you need to kill.

---

### Post by orduek on 2009-12-27
> **nickrout said:**
> if you look at the output of ps ax you will see there is no mythfrontend to kill. It is mythfrontend.real you need to kill.

oh, sorry - I said killall mythfrontend but actually my script says killall mythfrontend.real.
that wasn't the problem.
I put it in /home/user/.lirc/mythtv - but when mythfrontend is up the script is not responding.

---

### Post by nickrout on 2009-12-27
> **orduek said:**
> oh, sorry - I said killall mythfrontend but actually my script says killall mythfrontend.real.
that wasn't the problem.
I put it in /home/user/.lirc/mythtv - but when mythfrontend is up the script is not responding.

try the full path in the script like /usr/bin/killall mythfrontend.real

also try /usr/bin/killall -9 mythfrontend.real

---

### Post by orduek on 2009-12-28
the full path is there.
I'll try the -9 (what is it?).
Although I think the problem is that when I put the specific button configuration in ~/.lirc/mythtv I can start mythfrontend but not kill it - it just doesn't do what I press as long as I'm in mythtv (like the irexec is waiting for mythfrontend to close before listening to the remote again).
So I need to make it higher priority or either, put this configuration in another file or something?

---

### Post by nickrout on 2009-12-28
how about you pot EXACTLY what you put in the lirc setup?

---

### Post by orduek on 2009-12-28
you right.
```

begin
prog = irexec
button = Red
config = /home/username/restartmyth.sh
end


```

---

### Post by nickrout on 2009-12-28
and what is in ```
/home/username/restartmyth.sh
```?

---

### Post by orduek on 2009-12-28
sorry.
```

#!/bin/sh
killall mythfrontend.real
mythfrontend

```

---

### Post by orduek on 2009-12-29
using another thread here I was able to solve my problem.
thank you very much for your help.

---

### Post by Nausser on 2010-06-09
What other thread?

Please post the link.

Thanks.

---

### Post by Nausser on 2010-09-08
*bump*

---

