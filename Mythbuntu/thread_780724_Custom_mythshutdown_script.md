---
title: "Custom mythshutdown script"
date: 2008-05-03
forum: Mythbuntu
---

### Post by amphibem on 2008-05-03
I am looking for some help with a custom shutdown script for my mythbox, but a quick explaination first.

My media-center is a combined backend/frontend that sits in the lounge and is used for TV, Music, FM radio and Videos. I also use mythtv player to view recorded TV from my desktop and mythweb to monitor the media-center and schedule recordings. It is also a samba server holding all my music, which I am playing during the day on my desktop. So I do not want the box shutting down or sleeping when it thinks it is idle throughout the day.

I do however want to it to shutdown after its last recording at night, and wake up in the morning so it is there when I get up. So I had a look at mythshutdown --help:

  ```
Usage of mythshutdown
-w/--setwakeup time      (sets the wakeup time. time=yyyy-MM-ddThh:mm:ss
                          doesn't write it into nvram)
-t/--setscheduledwakeup  (sets the wakeup time to the next scheduled recording)
-q/--shutdown            (set nvram-wakeup time and shutdown)
-x/--safeshutdown        (equal to -c -t -q.  check shutdown possible, set
                           scheduled wakeup and shutdown)
-p/--startup             (check startup. check will return 0 if automatic
                                                           1 for manually)
-c/--check flag          (check shutdown possible
                          flag is 0 - don't check recording status
                                  1 - do check recording status (default)
                          returns 0 ok to shutdown
                                  1 reset idle check)
-l/--lock                (disable shutdown. check will return 1.)
-u/--unlock              (enable shutdown. check will return 0)
-s/--status flag         (returns a code indicating the current status)
                          flag is 0 - don't check recording status
                                  1 - do check recording status (default)
                          0 - Idle
                          1 - Transcoding
                          2 - Commercial Flagging
                          4 - Grabbing EPG data
                          8 - Recording - only valid if flag is 1
                         16 - Locked
                         32 - Jobs running or pending
                         64 - In a daily wakeup/shutdown period
                        128 - Less than 15 minutes to next wakeup period
                        255 - Setup is running
-v/--verbose debug-level (Use '-v help' for level info
-h/--help                (shows this usage)

```

So what I think I want here is a sh script that will run from say 10pm every 5 minutes until the box sleeps. Something like:

```

#shutdown.sh
#!/bin/bash
mythshutdown -c
{some sort of if statement, run if answer above is 0}
    mythshutdown --t time 07:30:00 -q

```

Questions: 
1) Am I on the right track? Or is this the hard way of doing things?
2) The 'mythshutdown -t' command wants a time stamp with the year and month etc. How can I include this in the script, or will it auto-run the next day if it isn't given a day?
2) I had tried 'mythshutdown -c' and 'mythshutdown -s' in the terminal and got no output. How can I make the script read this output?
3) How can I set this script to run at say 5 minute intervals after 10pm?

Your help is much appreciated.

Edit 1: OK so some quick googling gets me to a get howto on Cron, it looks like I can easliy use this to set my shutdown.sh script to run at 10pm very night. How about repeating every 5 minutes?

---

### Post by amphibem on 2008-05-04
I will give a quick update on this for those following:

I have set RTC-Wakeup in BIOS, and set it for 9am this morning. This didn't work. It is still set and I will see what happens tommorow. I then run a mythshutdown trial run:

```

sudo mythshutdown -w 2008-05-0416:26:00
sudo mythshutdown -q

```

This successfuly shut the machine, however it didn't wakeup. 

So this isn't looking promising. The machine is now recording for the rest of the night but I will redo these tests, and also double-check the BIOS is set to the correct time. Any other thoughts on what it will take to make this work? There seems no point trying to get any scripts to work until I can do this stage. 

I should also note there are plenty of guides on how to do ACPI Wakeup etc, but these tend to pre-date 0.21 and I knwo there have been changes that take most of the complexity out. However there may be steps I am missing. So would appreciate an help :)

---

### Post by BatPenguin on 2008-05-25
> **amphibem said:**
> 
I should also note there are plenty of guides on how to do ACPI Wakeup etc, but these tend to pre-date 0.21 and I knwo there have been changes that take most of the complexity out. However there may be steps I am missing. So would appreciate an help :)

Are you still trying to figure this out or did you get a solution done already? I'm actually looking to tweak my own mythshutdown script a bit and was looking for what people have done before here, so I'd appreciate hearing how this is going.

