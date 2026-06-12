---
title: "Limit MythFrontEnd to a single instance?"
date: 2008-11-06
forum: Mythbuntu
---

### Post by hozhead on 2008-11-06
Is there a way to limit the MythFrontEnd to a single running instance?

I don't have a keyboard or mouse hooked to my HTPC but I do have a button programmed on my remote to start the MythFrontEnd (in case I close it for some reason) and the button has been bumped a few times which then results in multiple instances running at once.  Naturally the instances aren't in perfect sync and so there's an audio echo from multiple instances playing at once and it also adds a load to the system.

---

### Post by SiHa on 2008-11-07
You could have irexec run a script that simply checks if Mythfrontend is already running, and only starts it if not.

```
#!/bin/bash
#
#This script will start Myth only if it's not already running...
#
(ps -A |grep mythfrontend) > null
if [ $? = 0 ];
then
echo Mythfrontend already running
else
echo Mythfrontend not running, starting...
mythfrontend &
fi
```

I wrote this script, called it restart, saved it to /usr/sbin, and made it world executable:```
chmod 777 restart
```.

Just point the relevant line in your lircrc to this script instead of directly to Mythfrontend, and you should be set.

HTH

Simon

---

### Post by hozhead on 2008-11-09
Thanks, that got me going. I did use a script, located in /usr/local/bin to handle the issue.  I pointed my irexec command to the script (after making it executable) and all is well.



#!/bin/bash

# script taken from [http://www.pvrweb.com/bbs/lofiversion/index.php/t4398.html](http://www.pvrweb.com/bbs/lofiversion/index.php/t4398.html)

# Test to see if process is running first
if ps -ef|grep -v grep|grep mythfrontend
then
# Do nothing
echo "mythfrontend found"
else
# Startup frontend
mythfrontend &
fi
exit

---

### Post by laffinet on 2008-11-28
Hm. I did exactly what you did using your script but pressing the button again starts another mythfrontend. 

How can I stop this from happening ??

---

### Post by laffinet on 2008-11-30
bump.

---

### Post by SiHa on 2008-12-01
> Hm. I did exactly what you did using your script but pressing the button again starts another mythfrontend. 


Well it bl00dy shouldn't!

