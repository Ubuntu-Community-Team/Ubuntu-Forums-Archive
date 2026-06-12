---
title: "MythTV: Auto shutdown/Wakeup"
date: 2007-02-05
forum: Multimedia &amp; Video
---

### Post by sstakes1 on 2007-02-05
I have Ubuntu Edgy system with Nvidia NF325-A7 Motherboard, GeForce 5200FX AGP 8X video card and KWorld ATSC-110 ATSC tuner. All of it is working fine.

However, I am not able to setup the automatic shutdown and wakeup of the myth system. I have verified that the acpi wakeup works independently by setting the time into /proc/acpi/alarm. The RTC clock is set to UTC.

In my mythtv-setup Shutdown/Wakeup Options page I have the following settings

Startup Command:
Block shutdown before client connected: Unchecked
Idle timeout (s) : 60
Max Wait for Recording (min) 5
Startup before recording (s) 180
Wakeup time format(s) 180
Set wakeuptime command: sudo /home/mytthtv/scripts/setwakeup_time.sh $time
Server halt command: /sbin/halt -p
Preshutdown check command: /home/mytthtv/scripts/preshutdown_check

The wakeuptime and preshutdown scripts are attached.

[ATTACH]24611[/ATTACH]

[ATTACH]24612[/ATTACH]

Any ideas going forward will be greatly appreciated.

Thanks.
):P

---

### Post by sstakes1 on 2007-02-06
And I must add that these scripts never seem to be called. I replaced them with simple ones that echo a timestamp to a file and no such files are created.

Thanks

---

### Post by sstakes1 on 2007-02-06
I'm sure there's someone who can help me. It looks like my scripts is not being called. I do not know why

---

### Post by Prefader on 2007-02-06
I was planning on setting this up on my myth box as well - just out of curiosity, what happens if you yank the "sudo" from the "set wakeup time command"?  I'm guessing that it's failing when it doesn't get authenticated (waiting for a password, perhaps).

---

### Post by sstakes1 on 2007-02-07
I had it without the sudo first. Then added it and also amended the /etc/sudoers to have NOPASSWD for these commands for mythtv user. I do not know what is happening. Is there any logs I can look at for backend shutdown?

---

### Post by sstakes1 on 2007-02-09
Okay. I figured it out. /var/logs/auth.log showed authentication failures for mythtv sudo. It was due to the fact I had misspelled mythtv in /etc/sudoers. The scripts are getting called.

---

### Post by friesgaard on 2007-02-25
Somehow I do not have access to your scripts, could you make 'em available somewhere else?? ... or perhaps email 'em to me: friesgaard _at_ hotmail _dot_ com

Regards,
Morten

---

### Post by majoridiot on 2007-02-27
a complete wake-up/shutdown "how-to" should be posted to our ubuntu mythtv guides very 
soon... including set-up options and the associated scripts and changes to existing scripts.

the link will be posted here when it is available. :D

---

### Post by Dubstar_04 on 2007-02-27
I can't wait for the how to. I've been having problems with it. I can get my pc to shutdown using a sleep command in terminal and auto boot using acpi, but when it boots it hangs on the splash screen and crashes. When I try and shut down using the GUI it will not boot at all!!

The how to will be very very welcomed.

---

### Post by majoridiot on 2007-03-01
the first draft of the guide is posted-

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

at the moment, it covers ACPI wake-up, which works for many boards.  hopefully
someone with nvram-wakeup experience will add to it, to help those that can't get 
ACPI to work.

good luck ! :)

---

### Post by NT4usB on 2007-03-01
> **majoridiot said:**
> the first draft of the guide is posted-

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

at the moment, it covers ACPI wake-up, which works for many boards.  hopefully
someone with nvram-wakeup experience will add to it, to help those that can't get 
ACPI to work.

good luck ! :)

Very well written. 
We'll try it in the coming weeks and see if we can add a couple boards to the list...
Thanks for taking the time.

