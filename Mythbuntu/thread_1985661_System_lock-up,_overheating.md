---
title: "System lock-up, overheating?"
date: 2012-05-23
forum: Mythbuntu
---

### Post by ekimseekem on 2012-05-23
Hey everyone,

I'm seeing an intermittent issue where during video playback or even just sitting at the MythTV frontend menu when the system just seems to lock up, I have to force a shutdown and reboot.  The odd thing is, if the system were overheating, I would think it would do it again soon after rebooting, but it continues on chugging after said reboot for quite some time if at all...

I installed a temp monitor and inspected the Nvidia X server settings for temperatures.  The temps don't seem to be anywhere near hot enough to cause the system to crash, they are usually in the mid-40s idling and then maybe mid-50s when playing video, my machine at work is usually in the low 60's and also running Linux with no issue.

What logs should I be looking at to see potential causes, is there any tweaks I should be using?  Here is some additional info:

HTPC:
Acer Aspire x1301
AMD Phenom x2 CPU
4GB of DDR2 RAM
1TB WD Green Drive
PNY NVIDIA GT430 1GB DDR3 (HDMI/DVI) (for reference, the machine at work has a NVIDIA GT220 in it)
OS: Mythbuntu 12.04

Setup: I've used various players (Internal, VLC, currently SMPlayer), all with the same issue.  I have SMPlayer set to use xv video output instead of VDPAU as I find it smoother, should I set the video output setting to something different inside of MythTV, or does it matter when using an external player?

I'm not using any other features of MythTV, I just have a folder full of videos (one being mapped from another computer on the network).

Edit: I also have not seen it lockup while not in the mythfrontend... but I may boot it up when I get home and then leave it at the desktop to see if it happens.

---

### Post by roelforg on 2012-05-23
dmesg and syslog are always good starters.

The /var/log/dmesg.0 is the dmesg from the previous boot.
The /var/log/syslog.1 is the syslog from the prev. boot.

