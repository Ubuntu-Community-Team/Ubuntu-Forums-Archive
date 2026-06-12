---
title: "Wake on Lan / ACPI Shutdown question"
date: 2011-03-26
forum: Mythbuntu
---

### Post by jim.hitch on 2011-03-26
To save energy I want to get ACPI shutdown/wake up working and get the front end to wake on lan the backend when I turn on the frontend.

I had a go with Wake on Lan and failed, and then realised that perhaps the server needed to be asleep or hibernating, not fully shutdown, for this to work. It's unclear in the mythtv wiki.

So, before I start posting technical queries, is this true?

Given that I DO need to have the server sleeping or hibernating to use wake on lan, I discovered that my server neither hibernates or sleeps when requested. When given the command it just freezes.

Why is this? Is it because the backend is still running, or has my server not been set up right?

A couple of quick answers to these questions would set me off on the right path.

Thanks.

My setup:

Ubuntu 10.04 Server
MythTV 0.24 + fixes
Intel® Celeron® DualCore E3400 (2.6GHz) 800MHz FSB/1MB Cache
ASUS® P5G41T-M LX: MICRO ATX VALUE BOARD & DDR3, SATA-II, 2 x PCI
2GB SAMSUNG DDR3 DUAL-DDR3 1333MHz (1 x 2GB)

---

### Post by Dan_R on 2011-03-26
The server just needs to be shutdown, hibernated or in sleep mode in  order for wake on lan to work. The only time it won't work properly is  if loses power and you try to send a "magic packet" to wake it back up.  It would have to be turned back on and off/sleep/hibernated until it starts working  again.

I'm not sure why your server is freezing when you try to hibernate/sleep though. Dunno where to start with that one.

Of note, WOL no longer works for me since an update on Ubuntu 10.10 and haven't been able to fix it.

If you have any questions about ACPI Wakeup/Shutdown while using mythwelcome let me know, it's one of my favorite features on my backend.

---

### Post by AKADAP on 2011-03-27
On my system, neither sleep nor hibernate works. But my system shuts down and powers up fine with the ACPI stuff.

The fundamental question: Does the ACPI wakeup test work on your system? If so, you should be able to get Myth to shutdown and wake up fine.

Dan_R mentioned a problem with wake on lan not working after a power glitch. The solution is to set the option in the bios to have the computer turn on when the power comes on. This way, after a power glitch the computer will turn on, decide it has nothing to do and shut itself off again, but the shut down will reset the wake timer, and re-enable the wake on lan stuff that was upset by the power glitch.

---

### Post by jim.hitch on 2011-03-27
Thanks for getting back to me. I'll have a go this week when I get a chance, and report back.

I'm using 10.04, so wake on lan should work, right?

I'd like to use it in conjunction with ACPI.

Which wake on lan package have you used in the past?

---

### Post by alien878 on 2011-03-28
WOL should work if your HW supports it (MB, PSU and ethernet connector).  It works from a shutdown state (sudo poweroff).

Have you checked your BIOS settings?  For example, I have to enable "Power On By PCI(E) Device" even though my LAN is on-board.

A good indicator it is set set up is that the ethernet port typically has an LED lit when the computer is off.

---

### Post by jim.hitch on 2011-04-03
Hi

Thanks for the replies. Apologies for not getting back sooner, but my daughter is 18 months old... enough said!

So,

WOL works, no problem. Interestingly I couldn't get the 'powerwake' to work, which is in the ubuntu repos.

Unfortunately I can't get ACPI Wake Up to work.

The option 'Power on by RTC Alarm' exists in the BIOS but according to kern.log my system will only wake from S4 (sleep or hibernate), but as mentioned above, the machine won't do either (that'll be my next question).

There is an option in the BIOS called 'Suspend Mode' which is set to 'auto', but also has the options 'S1 (POS) only' and 'S3 only', neither of which I would want if my system will only wake from S4. 

The other problem is that if I have 'Power on by RTC Alarm' enabled, WOL doesn't work!

Mmmmm...

---

### Post by alien878 on 2011-04-04
For ACPI wakeup, you can try the scripts here:

[http://ubuntuforums.org/showpost.php?p=9617419&postcount=26](http://ubuntuforums.org/showpost.php?p=9617419&postcount=26)

The test script will help you get the HW working.  The actual ACPI support depends on your HW, so you might google it (ex. some MBs you have to disable RTS alarm in the BIOS).

If you get the test script to wake up the computer, you will then have to set up the scripts to set the wakeup time for the next recording.  Since this is a backend, it might take a bit of doing.  I would recommend using mythwelcome even though it is primarily for a combined front/backend.  You will need to do something to shutdown the backend if it was wakened by a WOL though.

---

### Post by jim.hitch on 2011-04-06
Thanks Alien & others.

the link you sent seems to work a treat.

now I need to find a script, or write one, to run on the frontend at start up to wol the backend and then pause before running mythfrontend.

Thanks for the help. I'll post my solution when I get around to it.

Jim

---

### Post by jim.hitch on 2011-04-08
I had a look at various options and have come up with a very simple solution to waking up the server from the separate frontend.

Simply put, the script below automatically runs from powering on the separate frontend.

It wakes on lan (wol) the backend (at MAC address 2X:Xf:3X:X4:X5:3X), then pauses for 35 seconds to wait for it to boot, then starts its local frontend.

```
#!/bin/bash

wol 2X:Xf:3X:X4:X5:3X

sleep 35s

mythfrontend --service
```

Having set up the ACPI options in the previous posts, I don't need to do anything in the frontend to keep the backend from shutting down when I don't want it to, or equally from NOT shutting down when I do want it too. Mythwelcome knows when the backend is idle and shutsdown accordingly.

It's amazing, and easy. I feel quite smug.

I know next to nothing about coding, so if anyone has any suggestions for improvements, it'd be good to hear from you.

---

### Post by joho500 on 2011-04-09
> **jim.hitch said:**
> Thanks Alien & others.

the link you sent seems to work a treat.

now I need to find a script, or write one, to run on the frontend at start up to wol the backend and then pause before running mythfrontend.

Thanks for the help. I'll post my solution when I get around to it.

Jim

Hi Jim,

I found a script a while ago that checks the backend. It checks the availability of the backend network port. 

```
LOGFILE=/var/log/startbackend.log

wol xx:xx:xx:xx:xx:xx

# check to see if backend is up
wget -q http://192.168.x.x:6544 -O /dev/null
while [ $? != 0 ]
do
  # try 5 times
  i=$[$i + 1]
  if [ $i -lt 5 ]
  then
    echo "[Start backend]: try $i" >> $LOGFILE
    sleep 10
    wget -q http://192.168.x.x:6544 -O /dev/null
  else
    echo "[Start backend]: Beware! Starting MythTV backend FAILED." >> $LOGFILE
    exit 1
  fi
done

mythfrontend --service

```

Cheers,
Joost

---

### Post by jim.hitch on 2011-04-12
Thanks Joost, I'll give it a go.

---