---

### Post by BatPenguin on 2007-03-26
Hello there,

I'm hoping someone might be able to give me a hand here, I'm frustratingly close to having this work but so far it doesn't. I feel pretty dumb looking at this and not just being able to get the last thing to click, hopefully there's something really obvious I'm missing here.

I've done everything as far as I know according to the how-to, but I'm having problems with getting Myth to call the script to write to /proc/acpi/alarm. The machine wakes up fine if I write a wakeup time to the /proc/acpi/alarm file manually, so that's all good. It's the scripts that are giving me a hard time. My preshutdown script is working fine, I can see the "shutting down in 100 seconds" messages and the whole countdown being reset afterwards. So that's called. However, regardless of what I put in the MythWakeSet script/field, nothing seems to be getting done, looks like that script is not being called OR (more likely), there's a sudo problem here somewhere.

I'm running mythtv as my normal user account (yeah, I guess not the best option, but this is how I've done it and I'd prefer to do it like that) so I set sudoers file (with sudo visudo) to the following:

```

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
risto ALL=NOPASSWD: /sbin/shutdown, /usr/bin/halt, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%risto ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

```

Shouldn't this be working alright? My username is risto. I thought the first line (risto) should do the trick but I also included the same with %risto since, err, it wasn't working =)

So, this all just doesn't seem to work for some reason, could anybody give me a hint here to either a) how to fix it :D or b) if it isn't obvious to anybody else either, can I get a little help on how to set the MythWakeSet script to something really, really generic that I could use to check whether this is a sudo problem or not -- to see whether the script is called at all. I've tried things like echo hello >/home/risto/text.txt etc. but nothing seems to be getting done. If, however, I run the MythWakeSet script manually (with sudo) it does run but of course doesn't write out anything with the $time variable...but I've tested with a time set inside the script, and that seems to work. Myth just isn't calling it. Any ideas? Thanks.

---

### Post by majoridiot on 2007-03-26
> **BatPenguin said:**
> I'm running mythtv as my normal user account (yeah, I guess not the best option, but this is how I've done it and I'd prefer to do it like that) so I set sudoers file (with sudo visudo) to the following:

```

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
risto ALL=NOPASSWD: /sbin/shutdown, /usr/bin/halt, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%risto ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

```

the problem is that you are giving your normal user account the privs to run the scripts, yet it
is **mythtv** that is actually executing the script, not your main user.

your main user *launches* mythtv, but it is mythtv itself that needs the privs- it's kinda 
confusing, so don't feel bad.

change your visudo to mythtv user and that should fix it:

```

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
risto ALL=NOPASSWD: /sbin/shutdown, /usr/bin/halt, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/MythShutdown

```

also, if you haven't already, be sure to add your main user to the mythtv group:

```
# sudo usermod -a -G mythtv risto
```

be sure to add your board to the list when it's working- or PM me and i will.

good luck!

---

### Post by BatPenguin on 2007-03-28
Thank you for the great response! Unfortunately I still didn't get it going yet, same problem even though I made those changes. I'm pretty sure it's still a sudo problem though, your explanation made perfect sense but still not working. 

Anyway, I'm noticing also that even though my machine is going through the MythWakeSet command, it won't shutdown by itself. I had the machine on, logged out myself, and it wasn't turning off...of course not sure it's still callign the script when I'm staring at the login screen, but I assume it is since when I'm logged in it's warning about the shutdown (well, if I start it from the command line, normally I dont see the warning when the daemon is just launched on bootup). So apparently calling shutdown command doesn't work but the script otherwise gets called. My mythtv's backend log doesn't seem to be logging much, the log file is mostly empty. Anything I can do to get it to record more things? That'd probably be useful information.

I tried skipping my own account and using the mythtv user as well, placing those same lines with both "risto" and "mythtv" in the visudo, basically doing it more according to the instructions. But no luck. I really don't get it.

