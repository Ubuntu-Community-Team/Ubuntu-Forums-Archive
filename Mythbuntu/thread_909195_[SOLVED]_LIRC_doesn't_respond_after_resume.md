---
title: "[SOLVED] LIRC doesn't respond after resume"
date: 2008-09-03
forum: Mythbuntu
---

### Post by SiHa on 2008-09-03
Mythbuntu 8.04.1 i386, P4 2Ghz, Nvidia 5200, Homebrew serial receiver.

I'm having a small problem resuming. After resuming from pm-suspend, Mythtv can't see the backend and the remote doesn't work.
Thanks to 'caljohnsmith' I've managed to locate the place to add a script to run on resume : /usr/lib/pm-utils/sleep.d.

I need to restart LIRC & Mythfrontend in that order to get things up and running again. 

So I wrote a little script '00test' and renamed the previous '00..' to '01...' to make sure it was the last hook to be executed on resume, and placed it in the above dir:

```

#!/bin/bash

case "$1" in
	suspend|hibernate)
                killall mythfrontend.real
                ;;
	resume|thaw)
                /etc/init.d/lirc restart
                mythfrontend &
		;;
esac
```

The system suspends, and appears to resume OK. /var/log/pm-suspend.log shows both LIRC restarting, with three OK's, and Mythfrontend starting OK. The frontend log shows Lirc successfully initialising using /home/frontend/.lirc/mythtv.

Now Myth is OK, it can see the backend and it functions normally but the remote doesn't work.

'ps -A' shows an LIRCD process but 'irw' does nothing.

Run the above script manually and voila! the remote works. In fact, I've found that replacing the 'restart' argument with 'force-reload' works equally well when run from the command-line.

So LIRC is loaded, but it just doesn't want to talk to anyone. As I'm using a homebrew receiver, I'll take a 'scope home tonight and see if anything is actually being generated (ie - if the serial port, ttyS0 is being initialised correctly).

Apart from that, I'm stumped.

Edit: I've just realised, typing this that there are two sleep.d's and scripts from both run at resume. Perhaps I should try the script in the other one - /etc/pm/sleep.d?

Is there an lirc / lircd log that I can look at? I've seen something about running ```
lircd --nodaemon
```, would that help to debug this? How do I do it?

Sorry for all the questions, but I'm a relative Linux noob (four months in and counting).

---

### Post by mrand on 2008-09-03
> **SiHa said:**
> Mythbuntu 8.04.1 i386, P4 2Ghz, Nvidia 5200, Homebrew serial receiver.

I'm having a small problem resuming. After resuming from pm-suspend, Mythtv can't see the backend and the remote doesn't work.
Thanks to 'caljohnsmith' I've managed to locate the place to add a script to run on resume : /usr/lib/pm-utils/sleep.d.

I need to restart LIRC & Mythfrontend in that order to get things up and running again. 

So I wrote a little script '00test' and renamed the previous '00..' to '01...' to make sure it was the last hook to be executed on resume, and placed it in the above dir:

```

#!/bin/bash

case "$1" in
	suspend|hibernate)
                killall mythfrontend.real
                ;;
	resume|thaw)
                /etc/init.d/lirc restart
                mythfrontend &
		;;
esac
```

The system suspends, and appears to resume OK. /var/log/pm-suspend.log shows both LIRC restarting, with three OK's, and Mythfrontend starting OK. The frontend log shows Lirc successfully initialising using /home/frontend/.lirc/mythtv.

Now Myth is OK, it can see the backend and it functions normally but the remote doesn't work.

'ps -A' shows an LIRCD process but 'irw' does nothing.

Run the above script manually and voila! the remote works. In fact, I've found that replacing the 'restart' argument with 'force-reload' works equally well when run from the command-line.

So LIRC is loaded, but it just doesn't want to talk to anyone. As I'm using a homebrew receiver, I'll take a 'scope home tonight and see if anything is actually being generated (ie - if the serial port, ttyS0 is being initialised correctly).

Apart from that, I'm stumped.

Edit: I've just realised, typing this that there are two sleep.d's and scripts from both run at resume. Perhaps I should try the script in the other one - /etc/pm/sleep.d?

Is there an lirc / lircd log that I can look at? I've seen something about running ```
lircd --nodaemon
```, would that help to debug this? How do I do it?

Sorry for all the questions, but I'm a relative Linux noob (four months in and counting).

I haven't attempted to debug it, but I believe my LIRC wigs out as well (MCE based remote, not homebrew).  Suspend/resume isn't something I do...  maybe others have figured this out already.

[INDENT]   Marc[/INDENT]

---

### Post by SiHa on 2008-09-04
OK - For those of you who've come here for an answer. Here's how I finally fixed the problem.
In /**usr/lib/pm-utils** there's a file called '**functions**'. In it are listed all the functions that can be called from the pm-utils scripts.
There are two functions '**modunload**' & '**modreload**'.

The attached script unloads the lirc modules relevant to my setup on suspend and reloads them on resume. I've no idea why simply restarting LIRC or reloading the modules doesn't work but it doesn't.
To check what modules you're using, look in **/etc/.lirc/hardware.conf**

The script also kills and restarts Mythfrontend, otherwise it loses the backend.

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
	suspend|hibernate)
		echo "Suspending..." > /home/frontend/suspend.log
		killall mythfrontend.real
		modunload lirc_serial lirc_dev
		;;

	resume|thaw)
		echo "Resuming..." > /home/frontend/resume.log
		modreload lirc_serial lirc_dev
		mythfrontend &
                ;;
esac
```