Can you post: 
The contents of the script.
The output from 'ps -A' or 'ps -ef' when mythfrontend is running, depending on which of the above you are using (mine isn't as elegant, but both should work). I prefer to use -A, as you don't have to filter out the 'grep' process from the results.
The lircrc entry for this. - probably irrelevant, but you never know,

Simon

---

### Post by laffinet on 2008-12-01
I know it shouldn't but it sure does.

Here's the script (I called it runmyth)
```
#!/bin/bash
#
#This script will start Myth only if it's not already running...
#
(ps -A |grep mythfrontend) > null
if [ $? = 0 ];
then
echo Mythfrontend already running
else
echo Mythfrontend not running, starting...
mythfrontend &
fi
```

ps -A

```
ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:03 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:05 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:12 events/0
   10 ?        00:00:10 events/1
   11 ?        00:00:00 khelper
   51 ?        00:00:00 kintegrityd/0
   52 ?        00:00:00 kintegrityd/1
   54 ?        00:00:00 kblockd/0
   55 ?        00:00:00 kblockd/1
   57 ?        00:00:00 kacpid
   58 ?        00:00:00 kacpi_notify
  162 ?        00:00:00 cqueue
  166 ?        00:00:00 kseriod
  211 ?        00:00:00 pdflush
  212 ?        00:00:06 pdflush
  213 ?        00:00:17 kswapd0
  255 ?        00:00:00 aio/0
  256 ?        00:00:00 aio/1
 1201 ?        00:00:00 ksuspend_usbd
 1202 ?        00:00:00 khubd
 1240 ?        00:00:00 ata/0
 1241 ?        00:00:00 ata/1
 1242 ?        00:00:00 ata_aux
 2028 ?        00:00:00 scsi_eh_0
 2030 ?        00:00:00 scsi_eh_1
 2058 ?        00:00:00 scsi_eh_2
 2059 ?        00:00:18 scsi_eh_3
 2060 ?        00:00:00 scsi_eh_4
 2061 ?        00:00:00 scsi_eh_5
 2267 ?        00:00:00 kjournald
 2420 ?        00:00:00 udevd
 2661 ?        00:00:00 kpsmoused
 3435 ?        00:00:00 cx88 tvaudio
 3518 ?        00:00:16 rt61pci
 3886 ?        00:00:01 lircd
 4740 ?        00:00:00 xfs_mru_cache
 4744 ?        00:00:00 xfslogd/0
 4748 ?        00:00:00 xfslogd/1
 4749 ?        00:00:00 xfsdatad/0
 4750 ?        00:00:04 xfsdatad/1
 4751 ?        00:00:00 xfsbufd
 4756 ?        00:00:00 xfsaild
 4757 ?        00:00:00 xfssyncd
 4914 ?        00:00:00 portmap
 4936 ?        00:00:00 rpc.statd
 4944 ?        00:00:00 rpciod/0
 4945 ?        00:00:00 rpciod/1
 4955 ?        00:00:00 nfsiod
 4963 ?        00:00:00 rpc.idmapd
 5083 tty4     00:00:00 getty
 5084 tty5     00:00:00 getty
 5089 tty2     00:00:00 getty
 5090 tty3     00:00:00 getty
 5091 tty6     00:00:00 getty
 5263 ?        00:00:00 acpid
 5315 ?        00:00:00 kondemand/0
 5317 ?        00:00:00 kondemand/1
 5383 ?        00:00:00 syslogd
 5436 ?        00:00:00 dd
 5438 ?        00:00:00 klogd
 5461 ?        00:00:03 dbus-daemon
 5483 ?        00:00:00 avahi-daemon
 5484 ?        00:00:00 avahi-daemon
 5514 ?        00:00:00 sshd
 5557 ?        00:00:01 apache2
 5591 ?        00:00:00 cupsd
 5593 ?        00:00:00 apache2
 5594 ?        00:00:00 apache2
 5595 ?        00:00:00 apache2
 5596 ?        00:00:00 apache2
 5597 ?        00:00:00 apache2
 5729 ?        00:00:00 mysqld_safe
 5771 ?        00:01:47 mysqld
 5772 ?        00:00:00 logger
 5903 ?        00:02:19 mythbackend
 6006 ?        00:00:00 lockd
 6010 ?        00:00:00 nfsd4
 6011 ?        00:00:00 nfsd
 6012 ?        00:00:00 nfsd
 6013 ?        00:00:00 nfsd
 6014 ?        00:00:00 nfsd
 6015 ?        00:00:00 nfsd
 6016 ?        00:00:00 nfsd
 6017 ?        00:00:00 nfsd
 6018 ?        00:00:00 nfsd
 6029 ?        00:00:00 rpc.mountd
 6041 ?        00:00:38 kdvb-fe-0
 6128 ?        00:00:03 hald
 6131 ?        00:00:00 console-kit-dae
 6132 ?        00:00:00 hald-runner
 6214 ?        00:06:29 hald-addon-usb-
 6215 ?        00:00:00 hald-addon-inpu
 6228 ?        00:00:00 hald-addon-cpuf
 6229 ?        00:00:00 hald-addon-acpi
 6259 ?        00:00:09 hald-addon-stor
 6292 ?        00:00:00 bluetoothd
 6301 ?        00:00:00 btaddconn
 6303 ?        00:00:00 btdelconn
 6314 ?        00:00:00 krfcommd
 6352 ?        00:00:05 NetworkManager
 6362 ?        00:00:00 wpa_supplicant
 6366 ?        00:00:00 nm-system-setti
 6390 ?        00:00:00 gdm
 6392 ?        00:00:00 gdm
 6398 tty7     00:04:21 Xorg
 6418 ?        00:00:00 system-tools-ba
 6435 ?        00:00:11 powernowd
 6488 ?        00:00:00 atd
 6518 ?        00:00:00 cron
 6568 tty1     00:00:00 getty
 6592 ?        00:00:00 sh
 6648 ?        00:00:00 ssh-agent
 6651 ?        00:00:00 dbus-launch
 6652 ?        00:00:04 dbus-daemon
 6657 ?        00:01:29 mtd
 6666 ?        00:00:00 irexec
 6668 ?        00:00:35 x11vnc
 6678 ?        00:00:00 xfce4-session
 6683 ?        00:00:00 gconfd-2
 6684 ?        00:00:41 gnome-screensav
 6685 ?        00:00:00 xfce-mcs-manage
 6687 ?        00:00:00 gnome-keyring-d
 6688 ?        00:00:00 xfwm4
 6690 ?        00:00:00 Thunar
 6692 ?        00:00:00 gam_server
 6693 ?        00:00:05 xfdesktop
 6696 ?        00:00:01 xfce4-panel
 6697 ?        00:00:02 update-notifier
 6698 ?        00:00:03 xfce4-menu-plug
 6700 ?        00:00:02 gnome-power-man
 6702 ?        00:00:00 irexec
 6722 ?        00:00:04 nm-applet
 6765 ?        00:00:01 notification-da
 8182 ?        00:00:00 dhclient
 8299 ?        00:00:02 ntpd
18381 ?        00:00:00 sshd
18388 ?        00:00:00 sshd
18391 pts/0    00:00:00 bash
18414 pts/0    00:00:00 dbus-launch
18415 ?        00:00:00 dbus-daemon
18417 ?        00:00:00 gconfd-2
18431 pts/0    00:00:00 dbus-launch
18432 ?        00:00:00 dbus-daemon
18532 ?        00:00:14 mythfrontend.re
18609 pts/0    00:00:00 ps

```

lirc entry

```
begin
prog = irexec
button = red
config = ~/runmyth &
end
```

---

### Post by SiHa on 2008-12-02
Umm...:oops:

I think I've shown my lack of bash scripting prowess here.

The line```
(ps -A |grep mythfrontend) > null
```
should, in fact be ```
(ps -A |grep mythfrontend) > /dev/null
```

to properly redirect to the output to the 'null' device (so that it's not echo'ed to stdout). My original line simply redirects it to the file 'null' in the same directory as the script.

As your script is located in your home directory, if irexec is not run as you, but as mythtv (probably) it lacks the permissions to create this file, so the line will return an error - exit code '1', which is tested ($?) in the next line.

Taking a leaf out of hozhead's book, to neaten things up you could change it to:

```
#!/bin/bash
#
#This script will start Myth only if it's not already running...
#
if ps -A|grep mythfrontend > /dev/null
then
echo Mythfrontend already running
else
echo Mythfrontend not running, starting...
mythfrontend &
fi
```

That should work.

---

### Post by laffinet on 2008-12-03
Thanks.

Will give this a try tonight and report back here.

---

### Post by laffinet on 2008-12-04
That did the trick, thank you.

Still one small issue: the button to restart mythfrontend sometimes seems to register twice, resulting in 2 instances being started. I guess this is still possible because the 2 mythfrontends start that soon after each other that ps... doesn't show the first instance yet. No idea how to get around that...

---

### Post by funkydan2 on 2008-12-04
This probably won't fix the problem of having mythfrontend start twice, but my 'myth restart' script is designed to kill any existing mythfrontend processes, and then start the frontend.

```

#!/bin/sh
MYTHEXISTS=`/bin/ps -e | grep mythfrontend | grep -v grep | awk '{print $1}'`;

if [ "$MYTHEXISTS" != "" ]; then
        for MYTHPROCESS in `/bin/ps -e | grep mythfrontend | grep -v grep | awk '{print $1}'`
        do
                echo $MYTHPROCESS;
                kill -9 $MYTHPROCESS;
        done
fi 

DISPLAY=:0 mythfrontend &

```

The reaosn I've gone for this is that on the odd occasion, I find that the frontend crashes to a black screen and this script (which I've linked to the 'power' button on my remote) restarts the frontend - perfect for the WAF.