I didn't have much time to look at this yesterday other than try these good suggestions and give the mythtv user a quick spin, but I'll try to do everything from the start and under the mythtv user this weekend. In the mean time, if there's a way to get myth to log more into the files, I'd appreciate hearing that...and of course, other suggestions are more than welcome too naturally).  One thing I was thinking is that I should put a little test script that does something first as a normal user and the as sudo in all those mythtv script fields...then I'd have something to check that it's working. Now if I try doing those "touch /tmp/test.txt" type of things, nothing ever gets done. Any good hints on what would be a super foolproof test to see if the scripts are called? I don't understand why touch or echo "blahblah" > /tmp/text.txt doesn't seem to do anything. I though I checked that both risto and mythtv have rights to the /tmp directory but (at work...yeah, busy busy as you can see :)  can't be absolutely sure now.

Again, thanks for the help -- I really appreciate the quick response. I'll get this going still...oh yes...I will...

---

### Post by majoridiot on 2007-03-28
just out of curiosity... did you make all of those scripts executable?

```
$ sudo chmod +x /usr/bin/MythWakeSet /usr/bin/MythShutdownCheck /usr/bin/MythShutdown 
```

you can add your own test info to the backend log to see where things are getting to... pretty much at any point from
the mythtv-setup page itself to inside the scripts.  the basic format you want is:

```
$ echo 'whatever you want'  >> /var/log/mythtv/mythbackend.log
```

if you do it as a standalone script, make sure to make it executable and that the mythtv
user has privileges.

you can also insert that echo into pretty much any point of the Myth* scripts to test where they get to.

---

### Post by BatPenguin on 2007-03-28
Yes, scripts are executable. I'll try the echo to log tonight...seems like I've been trying the echos a bit different. What I've been doing is:

echo "blah" > "filename"

you had >> instead of >. Is there a difference?

---

### Post by majoridiot on 2007-03-28
echo with a > creates a file or overwrites an existing one (by redirecting standard output), while >> 
appends to the file.  

you want to append to the mythbackend.log to preserve it and to also help troubleshoot, as you can
see where in the log your various echos appear- or don't.

hang with it.  if you got it to shut down manually, then the hardest part really is over.

---

### Post by BatPenguin on 2007-03-28
Yeah, not about to give up now. Seems to be so close. Thanks again for all the help...I'll dig in deeper tonight or when I have the time and try to get this thing going. I'll let you know how it goes...

---

### Post by majoridiot on 2007-03-28
i caught a typo on that page, which may be a problem for you:

```
Server Halt Command*: sudo shutdown -h now
```

should be:

```
sudo shutdown -h -P now
```

to fully power down. 

 simply halting it may or may not do a full powerdown, depending on a lot of factors.  the -P option specifies powerdown.

---

### Post by BatPenguin on 2007-03-28
Alright...did some more testing. This is going to be long post now, I'm trying to include as much information as I can.

OK, so now I'm getting somewhere at least. To me, this looks like / I'm guessing it's caused by something silly I've done in the past, installing or running myth with or without sudo somehow  that I shouldn't have or something like that. So, looks like a permissions issue with my computer, not necessarily a permissions issue with these scripts but some problem with the whole myth setup. Hopefully this is something that could be fixed by changing some permissions and not reinstalling myth etc. I'll explain:

So: my visudo is pretty much what I noted above, with the exception that in my moment of desperation I've put the all the same no password permissions to both the mythtv and risto users. Shouldn't matter, I guess.

I started testing by setting the shutdown check to this (according to the kind recommendation):

```
echo "testing testing" >> /var/log/mythtv/mythbackend.log 
```

and hooray! I'm getting this: 

```

2007-03-28 19:57:19.628 I'm idle now... shutdown will occur in 10 seconds.
sh: /var/log/mythbackend.log: Permission denied

```