Another thing to try is to TRY to get it to crash (bear with me for a sec here, it'll make sense in a sec), but monitor every aspect of the system and know what it did the moment before it crashed.

---

### Post by ekimseekem on 2012-05-23
> **roelforg said:**
> dmesg and syslog are always good starters.

The /var/log/dmesg.0 is the dmesg from the previous boot.
The /var/log/syslog.1 is the syslog from the prev. boot.

Another thing to try is to TRY to get it to crash (bear with me for a sec here, it'll make sense in a sec), but monitor every aspect of the system and know what it did the moment before it crashed.

That's a good idea, I'll post the logs after the next crash.

I think what I'll do is try to crash it while just playing a video in SMPlayer, outside the frontend.  I'll have a temp window open as well as a couple log files (using tail -f).  If it gets through the whole video, I'll try it with the frontend.

Thanks, I'll post back sometime this evening.

---

### Post by ekimseekem on 2012-05-24
Okay, here are the logs, last 10 lines before a crash:

dmsg:
```

[   11.988167] CIFS VFS: Error connecting to socket. Aborting operation
[   11.988562] CIFS VFS: cifs_mount failed w/return code = -101
[   11.993259] type=1400 audit(1337804976.713:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1081 comm="apparmor_parser"
[   12.000083] type=1400 audit(1337804976.721:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1082 comm="apparmor_parser"
[   12.005875] type=1400 audit(1337804976.725:8): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1082 comm="apparmor_parser"
[   12.006101] type=1400 audit(1337804976.725:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1082 comm="apparmor_parser"
[   12.012268] type=1400 audit(1337804976.733:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/mysqld" pid=1083 comm="apparmor_parser"
[   12.016416] type=1400 audit(1337804976.737:11): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1095 comm="apparmor_parser"
[   12.031207] forcedeth 0000:00:0a.0: irq 41 for MSI/MSI-X
[   12.100557] init: alsa-restore main process (1138) terminated with status 19
```

syslog:
```

May 23 01:09:01 hammie CRON[3619]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
May 23 01:12:11 hammie dbus[841]: [system] Activating service name='org.debian.apt' (using servicehelper)
May 23 01:12:12 hammie AptDaemon: INFO: Initializing daemon
May 23 01:12:12 hammie dbus[841]: [system] Successfully activated service 'org.debian.apt'
May 23 01:16:57 hammie &#65279;AptDaemon: INFO: CommitPackages() was called: dbus.Array([dbus.String(u'asoundconf-gtk')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s')), dbus.Array([dbus.String(u'')], signature=dbus.Signature('s'))
May 23 01:16:57 hammie AptDaemon.Trans: INFO: Queuing transaction /org/debian/apt/transaction/b247e9732f3c445da693f82f66db03db
May 23 01:17:01 hammie CRON[3869]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
May 23 01:17:01 hammie AptDaemon.Worker: INFO: Simulating trans: /org/debian/apt/transaction/b247e9732f3c445da693f82f66db03db
May 23 01:17:01 hammie &#65279;AptDaemon.Worker: INFO: Committing packages: dbus.Array([dbus.String(u'asoundconf-gtk')], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s')), dbus.Array([], signature=dbus.Signature('s'))
May 23 01:17:04 hammie AptDaemon.Worker: INFO: Processing transaction /org/debian/apt/transaction/b247e9732f3c445da693f82f66db03db
```

I also continued to monitor temperature when it crashed, GPU didn't really change much at 48 degrees C, CPU on the other hand was bouncing around a bit between 50 and 53 degrees C.

Edit: I should also add that I'm using alsa 1.9 for the audio output in SMPlayer, I am getting audio, but should I also apply the same setting across the system?  I have noticed I'm not getting audio from the rest of the system (eg. from a chromium window playing a youtube video).  This probably means the system probably has the wrong audio device selected.

---

### Post by nickrout on 2012-05-24
Note that cron did it's hourly run just before the crash, maybe it ran something that triggered a crash, or overstressed the power supply, or overheated the CPU.

If it's a hardware problem, the power supply is the first culprit to try. Can you replace it?

---

### Post by ekimseekem on 2012-05-25
> **nickrout said:**
> Note that cron did it's hourly run just before the crash, maybe it ran something that triggered a crash, or overstressed the power supply, or overheated the CPU.

If it's a hardware problem, the power supply is the first culprit to try. Can you replace it?

I will check out the cron jobs this evening...

The power supply seems to be custom for the case, it likely is only available from Acer directly, although I could rig something up with a standard power supply in a pinch...

Last night was fairly cool and I had some windows open, we didn't have an issue with the machine all night playing a movie.  So, I decided to do the ultimate test; I grabbed my wife's hair dryer, plugged it in and pointed it at the CPU (the CPU has a fairly open vent over top it), I watched the temp climb steadily until 55 degrees C and it crashed in exactly the same manner (I was playing a video at the same time).  Now I had observed that the temp hovered in the low 50's for the CPU and everything seemed fine, but I'm guessing something triggers it to go over the top and therefore overheats before I can see the final temperature.  I find this a bit odd that its crashing at just 55, I've seen other CPU's get marginally hotter then that and continue to work... maybe my CPU has a weak back...

I'll look into cron jobs to find out if anything is running that might cause it... I'm also thinking about getting a better CPU cooler, [maybe this]("http://www.newegg.ca/Product/Product.aspx?Item=N82E16835186035").

---

### Post by nickrout on 2012-05-26
May be as simple as blowing out dust, or reseating the cpu cooler with new thermal grease stuff.

---

### Post by ekimseekem on 2012-05-27
> **nickrout said:**
> May be as simple as blowing out dust, or reseating the cpu cooler with new thermal grease stuff.

Yea I did both these things already, to no avail.

As for cron jobs, not much in the hourly one, most are configured to run daily.  Is there a way to run set of cron jobs manually so that I can troubleshoot?

---

### Post by nickrout on 2012-05-27
> **ekimseekem said:**
> Yea I did both these things already, to no avail.

As for cron jobs, not much in the hourly one, most are configured to run daily.  Is there a way to run set of cron jobs manually so that I can troubleshoot?

The files in /etc/cron.hourly/ are all executable, simply run them.

---

### Post by The Toastcutter on 2012-05-28
Apart from the lockups, there's no indication that overheating is the actual problem is there?

Maybe try booting into memtest86+ and let that run for a while?

---

### Post by nickrout on 2012-05-28
Good point - as the system works harder, the RAM fills up and if there is an error it may only be apparent when the system gets busy.

---