---

### Post by SiHa on 2008-12-04
You could try adding```
sleep 5
``` to the beginning of the script, before the **if** statement. That way, if it accidentally runs twice, the Mythfrontend process should have started properly before the the script gets past the **sleep** for the second time.

---

### Post by funkydan2 on 2008-12-04
Also, do you have 'repeat = 0' in the lircrc definition for your power button?  This would mean that if you hold down the button, it will only send 1 message to irexec rather than continually sending messages (thus you'd have to press the button twice in order to accidentally start two processes).

---

### Post by laffinet on 2008-12-04
> **funkydan2 said:**
> Also, do you have 'repeat = 0' in the lircrc definition for your power button?  This would mean that if you hold down the button, it will only send 1 message to irexec rather than continually sending messages (thus you'd have to press the button twice in order to accidentally start two processes).

I don't. Will try that tonight.

---

### Post by SiHa on 2008-12-05
> **funkydan2 said:**
> Also, do you have 'repeat = 0' 

Good point

---

### Post by uncle hammy on 2008-12-11
I am going to tag onto this thread.

I have the above restart script working, and ~/.lircrc modified to run it when the power button is pressed.  If I manually start irexec, it works perfectly.  However, so far I have been unable to get irexec to start automatically at boot up.

I create a script /etc/init.d/start-irexec and ./start-irexec start works fine; irexec starts right up.  ./start-irexec stop shuts it down correctly.
```

#!/bin/sh

start_irexec() {
 /usr/bin/irexec -d   </dev/null  >/dev/null 2>&1 &
 echo Starting irexec
}

stop_irexec() {
 echo Stopping irexec
 killall -9 irexec
}

restart_irexec() {
  stop_irexec
  sleep 3
  start_irexec
}


case "$1" in
  'start')
    start_irexec
    ;;
  'stop')
    stop_irexec
    ;;
  'restart')
    restart_irexec
    ;;
  *)
    echo "usage $0 start|stop|restart" ;;
    esac
exit 0

```
Then, I did an update-rc.d start-irexec defaults and all the simlinks got created fine.  However, after booting, pgrep irexec (and the fact my power button isn't working) is revealing that irexec is not getting started.

Can anyone help me get irexec running at start up?

Thanks,
Scott

---

### Post by newlinux on 2008-12-11
seems that should work. Are you running gnome? In gnome I've just put irexec to be started with the session manager (Preferences->Session). But I have other scripts that need root priveleges started exactly the way you describe doing this script.

Maybe starting irexec as root is the problem (don't know why it would stop running though). Maybe as root it looks in the root folder for .lircrc

---

### Post by uncle hammy on 2008-12-12
Thansk for the reply newlinux.  I'm using just a default installation of Mythbuntu 8.04, so I believe is XFCE that's being used...I have no session manager that I have been able to find.  

ian dobson was kind enough to point me down the road to using this approach here [http://ubuntuforums.org/showthread.php?p=6268043#post6268043](http://ubuntuforums.org/showthread.php?p=6268043#post6268043) and it works perfectly for that application, so I just assumed it should work for this one.  The other thing that has me confused is the fact that I can run the init.d script manually (./start-irexec start) and it works, irexec runs.  So it appears to be the start up procedure that's the issue.

---

### Post by SiHa on 2008-12-12
Now it's a while since I setup irexec, but I *think* this is to do with the user that starts irexec, and where it looks for the relevant lircrc file.

Unless told otherwise, it looks in your home directory for the lircrc, so if you run it from a terminal it looks in the right place, if it runs at startup it looks somewhere else.

I can't remember the syntax, but I think if you specify the full path to your lircrc in the commandline, it will work. If I get a chance over the weekend, I'll have a looksee what I did and post it back here.

---

### Post by uncle hammy on 2008-12-12
So, will irexec not launch, or shut down if it doesn't find a lircrc file?  

I'm at work now, but tonight I will try modifying my /etc/init.d/start-irexec script and give it the path to the lircrc file in for my auto login user....
```

#!/bin/sh

start_irexec() {
 /usr/bin/irexec -d [COLOR="Red"]/home/myuser/.lircrc[/COLOR]  </dev/null  >/dev/null 2>&1 &
 echo Starting irexec
}

```
I may also try having the script output "attempting to start irexec" to a log file.  That way at least I can tell if it's trying to do it's thing, or if it seems to be getting by-passed altogether.

---

### Post by SiHa on 2008-12-12
That should work.

This is my **/etc/rc.local**```
frontend@frontend-desktop:/etc$ cat rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

irexec /home/frontend/.lircrc

exit 0

```
I suppose, I should really have it check the exit status of irexec, and make sure it passes the correct status back, but I've never had any problems.

Extract from the irexec manpages:
>        -d --daemon
              run in background
 ...

OPTIONS
       If you add the --daemon option irexec will fork to background. That way
       you  can  easily  start  irexec  from  an init script. In this case you
       should specify a config file on the command line  as  irexec  won’t  be
       able  to find your home directory. 



Note the lack of the **-d** in my script. I can't remember where I found this, but it seems that if you run it from an init script the -d causes problems. I know these two ideas seem to conflict but, for me, it's what worked.

NB, If you're going to try this, don't forget to set the execute bits so that rc.local will run.

This frontend any gets rebooted about once a month, the rest of the time it's just suspend / restart, and I've never had a problem where I need to restart irexec. The only thing I've found is that if you make a change to the lircrc, irexec quits. Once in use without tinkering, it appears stable.

HTH

Simon

---

### Post by uncle hammy on 2008-12-12
> **SiHa said:**
> NB, If you're going to try this, don't forget to set the execute bits so that rc.local will run.
What do you mean?  Set the execute bit on what, rc.local?  As in chmod +x /etc/rc.local?

---

### Post by SiHa on 2008-12-12
Yes, sorry.

---

### Post by uncle hammy on 2008-12-12
Ok, this is really driving me to drink!

I modified my /etc/init.d script to echo out to a log file and I included the path to the .lircrc file.  No dice, my log file indicated that the script ran, but irexec was not running.  I removed the -d, placed a copy of the .lircrc file in every user's home directory, and tried every combination there-of, nothing will get it going.

Next, I abondoned the /etc/init.d script altogether and moved to /etc/rc.local.  I added "irexec /home/user/.lircrc both with and without the -d.  I also added an echo to a log file to make sure it was running, and set the executable bit.  Again, no dice.  The log file shows it ran, however irexec is not running.

I've even tried adding "@reboot /usr/bin/irexec -d /home/user/.lircrc" to crontab using crontab -e.

I can't believe it's so hard to get this thing going at start up. :confused:

---

### Post by uncle hammy on 2008-12-17
Well, for what it's worth, I finally got it going.  I ended using Synaptic to install xfce-mcs-plugins-extra, which added some items to Applications>Settings>Settings Manager.  One of those items included the "Autostarted Apps" applet.  

In there, I added a new item the command I used was "/usr/bin/irexec -d /home/MYUSER/.lircrc", and it now starts when xfce is loaded.

---

### Post by laffinet on 2009-02-27
I recently changed my setup and am starting the frontend a lot more via a button on the remote. However, it very frequently starts two instances of the frontend, which is very annoying. Here's the startup script

```
#!/bin/bash
#
#This script will start Myth only if it's not already running...
#
if ps -A|grep mythfrontend > /dev/null
then
echo Mythfrontend already running
else
echo Mythfrontend not running, starting...
mythfrontend &
fi
```

Here's the entry in my lirc
```
begin
remote = mceusb
button = green
prog = irexec
repeat = 0
config = ~/runmyth &
end
```

The script works fine as it prevents a second frontend to be started if one is already running. However, about 50% of the time I press the button without the frontend running two instances are started simultaneously. Any ideas ?

---

### Post by newlinux on 2009-02-27
> **laffinet said:**
> I recently changed my setup and am starting the frontend a lot more via a button on the remote. However, it very frequently starts two instances of the frontend, which is very annoying. Here's the startup script

```
#!/bin/bash
#
#This script will start Myth only if it's not already running...
#
[COLOR="Red"]sleep 1[/COLOR]
if ps -A|grep mythfrontend > /dev/null
then
echo Mythfrontend already running
else
echo Mythfrontend not running, starting...
mythfrontend &
fi
```

Here's the entry in my lirc
```
begin
remote = mceusb
button = green
prog = irexec
repeat = 0
config = ~/runmyth &
end
```

The script works fine as it prevents a second frontend to be started if one is already running. However, about 50% of the time I press the button without the frontend running two instances are started simultaneously. Any ideas ?

Sounds like your button is getting repeated, and two are running before the process is found by ps. In my startup script I added a sleep command at the beginning to prevent this (see in red above). I use sleep 1, but you may need to sleep longer (maybe 2).

---

### Post by laffinet on 2009-02-27
> **newlinux said:**
> Sounds like your button is getting repeated, and two are running before the process is found by ps. In my startup script I added a sleep command at the beginning to prevent this (see in red above). I use sleep 1, but you may need to sleep longer (maybe 2).

Tried that (sleep 10), doesn't change a thing:(

The 2 frontend instances get started pretty much at the same time (if I watch closely I can just see that the progress bars for scaling icons etc. appears twice, almost not noticable). So there's (almost) no delay between the first and the second one starting.

---

### Post by laffinet on 2009-03-07
One thing I noticed is that if I run irw and press a button on the remote it sometimes registers once, sometimes twice, eg:

Code:

 irw
000000037ff07ba3 00 Green mceusb

and

Code:

irw
000000037ff07ba3 00 Green mceusb
000000037ff07ba3 01 Green mceusb

So I guess the button gets registered twice sometimes. No idea how to stop that, though.
I already have the line "repeat = 0" in my mythtv lirc file, however that didn't change a thing.

Any ideas ?

---

### Post by newlinux on 2009-03-07
> **laffinet said:**
> Tried that (sleep 10), doesn't change a thing:(

The 2 frontend instances get started pretty much at the same time (if I watch closely I can just see that the progress bars for scaling icons etc. appears twice, almost not noticable). So there's (almost) no delay between the first and the second one starting.

That's still strange--when you have sleep 10 in there they still start up quickly - meaning before 10 seconds have passed? 

The irw output is what happens with me, I think it may not be directly related to how often a button is repeated when read by LIRC because I have many buttons that do that with irw but they don't repeat when I use them in LIRC applications. For instance "play" does this and my playback doesn't play/pause/play/pause with each press (because play is a play/pause toggle). So it is only getting the button once.

---

### Post by SiHa on 2009-03-08
Just a thought, but I don't have a '&' at the end of my config line.

```
begin
    remote = lircd.conf
    prog = irexec
    button = Blue
    config = sudo /usr/sbin/Mythrestart
    repeat = 0
    delay = 0
end

```

---

### Post by laffinet on 2009-03-08
> **newlinux said:**
> That's still strange--when you have sleep 10 in there they still start up quickly - meaning before 10 seconds have passed? 


No, with sleep 10 there is a considerable delay between pressing the button and the frontend starting. If 2 start there's the delay and then both start almost simultaneously.

---

### Post by laffinet on 2009-03-08
> **SiHa said:**
> Just a thought, but I don't have a '&' at the end of my config line.

Yeah, thought that too, tried both, with and without the & and it doesn't change a thing.

---

### Post by newlinux on 2009-03-09
Do you have this repeating problem with other buttons in LIRC? Seems odd it would spawn off both at exactly the same time, but not for other LIRC events. If it doesn't do this with other buttons, are  you sure you don't have 2 irexec's running?

---

### Post by laffinet on 2009-03-11
Looks like that's it. Just checked via 'ps -ef |grep irexec' and got the following result:

```
laffi     6287     1  0 16:00 ?        00:00:00 irexec -d
laffi     6323     1  0 16:00 ?        00:00:00 irexec
```

Went into Settings -> Settings Manager -> Autostart applications, unticked 'Infrared' and things are working fine now. Fantastic. 
Don't know how and why the second irexec got started but this fixed my problem. Thank you very much !

---

### Post by roazena on 2009-03-30
I would rather do this as a global feature (*i.e.*, any command that starts the frontend has to go through the check step first) rather than tie it to a keypress or button script. Unless the developers can give me a real good reason why one box should have multiple frontends running on it, mythfrontend should obey the same rule Firefox does.

What I don't know is whether the 'mythfrontend' command is a script which can be patched to run the check, or a binary.

I'll probably file a bug on launchpad or something.

---