I of course treated this with a "ha-ha! no permissions to that log file, let's change it!" but, well, when I checked it, the whole folder is owned by mythtv. Same thing even after I set write permissions to everybody. How can that NOT have permissions to write into? Sounds strange.

So, actually this made me realize that even though I said earlier that the shutdowncheck script was working, I guess it wasn't being called either -- I thought those "...will occur in 10 seconds" things were a sign that the script is called, but I understand now that that's just mythttv's own countdown BEFORE the script is called. Duh. So it wasn't being run either ealier, myth just was counting down and then failing when calling it. Oh well. So: seems like scripts are being called but permissions fail. This even though visudo is like above so I'm guessing this is a deeper problem with permissions and myth itself, not an issue with the visudo permissions for running these scripts.

More things to note (that might be helpful): normally I just have mythbackend start automatically in the background when I boot up. I really don't even remember how and when I set that up, I was just following some instructions somewhere and got it to start up by itself, months ago. But anyway, I suppose it probably is starting as root since if I try to start it with:

```

/etc/init.d/mythtv-backend start
```

...I get this:

```

Starting MythTV Backend: mythbackendstart-stop-daemon: Unable to set initgroups() with gid 1001 (Operation not permitted) 

```

Unless I run it with sudo, in which case it starts fine. This is actually how I've "always" started it if I've ever had to shut it down, as far as I remember. However, just starting it with "mythbackend" starts it just fine without any sudo, so maybe the init.d script needs to be owned by something else than root? And also, while I'm at it, who should the "user" in that script be? Mythtv? I really don't know if I had edited this script before or not but now I have, trying to see if it would help with these things to change the user. As it stands now, it's "important parts" are: 

```
DAEMON=$LOCATION/mythbackend
NAME="mythbackend"
DESC="MythTV Backend"
HOME=/root

test -x $DAEMON || exit 0

set -e

USER=mythtv
RUNDIR=/home/mythtv/mythrun
ARGS="-d --logfile /var/log/mythtv/mythbackend.log --pidfile $RUNDIR/$NAME.pid"

```

Is this how it should be? User mythtv? Home /root? This is the /etc/init.d/mythtv-backend file. Just trying to make sure my files are like they should be for using it under the mythtv user.

Alright, enough wondering...my point is that I'm thinking that because of something dumb I've done before, myth is being run somehow with wrong permissions and this is making all these scripts fail. The eternal optimist in me thinks that I just need to have some permissions set right so that I can have mythtv started under the mythtv user like normal people and then all will be fine in my world again :) . Then I'm hoping the scripts would have permissions as well etc. Sound reasonable? I think it kinda does but I haven't got a clue what to do next and I've been fiddling with these permissions probably too much already. Should I change ownership of all the mythtv files? mythbackend, init scripts? to mythtv. Or am I making no sense at all anymore? I'll be glad to post more files/permission info etc. if anything will help.  

Thanks again.

---

### Post by majoridiot on 2007-03-28
first, it was late and i erred... the echo to the mythvbackend.log should be done as sudo. ;)

second, there is a *lot* of info to digest in your post... but one thing jumps out immediately- the init script.

you do need to run /etc.init.d/mythtv-backend as root- so always sudo or it will fail.  this launches the
backend as a *daemon* and works with stop, start and restart.  you can run mythbackend as a "normal"
process with no problem as you noted.  also a good way to see what's going on, as you can watch the
log in real time.

anyway, the init script head that you posted looked screwy so i checked- it still seems screwy. back it up-

```
$ cd /etc/init.d
$ sudo cp mythtv-backend mythtv-backend.back
$ sudo nano mythtv-backend

```

then make the following changes to the inidicated lines:

```
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin   (add this as the first line if it is not there.)
DAEMON=/usr/bin/mythbackend
# HOME=/root   (comment it out with a hash)
RUNDIR=/var/run/mythtv
```

then launch the backend and see what happens.  you can restore the init script if needed by:

```
$ sudo cp /etc/init.d/mythtv-backend.bak  /etc/init.d/mythtv-backend
```

