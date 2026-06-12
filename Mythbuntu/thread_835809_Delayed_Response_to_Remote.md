---
title: "Delayed Response to Remote"
date: 2008-06-20
forum: Mythbuntu
---

### Post by Sonthun on 2008-06-20
I've got a Silicon Dust HDHomerun that I'm using to pick up my remote control on my Mythbuntu setup with lirc.  This remote control setup worked perfect when I was running Feisty Fawn, but I wiped everything and started over with the Hardy Heron release when I started having other problems.  

Since I've started over, the remote works fine for the myth option screens, but after watching a recording for a short amount of time it will become very sluggish.  The longer the recording is watched the more sluggish it becomes until it is taking about a minute or more to respond.  Once it responds to one key press then it responds quickly to subsequent key presses and then goes back to being sluggish after watching the recording again for a while.  Can someone help me diagnose this behavior and figure out what I need to do to fix it?

Thanks.

---

### Post by dsegel on 2008-06-23
Sorry I don't have anything useful to add, but I'm experiencing the exact same thing. My remote sensor is the one on a PVR-150. I also have an IR sensor on my pcHDTV-5000 but I never got that one working at all.

I'm just starting to investigate this issue - I'll post back if I find out anything helpful.

---

### Post by netslacker on 2008-06-26
I am experiencing this same issue.  The longer a show is played, the longer the delay is in responding to remote control commands.

Anyone resolve this?

Silverstone LC20M case (with VFD & iMON Pad Remote)
Mythbuntu 8.04 all updates applied.

---