For you, I'd probably try doing this:

- make the shutdown script check if it's day (after 7am, before 10pm, whatever), if it is -> disable shutdown (in the same manner that it normally checks if there's logged in users -> disable shutdown). Otherwise let it run normally.
- schedule a one-minute recording at 7 am every day (or whenver you want it to wake up) to have it always wake up at that time. This would just use the normal myth wakeup to get up at the right time...sound easy to me.

How's that sound? I'm sure there's more ways to do it but that sounds liek something I might do in your case. 

Personally, I'm trying to think of a nice way to have a "disable automatic shutdowns" switch I can use when I want to. What I need that for is that I sometimes log into the system over ssh, run something (like a bittorrent download) in a "screen" and want it to keep going and the machine not shutdown automatically after I've logged out. Any ideas? I'm thinking of just making a script that sets some variable to 1 when I type "disable_shutdowns" or something and then have the script check that before checking for logged-in users. Gotta find that bash programming book I have somewhere now...(I've done very little scripting ever...)

---

### Post by amphibem on 2008-05-25
Hey appreciate your input, turns out after a lot of fiddling I just couldn't get the machine to wake up automatically at all; from BIOS, NVRAM or WOL. I eventually decided the old PSU (which I'm gussing is of the orginal ATX spec) is capable of it.

I do like your idea, I had basically decided to go with setting the mythshutdown 'lock' swith during the day and let it run normally otherwise. I think i just need to get a new PSU.

Thanks for your help.

---

### Post by BatPenguin on 2008-05-25
> **amphibem said:**
> Hey appreciate your input, turns out after a lot of fiddling I just couldn't get the machine to wake up automatically at all; from BIOS, NVRAM or WOL. I eventually decided the old PSU (which I'm gussing is of the orginal ATX spec) is capable of it.

I do like your idea, I had basically decided to go with setting the mythshutdown 'lock' swith during the day and let it run normally otherwise. I think i just need to get a new PSU.

Thanks for your help.

Heh, you know what...I'm such an idiot. I totally didn't see that mythshutdown has that "lock/unlock" switch usage. I have no idea how I missed that, tha'ts all I need! So, yeah, same for me - what I need to do is just simply run "mythshutdown -l" when I connect via ssh and want the machine to stay up, no need to modify scripts. You should probably just do the u and l switches with a cron job then, one that runs in the morning and other in the evening. For wakeup, the one-minute manual program in the morning might still be the easiest way.

Anyway: about your PSU. I guess that's probably it then if you've set all the BIOS options and followed the guides. I did have some problems though, so I'll just mention those in case (unlikely) these could help you:

- For myth wake-ups, the only change I've had to make is that I made the mythtv user the owner of /proc/acpi/alarm, otherwise mythtv didn't get to change it and write the time (I got permissions errors in the log). Testing went fine outside of myth even without this change, so I knew the problem was myth and this probably won't help you.
- In my BIOS, wakeups had to be ON, not OFF as the how-to said, for these timed wake-ups to work.

For WOL, sending wakeup-packets from outside the local lan didn't work with my old router, but from the LAN they always worked. This was really weird, I had ports forwarded and all, just couldn't get it to work. Anyway, I changed routers and they worked fine then even from outside. Oh, and for outside wake-ups, I setup an account at [www.noip.com](www.noip.com) (free, just have to keep activating every two months or so) so now I can always send a wakeup to my machine from anywhere and log into mythweb for schedulign etc. Very handy, the service just has a little deamon running on your machine that tells the noip service what your IP is currently and binds it to a proper sitename (something.something.com). So now I truly can always get to my myth box from anywhere.

If it's just the PSU you need to change, I totally recommend it. The wakeups/WOL are very nice features. Good luck!

---

### Post by amphibem on 2008-05-25
Yer I have tried WOL to and from most of my computers with no luck so maybe it is my router, not really a high priority. I do have a no-ip account though as I wanted external mythweb access.

Other than that what I forgot to mention in my LAST post is I am not actually running myth anymore, while I wait on full support for NZ's HD system I am using (well trying to) MediaPortal. Really missing myth too, not going too well with the Windows software.

So yes, a new PSU eventually and all will be good. As is I will run 24/7 and try to get digital TV working properly.

---