And that's magic! System suspends and resumes and the remote works afterwards.

Now all I've got to do is learn how to 'visudo' and add get irexec to suspend from the remote...

Edit: By the way, the script needs to go in **/usr/lib/pm-utils/sleep.d**. The scripts are run in alphanumeric order, so I named mine **00test**, and renamed the existing script **00clear **to **01clear** so that it would get run last on resume. It might not matter when it runs though.

---

### Post by rodercot on 2009-02-22
Hey Siha,
 
 I am just getting into this now and I am testing your script as supplied here. I have added visudo permissions to pm-utils for suspend and hibernate. What I am wondering is I have to unload lirc_dev, lirc_imon and lirc_mceusb2 for modules BUT lirc_imon is also used by lcdproc for the lcd display so before unloading the lirc_imon module I am going to have to kill LCDproc and then start it again on resume, any idea on how to do that.

 rgds,

 Dave

---

### Post by SiHa on 2009-03-17
Hi Dave, 

Sorry for the delay, haven't had much time to spend on this lately - got a new baby!

Anyway, I'd've thought you could just kill and restart the LCDproc process in the same way as mythfrontend.```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
	suspend|hibernate)
		echo "Suspending..." > /home/frontend/suspend.log
		killall mythfrontend.real
                [COLOR="Red"]  killall LCDproc[/COLOR]
		modunload lirc_serial lirc_dev
		;;

	resume|thaw)
		echo "Resuming..." > /home/frontend/resume.log
		modreload lirc_serial lirc_dev
                [COLOR="red"]  LCDproc &[/COLOR]
		mythfrontend &
                ;;
esac
```

Maybe with a ```
sleep 5
```
after the **modreload** line to give the modules a chance to finish loading before LCDproc loads, if it complains.

Don't quote me on this though!

---

### Post by TheKorn2 on 2009-04-20
I, too, have this problem where the remote stops working after a suspend.  I have a MCE USB remote, and receiver.

Through testing, I've found that I don't need to restart lirc; the only thing I need to do is restart the myth frontend.

So I stumbled across this script, and am playing with it.  Can't quite get it working correctly, though.

It kills mythfrontend just fine on a suspend.  But on resume, mythfrontend never launches, and I'm stumped as to why!

```

#!/bin/bash

case "$1" in
suspend|hibernate)
killall mythfrontend.real
;;
resume|thaw)
sleep 10
/usr/bin/mythfrontend &
;;
esac

```

I added the sleep 10 because it takes a minute for gigE to autoconfigure after a sleep, and if mythfrontend were to come up before gig was up, it wouldn't be able to find the back end.

What happens is that the system comes up with a black screen, I can do a ten-count, then the desktop reappears.  So the sleep 10 IS running.  (If I remark it out, then I don't have to do the ten count; the desktop appears right away.)  But mythfrontend isn't!

I cat'd /var/log/pm-suspend.log, and here's what's at the end:

```

(zenity:11921): Gtk-WARNING **: cannot open display: 
(zenity:11925): Gtk-WARNING **: cannot open display: 

```

Can't help but think the two are related.  Problem is I have no idea where to go from here.

Thanks in advance!

---

### Post by SiHa on 2009-04-21
Apparently, one of the biggest problems with suspend / resume and linux is video adaptors not restarting properly. It looks like you may be experiencing this. There are a number of different command-line switches (called 'quirks') that can be used to try and overcome these problems. I can't remember where these are documented, but I have a feeling I found them when looking at the actual pm-suspend script.
I've just googled **pm-suspend quirks **and found quite a lot of stuff, so hopefully there's enough there for you to try them out.

---

### Post by cmcginty on 2011-01-09
Thanks for posting this. The module load/unload did not work for me. You can verify if its working by looking at /dev/lirc0 device. When it doesn't work, it comes back as /dev/lirc1.

There is a full write-up here: [http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake#Fix_the_Lirc_Device_Increment_Bug](http://wiki.xbmc.org/index.php?title=Ubuntu_Suspend_/_Wake#Fix_the_Lirc_Device_Increment_Bug)

The fix for my situation was to stop/start lirc in the script you provided above. Here is my version:

```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
   suspend|hibernate)
      /etc/init.d/lirc stop
      ;;

   resume|thaw)
      /etc/init.d/lirc start
      ;;
esac

```

---