### Post by netslacker on 2008-06-27
This is actually a really annoying issue that I see now very prevalently. It occurs whenever I am watching a pre-recorded show - during this time any remote commands are delayed up to 20+ seconds and are all queued up (ie: hitting esc, esc again - in case the first one didn't work, then FF or Rwd, then more keys results in an initial delay of 20 or more seconds... then the execution of all remote commands pressed carried out in rapid succession).

If I am watching a longer show (say a pre-recorded movie) then this issue is present right off the bat.  Otherwise, it doesn't appear until the show has played for a bit.

I enabled realtime priority threads to see if a higher priority would resolve it, no dice.

There are no errors in any of the log files, everything appears to be functioning normal.

Any clues would be appreciated.

Thanks.

---

### Post by netslacker on 2008-06-27
I think I have a possible solution to the delayed response to the remote problem that some (myself included) have experienced.

When I run "top" from an ssh session and play a show (attempting to reproduce the delay) I am able to successfully use the remote without issue when the total CPU % is below max.  However, once in a while, the process for Xorg will spike to ~97% and when it does, combined with other processes, the CPU is pegged and the remote control delay problem is now present. The Xorg process seems to vary from ~10% to 99% when a show is playing (not exactly sure why) but when it spikes to higher levels the remote delay is introduced and commands from the remote are not executed until the Xorg process goes to a lower CPU level.  Once that occurs, CPU cycles are freed and the commands execute.

Here's the other thing that I have noticed.  This usually only ever happens while the process mythcommflag is also running. This is the commercial flagging process that is kicked off (by default) when a show is recorded.  Since this process is CPU intense, it competes heavily for CPU time and can contribute to your CPU going to max.  There are a number of suggestions out there on how to disable this feature (backend setup) and then run it as a nightly cron job (say, at 2am) so that it does not interfere with regular myth usage. I've seen that while this process is running it is eating up 1/4 to 1/2 of my overall CPU power available (2 core system). So, if Xorg and mythfrontend are working to play a program AND mythcommflag is running you will have a much higher potential to run out of CPU power, when that occurs the remote commands are queued until CPU becomes available.

I have disabled the mythcommflag process from running and will run it as a cron job during the night.  Since doing this I haven't noticed the remote control lag/delay as so far it has freed up enough CPU to keep things running smooth. This is only after about an hour of testing, so YMMV.  But so far so good.

Another possible solution might be to give a higher priority to lirc (if that is the piece that is being queued).  But I'm not sure how to go about doing that.

One other help to resolving this (and actually helping your system in general) is to lower the priority of the Xorg running process.  For me, this process would jump to 99% and basically peg one of the CPU cores which significantly contributed to the remote control delay (and overal performance of the system).  At a command prompt (via ssh) I typed: "sudo renice -10 <pid>" where the pid is the number I got from running "top" and finding the Xorg process (first in the list since it was pegged at 99%).  Since this change Xorg has jumped to a maximum of 24%, freeing up significant CPU cycles.

I've yet discovered another setting that may help in resolving this: in the Xorg.conf file make sure you have Option "UseEvents" "true" in the Device section.  This appears to keep X from using a busy wait and keeps CPU usage down. **UPDATE: Nevermind, using the "UseEvents" option totally kills my remote control and requires me to re-install the kernel modules to get it working again (confirmed after 3 attempts).

---

### Post by Sonthun on 2008-06-27
I've been having the problem even when mythcommflag isn't running.  I'll take a look at my cpu load when a program is running to see if it is maxing out like your is.  I also have a dual cpu.  Can mythtv not use both cpu's?

Edit:
Interestingly enough, it looks like having System Monitor running seems to wake up the computer enough to process remote commands.  When running system monitor the remote never had any delay.

---

### Post by netslacker on 2008-06-28
I have added 2 more possibilities to my earlier post: [POSSIBLE SOLUTION] above that shouldn't be over looked.

---

### Post by Lodurr on 2008-08-23
I resolved this problem simply by reinstalling Hardy and MythTV, rather than continuing on my Feisty -> Gutsy -> Hardy upgrade.  I previously had the exact same problem, that remote presses would usually take an extra 5 - 90 seconds to register.

---

### Post by netslacker on 2008-08-25
> **Lodurr said:**
> I resolved this problem simply by reinstalling Hardy and MythTV, rather than continuing on my Feisty -> Gutsy -> Hardy upgrade.  I previously had the exact same problem, that remote presses would usually take an extra 5 - 90 seconds to register.

Can you be more specific? You re-installed Hardy and then applied Myth?  Or you started fresh w/ Mythbuntu?

I can't seem to fully get rid of this problem and I'm now willing to try just about anything.  Now that the new season is approaching I need to get this system stable.

---

### Post by newlinux on 2008-08-25
I posted a thread a while back with similar issues (no responses). in my case it happens with LIRC or the keyboard and only on liveTV and recordings (not mythvideo using the internal player). Glad (well sad for you guys) its not just me.

---

### Post by Lodurr on 2008-08-26
Yes, I installed Hardy and then MythTV.  I pretty much followed this guide: [http://parker1.co.uk/mythtv_ubuntu.php](http://parker1.co.uk/mythtv_ubuntu.php)

---

### Post by newlinux on 2008-08-28
anybody got any ideas? this is really annoying me.

---

### Post by netslacker on 2008-09-03
I recently rebuilt my myth box using ubuntu 8.04 LTS (32bit) and then installing Myth.  I was previously using mythbuntu 8.04.1 64bit amd.  I am sad to report however, that the delayed response to the remote control is still present.

I'm wondering if any of the other distributions would exhibit the same problem, like knoppmyth or one of the others. I may go this route if I can't resolve it soon.

I also tried raising the priority of the lircd process that was running and various other tweaks, all with no change.

Any other suggestions?

---

### Post by uopjohnson on 2008-09-18
It looks like this is a myth issues as it is being reported on the mythtv mailing list:
[http://www.gossamer-threads.com/lists/mythtv/users/348526](http://www.gossamer-threads.com/lists/mythtv/users/348526)
with multiple disttributions.  I have sepearte backend/frontend(s) so it isn't a commflagg issue and both of the frontends are WAY over powered.  There is nothing in any log to account for this, but I will keep an eye on the xorg process tomorrow to see if that is the cause.  I can verify with certanty that this isn't a lirc issue as I have the same delayed response when using the telnet interface and a usb keyboard.

---

### Post by newlinux on 2008-09-18
Same here. Happens with the keyboard, so it's not LIRC, happens when I am commflagging from a remote machine or not commflagging at all. Interestingly for me, it never happens in mythvideo (and I use the internal player for mythvideo). It also happens on recordings on the remote and local backends, so it probably isn't a network problem either. Only happened since upgrading to .21 and 8.04. I've tried fiddling with various playback settings to no affect.

---

### Post by uopjohnson on 2008-09-18
Second the mythvideo, never a problem there.

---

### Post by uopjohnson on 2008-09-19
xorg was pegged at 97% when watching recordings.  Read that hear, or in another thread and confirmed it on my system.  This seemed like it might be the cause of the problem so I looked around for that and found a solution, at least for me.  I added
```
Option "UseEvents" "on"
```
to the Device section of xorg.cong and my Xorg cpu usage went down to 3% and I have had no problems with the remote tonight.
Give it a try, maybe it will work for you.  It seems to be an nvidia speicific fix, so it may not fix all problems.

---

### Post by netslacker on 2008-09-29
I just wanted to link the two threads together that discuss this issue since it took me several weeks to resolve.

[http://ubuntuforums.org/showthread.php?t=885337&highlight=delayed+response+remote](http://ubuntuforums.org/showthread.php?t=885337&highlight=delayed+response+remote)

The solution is indeed to add the following to the Device section of your Xorg.conf file:

```

Option "UseEvents" "on"

```

Thanks to all those that posted this solution.  I am reposting to make it clear that this code seems to be working for many people that have reported this problem.

---

### Post by ajhtiredwolf on 2008-11-04
Should my remote be listed as a device in the xorg.conf? I have a few device sections. the remote is an mceusb2.

---

### Post by uopjohnson on 2008-11-04
No the Device section you are looking for here is your nvidia video card.  The remote issue is a red herring, the actual problem is with CPU overload.

---

### Post by Geurrilla on 2008-12-28
I had the same / similar issue but this did not fix it (but it did help) -- this however fixed it perfectly: [http://www.gossamer-threads.com/lists/mythtv/users/359904#359904]("http://www.gossamer-threads.com/lists/mythtv/users/359904#359904")

>  A couple of people on IRC--one using Ubuntu 8.10 and another using
Fedora 10--asked about an issue where playback paused on every press of
a remote button, and I provided a (dirty) hack that worked around the
issue until the real fix/patch was made available in packaged versions
of Myth.

The problem was that Myth was running gnome-screensaver-command on every
button press, so the workaround was to create a link called
gnome-screensaver-command that referred to /bin/true and that exists in
a PATH directory that comes before the directory containing the real
gnome-screensaver-command.

I.e. given:
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
with (the real) gnome-screensaver-command installed in
/usr/bin/gnome-screensaver-command , creating the link:
ln -s /bin/true /usr/local/bin/gnome-screensaver-command
would avoid the problem with the remote.

The proper fix has now gone into the -fixes branch, now, so anyone who
used the hack should clean it up once they get MythTV 0.21-fixes r19222
(from 2008-12-03 04:36:29 +0000) or above. If you created a link at
/usr/local/bin/gnome-screensaver-command , as above, then clean it up with:
rm /usr/local/bin/gnome-screensaver-command

(Just feeling guilty about the ugly hack and had to say something,
hoping people would clean it up when it's no longer necessary. And,
since it seemed to have a rather pronounced effect on the latest Fedora
and Ubuntu distros, I thought I'd mention it here.)

Mike 

---

### Post by IntuitiveNipple on 2008-12-28
I'm currently working on a fix for this. I've got some packages available in my PPA already. Read more about it [in the forums](http://ubuntuforums.org/showthread.php?p=6443796#post6443796) or [in the bug report](https://bugs.launchpad.net/mythbuntu/+bug/311772).

---

### Post by Lodurr on 2009-01-02
> **uopjohnson said:**
> 
```
Option "UseEvents" "on"
```

Worked for me.  After my fresh Hardy install, I didn't have any remote responsiveness problems, but a few months later I had it intermittently, and just recently the problem was very persistent.  However, putting this line in xorg.conf cleared it all up.

EDIT: I'm running onboard Nvidia video card.

---

