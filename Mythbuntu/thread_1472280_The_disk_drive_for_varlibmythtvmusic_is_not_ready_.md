---
title: "The disk drive for /var/lib/mythtv/music is not ready yet or not present"
date: 2010-05-04
forum: Mythbuntu
---

### Post by larsolav on 2010-05-04
Dear all, 
I just upgraded to 10.04 last night. After the mandatory reboot I got this error when restarting (images are on picasaweb):
[IMG]http://picasaweb.google.com/lh/photo/Xcx1w_MZsWaj5RW5lyKEWg[/IMG]
[http://picasaweb.google.com/lh/photo/Xcx1w_MZsWaj5RW5lyKEWg?feat=directlink](http://picasaweb.google.com/lh/photo/Xcx1w_MZsWaj5RW5lyKEWg?feat=directlink)


Pressing M or S did nothing. Pressing ESC gave this screen:
[IMG]http://picasaweb.google.com/lh/photo/Zfn5OKcxSTlnzaYTKSn0_Q?feat=directlink[/IMG]
[http://picasaweb.google.com/lh/photo/Zfn5OKcxSTlnzaYTKSn0_Q?feat=directlink](http://picasaweb.google.com/lh/photo/Zfn5OKcxSTlnzaYTKSn0_Q?feat=directlink)


Letting it stand overnight seemed to work. This morning I was asked to upgrade the database and it worked. Mythttv worked (including mythmusic).

I then rebooted, just to see if the stuff above would happen again. It did not, but then I got something about the graphics card (onboard Nvidia 9400)having to start in low graphics, so I went to MCC and reinstalled the proprietary driver and rebooted. Upon reboot I got the same graphics error but now I actually read something about it not reading the EDID from the Tv, so I plugged the TV directly to the computer (not through ampliphier) and rebooted.

Now, upon restart I get the same images as above! 

Help! What do I do? My children are not going to be able to see their PBS shows this morning. Oh the horror!

---

### Post by williammanda on 2010-05-04
Is this computer just a frontend? If so are you using nfs for the music directory from the backend? Based on that I got this message due to my backend wasn't running.

---

### Post by larsolav on 2010-05-04
> **williammanda said:**
> Is this computer just a frontend? If so are you using nfs for the music directory from the backend? Based on that I got this message due to my backend wasn't running.

Hi William,
No this is a combined backend/frontend. But, come to think of it, I have the music folder SAMBA linked to a Windows machine where I store my music. So you are on to something!
Maybe that is the culprit? How can I fix it when the tooting thing won't even boot up all the way now?

---

### Post by larsolav on 2010-05-05
Well, I fixed it, but not elegantly.
I just did a fresh new and clean install of 10.04. This gave me an opportunity to install Mythbuntu to a compact flash drive. Next time I upgrade or mess with Mythbuntu I will clone the drive to another flash drive first...

---

### Post by Nobre on 2010-05-06
Not fixed yet... same problem here.

---

### Post by andree_b on 2010-05-07
Sounds like an upstart race condition:
mythtv-backend started before remote directories are mounted so it does not find those.
May be someone familar with upstart can give a hint?

---

### Post by toggles on 2010-05-11
I'm having the same issue, my boot disk is setup as follows

/dev/sdc1 mounts as /
/dev/sdc2 mounts as swap
/dev/sdc3 mounts as /mnt/mythtv

I get this error on a restart as for some reason /dev/sdc appears as /dev/sda, if I ctrl+alt+f1 then ctrl+alt+del and reboot the hard drive now appears as /dev/sdc and it boots fine.

My question is how to nail down the device to either /dev/sdc or /dev/sda, either way it was solid in 9.04 and 9.10 with no hw changes to the machine.

Cheers.

---

### Post by ian dobson on 2010-05-11
Hi,

Rather than using the device names (/dev/sda1) you could use the uuid's. These uuid's shouldn't change no matter which order the drivers load.

Have a look here [http://blog.mypapit.net/2008/04/linux-how-to-get-harddisk-uuid-number.html](http://blog.mypapit.net/2008/04/linux-how-to-get-harddisk-uuid-number.html) or [http://www.linuxforums.org/forum/misc/158702-solved-what-uuid.html](http://www.linuxforums.org/forum/misc/158702-solved-what-uuid.html)

regards
Ian Dobson

---

### Post by toggles on 2010-05-11
Thanks a lot, that fixed it, I should have thought of that ](*,)

I have a feeling that this might be the cause of others problems.

Cheers.

---

### Post by leafpaul on 2010-05-11
I am also having this problem on two mounts, one coincidently music, the other photos but these are nfs mounts over a network.  One of 3 things happens either, everything is fine, or I get to the same screen as larsolav where it pauses for no more than a couple of seconds then proceeds as normal, or I get booted to a command prompt with error messages saying the mounts cannot be found.

There would seem to be some sort of race condition going on but uuids will not solve my issue.

---

### Post by ian dobson on 2010-05-11
Hi leafpaul,

Maybe just add a delay to your mythbackend startup script. I'm using a m3u/ip recorder and need that apache is running before mythbackend starts so I've modified the upstart script in /etc/init/mythtv-backend.conf to read

```

# MythTV Backend service

description     "MythTV Backend"
author          "Matt Mossholder <matt@mossholder.com>"

start on (local-filesystems and net-device-up IFACE=lo)
stop on runlevel [016]

#expect fork
respawn

pre-start script
    # wait for listen on port 80
    while ! nc -q0 localhost 80 </dev/null >/dev/null 2>&1; do
        sleep 1;
    done
end script

script
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER
end script

```

the while loop just checks if apache is listining on port 80 and when apache answers the pre script ends and the script runs. The while loop waits 1 second between each attempt.

Maybe you could use something like
```

while ! exist /var/lib/mythtv/music/* </dev/null >/dev/null 2>&1; do
  sleep 1
done

```

Maybe you need to have a dummy file in the music directory that the script looks for.

Hope this helps
Ian Dobson

---

### Post by leafpaul on 2010-05-11
I've had this problem since the 10.04/0.23 release, and since it's early days it'll likely get fixed at some point.  But thanks for the pointer with the script change, if it continues I'll give it a whirl.  For me it's not a major issue at the moment only occurring probably one time in 10 boots.

---

### Post by leafpaul on 2010-05-12
Reading my posts I wasn't clear about the race condition which I suspect is between the wireless network connecting and fstab mounting the remote shares.  Still fixable with script change but probably not involving mythbackend starting which, I suspect, happens later in the boot sequence.

---

### Post by ian dobson on 2010-05-12
Hi,

Since 10.04 ubuntu uses upstart to start all processes/deamons. The good old rcX.d/S99script/K99script aren't really used anymore. The old startup method was just to start the scripts one after the other based on the SYY number. upstart is a more event based system that when something happens (network interface up) is checks which jobs are waiting for this event to happen and calls them.

This makes booting alot quicker as scripts can be called in parallel but it can also cause race conditions, where one process is waiting for the results of another (mount file system) but both scripts start at almost the same time.

Upstart supports quite afew events/triggers, maybe you can modify the upstart job for mythtv-backend so that it only fires when network filesystems are up.

The line start on (local-filesystems and net-device-up IFACE=lo) in my case causes myth-backend to start when the local filesystems are up and network interface lo is up. I think upstart supports the event start on (network-filesystems) which would cause mythtv-backend to start later, when your nfs shares are up.

Regards
Ian Dobson

---

### Post by leafpaul on 2010-05-12
Thanks Ian for the pointer about upstart, I knew it existed but I've never looked in detail at how it worked before. Only using it to start and stop processes.

I have checked the boot log for a number of boots and sometimes the network mounts fail and sometimes they succeed (I think this only records the first mount attempt).  Most of the time even if there are errors in the boot log (ie failed mounts) by the time that mythtv has started the network mounts have been successfully mounted in the background.  Going through the upstart scripts there is one "mountall-net.conf" which says in the comments:

"# Send mountall the USR1 signal to inform it to try network filesystems
# again."

ie it tries to remount the network shares - the vast majority of the time this is successful.  But for some reason every once in a while this upstart script fails to remount the network mounts.  Not sure why, and I cannot find any logging to indicate whether this script is actually running in this circumstance.  I will have a detailed look through all the logs next time it happens to see if there are any clues.

---

### Post by ian dobson on 2010-05-12
Hi leafpaul,

Looking at the mountall-net.conf file:-
```

# mountall-net - Mount network filesystems
#
# Send mountall the USR1 signal to inform it to try network filesystems
# again.

description     "Mount network filesystems"

start on net-device-up

task

script
    PID=$(status mountall 2>/dev/null | sed -e '/start\/running,/{s/.*,[^0-9]*//                                                          ;q};d')
    [ -n "$PID" ] && kill -USR1 $PID || true
end script

```

It looks as if the script starts when the network device starts up. Maybe you should try adding a delay to the script or maybe only start the script when your ethX device starts up. Something like:-
start on net-device-up IFACE=eth0

Do you have several network cards in you backend? 
Are you using DHCP for the IP address of the backend?
Are you using the IP address or DNS name of the network file system?

Regards
Ian Dobson

---

### Post by leafpaul on 2010-05-12
Do you have several network cards in you backend?
No but it is wireless so in my case:

start on net-device-up IFACE=ath0

I'll give this a try, although I can see future updates overwriting this modified file with the standard one and in 2 years time I'll be wondering why the issue has suddenly recurred ;-)

Are you using DHCP for the IP address of the backend?
No, fixed IP

Are you using the IP address or DNS name of the network file system?
No aliasing the IP using the hosts file

I am assuming the loopback interface (auto lo) couldn't produce a positive net-device-up for

"start on net-device-up"

even if ath0 fails.

---

### Post by ian dobson on 2010-05-12
Hi leafpaul,

I am assuming the loopback interface (auto lo) couldn't produce a positive net-device-up for "start on net-device-up"

I'm not sure, but I see some conf files have net-device-up != lo so it looks as lo up produces an event.


I'll give this a try, although I can see future updates overwriting this modified file with the standard one and in 2 years time I'll be wondering why the issue has suddenly recurred 

apt-get update complains when your local version of a configuration file is different to the maintainers version and gives you the option to keep the old version/install the new version/compare the differences.

I've started looking into upstart abit more and although I find it a good idea/it seems to speed up the boot sequence, I'm hearing alot of problems caused by race conditions. I'm starting to think about writing a script that reads through the conf files and builds a dependancy list (abit like bootchart without booting). It's just an idea at the moment but I've got afew days off work and abit of time free.

Regards
Ian Dobson

---

### Post by leafpaul on 2010-05-12
Thanks for the info Ian

"apt-get update complains when your local version of a configuration file is different to the maintainers version and gives you the option to keep the old version/install the new version/compare the differences."

You would like to to think so but my lirc "hardware.conf" file is regularly overwritten without prompting during updates....., maybe an unusual file though.  Just as well there aren't that many lirc updates.

Interesting idea to build a boot sequence for the scripts, one of the things that I couldn't find is any info on the order that the scripts are invoked which was easy to determine for the old init.d set up.  I appreciate that many of them are called at the same time and then wait for events but there must? be a co-ordinating base script or maybe not.

Interesting the line "net-device-up != lo", the fact that lo might be detected by net-device-up would explain the symptoms that I am seeing, so I'll give this a go.

Ian, Thanks again for your help with this

---

### Post by ian dobson on 2010-05-12
Hi,

The order scripts start in upstart isn't fixed. It's more like dominos that fall over knocking down other ones. An event could cause one or more scripts that produce more events (emit) that can cause other scipts to start.

The backend code for a dependancy tree for upstart jobs isn't that hard, the problem will be displaying the results in a user readable form.

Regards
Ian Dobson

---

### Post by leafpaul on 2010-05-13
OK tried editing the mountall-net.conf file with both:

start on net-device-up IFACE=ath0

and

start on net-device-up IFACE!=lo

both caused the the boot to drop to a command prompt with error messages concerning the failed mount of the network mounts (same messages as reported earlier in this thread), I tried 3 boots with each and on all occasions drop to the command prompt as opposed to with "start on net-device-up" which produces that result relatively rarely.

This result seems a bit odd, as if something else might be causing it.  I'll continue to tinker and will report if I find anything which solves the problem.

---

### Post by ian dobson on 2010-05-13
Hi,

Maybe try adding a short delay before running the mount all script.

```

script
    sleep 2
    PID=$(status mountall 2>/dev/null | sed -e '/start\/running,/{s/.*,[^0-9]*//;q};d')
    [ -n "$PID" ] && kill -USR1 $PID || true
end script

```

Regards
Ian Dobson

---

### Post by leafpaul on 2010-05-13
Ian

Up to sleep 5 fails to work completely (still dropped to a prompt sometimes) and by sleep 5 the mythwelcome screen opens before mythbackend has started (both FE and BE on same machine - although this is not an issue.  Small values for sleep eg 2 seem to cause other issues with the boot hanging.  I think I'll leave the script as it is as by the time you are at sleep 5 the occasional failed boot followed by a reboot takes less time than artificially slowing the boot down all the time.

Paul

---

### Post by havenoname on 2010-05-15
I had a similar problem and it is solved, try the following:

[http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html](http://www.nyutech.com/2009/03/make-ubuntu-mount-partitions-and-drives.html)

---