---

### Post by BatPenguin on 2007-03-29
OK, I think this is finally working now! First of all, the init script works now, thanks. I changed it to what you said and no problems now. I did - naturally - have a new small mysql authentication problem when starting mythbackend after that, but I got that  solved by fixing a password in a mysql.txt file. Apparently there's a few mysql.txt files on the machine and myth started using another one when I changed the init script user to mythtv. But that's fixed now, no errors on startup.

However, then I started seeing "no permissions" or "password" messages in the log for the scripts, so the visudo still wasn't working. I thought everything was set up like it should be permissions-wise, running it under mythtv user, had the visudo set up according to the how-to. But didn't get it going...soo....I suppose this could be called the sledgehammer method of getting it working but I added the mythtv user to the admin group and went ahead and chowned the scripts and /proc/acpi/alarm for mythtv. I know this is probably a very bad idea security-wise but, oh well, this isn't exactly a top secret government nuclear lab computer, the reason I'm setting this up, after all, is to get the machine to wake up daily to record Teletubbies for my daughter..:)

So, just like that it seems to work now. I just tested by having it shut down and wake up once to record something. I guess there could be more problems I didn't notice yet but looks good: scripts are called, machine shutdown and woke up, so pretty much seems to be OK now. No style points for how I handled those permissions, I know...I might give it another go later to get the sudos to work, but at the moment I'm just happy it seems to work this way.

Thanks a lot for all the help, I really appreciate it. The how-to is great, these problems were clearly caused by my setup's problems. All in all these Ubuntu forums are quite amazing - as much as I like Ubuntu for other reasons too (used to play around with Fedora and SuSE for a while), the community really is the best Ubuntu "feature" in my mind. Not having to read five RTFM replies to every newbie/non-expert question is very, very nice.

Anyway, I'll get back to you with my board information once I've had a few days to make sure that everything really works like it should. Thanks again!

---

### Post by majoridiot on 2007-03-29
> **BatPenguin said:**
> However, then I started seeing "no permissions" or "password" messages in the log for the scripts, so the visudo still wasn't working. I thought everything was set up like it should be permissions-wise, running it under mythtv user, had the visudo set up according to the how-to. But didn't get it going...soo....I suppose this could be called the sledgehammer method of getting it working but I added the mythtv user to the admin group and went ahead and chowned the scripts and /proc/acpi/alarm for mythtv. I know this is probably a very bad idea security-wise but, oh well, this isn't exactly a top secret government nuclear lab computer, the reason I'm setting this up, after all, is to get the machine to wake up daily to record Teletubbies for my daughter..:)

/me *rolls* @ the teletubbies comment

chowning the scripts, etc. is really no big deal- unless for some reason another process/app wants 
access to /proc/acpi/alarm.  if you think that might be the case, follow your chown instruction with:

```
$ sudo chmod o+rw /proc/acpi/alarm
```

which will give read/write access outside of the mythtv group.

as you note, your problems were likely due to a funky install.  next time you do a clean install of
mythtv, if you follow the ubuntu guides: [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) then the 
shutdown/wakeup setup should go as written.  

> **BatPenguin said:**
> All in all these Ubuntu forums are quite amazing - as much as I like Ubuntu for other reasons too (used to play around with Fedora and SuSE for a while), the community really is the best Ubuntu "feature" in my mind. Not having to read five RTFM replies to every newbie/non-expert question is very, very nice.

i couldn't agree more.  we have a great community and the forums are *usually* a great source of
non-flame support.  i tried ubuntu based on the distro reputation and stayed because of the quality
of the software *and* community.

> **BatPenguin said:**
> Anyway, I'll get back to you with my board information once I've had a few days to make sure that everything really works like it should. Thanks again!

Please do, so that it can be added to the list- or just click on the "edit" link at the top of that page,
register and add it yourself.

i'm glad you finally got this working! :D

---