### Post by bmwman on 2008-09-04
Did you guys ever figured this out? I'm trying to do the same thing. Basically I use the machine to download torrets or listen to Amarok's online stations.
 Can I modify the "shutdown --check script to check if Azureus or Amarok is running and if not then shutdown?

---

### Post by deadcyclo on 2008-09-04
There is a great guide on how to get the backend to automatically turn off after a frontend has disconnected and it isn't recording anything [here](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake). It will also automatically turn the backend on when a recording is scheduled, and turn it back off again afterwards. (And it works - I just finished setting my box up to do this today).

PS! To those of you having trouble with WOL. WOL is broken in Ubuntu 8.04. You have to modify the shutdown and reboot scripts to not include the -i parameter, remove the network manager and configure it to automatically start the network at boottime (like a normal distro ;) ) In addition you have to add the enable WOL startup script.

---

### Post by bmwman on 2008-09-04
I already have everything working. I used the same guide also. That's not what I want though. I need to add couple of extra steps to check before it shut down . Currently if there is no Backend connected and nothing currently recording the machine would shut down. I have Azureus or Amarok running sometims so if they're on I need to prevent the shutdown. I know I can use the Lock option in Mythwelcome but I would really prefer to have that automatically.

---

### Post by deadcyclo on 2008-09-04
That reply was actualy for the previous posts, not yours ;)

Anyhow. I'm not using the mythwelcome. Instead I'm letting mythbackend do all of the work. I use the Startup command to write a temporary file that determins if the frontend should load or not.

I have absolutely no idea how to solve it when using mythwelcome, but I wrote a quick and dirty script that should work if you set it up to only use mythbackend.

```

#!/usr/bin/env perl

$app1 = `ps aux|grep azureus|grep -v grep`;
$app2 = `ps aux|grep amarok|grep -v grep`;

exit 1 if ($app1 ne "" || $app2 ne "");
exit 0;

```
You might need to change the names above, I don't use either of the programs so I don't know what the process name is.
Change the Pre Shutdown check-command setting in mythbackend to run the above script, and you should be good to go.

If you don't want to only use mythbackend this modification might help you. (I can't guarantee it since I don't use mythbackend my self)

```

#!/usr/bin/env perl

`/usr/bin/mythshutdown --check`;
$res =  $? >> 8;
exit $res if ($res>0);

$app1 = `ps aux|grep azureus|grep -v grep`;
$app2 = `ps aux|grep amarok|grep -v grep`;

exit 1 if ($app1 ne "" || $app2 ne "");
exit 0;

```
Calling the above script from the inside mythwelcome probably should work.

---

### Post by gregshldn on 2009-01-01
For what it's worth, I had a similar quest somtime ago too ...

[http://ubuntuforums.org/showthread.php?t=639669](http://ubuntuforums.org/showthread.php?t=639669)

if mythshutdown returns 0 then myth shuts the PC down, so just put some code in to detect any app(s) amd return 1 if you want to about shutdown.

The only problem I find is starting the PC up, going to make a cup of coffee and finding it shut down again because the kettle had too much water to boil :)

---

### Post by Blonddeeni on 2009-01-26
Hi Bmwman. I also had similar requirements on my system, and just like deadcyclo, I ended up letting the Backend do all the work by modifying my MythShutdownCheck script to look for various programs that I might be running. Should any of them be doing something, then the backend will keep the whole system running until those programs are finished.
It also checks for any particular user logged on. (For when I'm fiddling with things :))

I've used the "top" command, but any command that has a look at what processes are running would do.
I also modified the startup sequence to disable the Frontend from auto starting, and instead manually start it either from the mouse or via my remote.

The link for how I arrived at all this is [http://ubuntuforums.org/showthread.php?t=723722&page=2](http://ubuntuforums.org/showthread.php?t=723722&page=2)

I have since modified the MythSHutdownCheck script even further than the last post on ...

(I'm not at my system, but I think it is something like the following.)

if top -b -n 1 |grep -q transcode ; then
   exit 1
  else if who |grep -q nobby ; then
   exit 1
  else if top -b -n 1 | grep -q amorak ; then
   exit 1
  else if top -b -n 1 | grep -q azeures ; then
   exit 1
 else
exit 0
      fi
    fi
  fi
fi

So anytime it would suddenly shutdown on me, I'd realise that I found another hole and just add another "else if top" line (and "fi" for the bottom).

All works for my peculiarities, and I hope it gives you another way of looking at solving your situation.

Cheers
Blonddeeni.

---

