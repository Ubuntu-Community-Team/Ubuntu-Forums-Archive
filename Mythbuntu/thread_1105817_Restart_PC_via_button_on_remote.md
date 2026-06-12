---
title: "Restart PC via button on remote"
date: 2009-03-25
forum: Mythbuntu
---

### Post by laffinet on 2009-03-25
I'm trying to assign a button on my remote to restart my machine.

I've created a small script which contains the following:

```
#!/bin/bash
#
#restart computer
#
sudo reboot
```

My lirc contains the following:

```
begin
prog = irexec
button = red
config = /home/laffi/restart
end
```

and I've added the following line(s) via

sudo visudo
```
%mythtv ALL = NOPASSWD:  /home/laffi/restart
%laffi ALL = NOPASSWD: /home/laffi/restart

```

(wasn't sure for which user, hence I added for mythtv and laffi)

Problem is that the script gets called alright but still asks for a password. Why ? What am I missing ? 

Thanks.

---

### Post by Kytsi on 2009-03-25
> **laffinet said:**
> I'm trying to assign a button on my remote to restart my machine.

I've created a small script which contains the following:

```
#!/bin/bash
#
#restart computer
#
sudo reboot
```

My lirc contains the following:

```
begin
prog = irexec
button = red
config = /home/laffi/restart
end
```

and I've added the following line(s) via

sudo visudo
```
%mythtv ALL = NOPASSWD:  /home/laffi/restart
%laffi ALL = NOPASSWD: /home/laffi/restart

```

(wasn't sure for which user, hence I added for mythtv and laffi)

Problem is that the script gets called alright but still asks for a password. Why ? What am I missing ? 

Thanks.

You should set NOPASSWD option for /sbin/reboot instead of your own script

You are now setting NOPASSWD options for groups mythtv and laffi
I think that user laffi belongs to mythtv group so it should be enought to give NOPASSWD option for mythtv group.

visudo:
```
%mythtv ALL = NOPASSWD:  /sbin/reboot

```

---

### Post by laffinet on 2009-03-26
Thanks, setting NOPASSWD for /sbin/reboot worked, but why didn't it work for my script ?

---

### Post by Kytsi on 2009-03-26
I think that after you added NOPASSWD, your script should work without asking password.

If you add NOPASSWD option to your script, it means that you don't need password to execute script, but passwords are still required for commands inside script.

---

### Post by azmyth on 2009-03-26
May want to take a look at irwatch.pl. You can program a sequence of buttons to reboot like red, red, blue, red. With just red, you may have accidental reboots.

---

### Post by liquidox on 2009-10-28
> **azmyth said:**
> May want to take a look at irwatch.pl. You can program a sequence of buttons to reboot like red, red, blue, red. With just red, you may have accidental reboots.
  I'd love to use the irwatch script but the official download seems to be offline ([http://www.ronfrazier.net/mythtv/irwatch.pl.tar](http://www.ronfrazier.net/mythtv/irwatch.pl.tar))
  
  Can anyone help me out? Or is there something else people use nowadays?
 
 Thanks!

---

### Post by laffinet on 2009-10-28
I'm still using my little script, works fine and I never had problems with accidental reboots.

---

### Post by azmyth on 2009-10-28
The thing I like about irwatch is you can assign a series of keys to perform a task. If it's just one person than you don't have to worry about hitting the red button but in a multi-use situation if someone hits the red button then you could end up with a reboot at a bad time. You can also assign the replay button to skip back 40 seconds. Possibilities are unlimited. I guess it all depends on the situation.

Send me an IM with your email and I'll send you my copy of irwatch.pl

---

