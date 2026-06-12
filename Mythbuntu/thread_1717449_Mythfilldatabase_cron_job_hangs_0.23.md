---
title: "Mythfilldatabase cron job hangs 0.23"
date: 2011-03-29
forum: Mythbuntu
---

### Post by 8link on 2011-03-29
Hello all,

I've had a problem with mythfilldatabase hanging for the last few months.  I've searched over many boards and while I've seen mention of problems very similar to this I have not been able to locate a fix.

If I manually run mythfilldatabase, it completes normally, closes normally, and updates all listing information as designed.

The automated mythfilldatabase job runs under the correct user but hangs indefinitely and prevents the update of listing data.  I have been manually killing the two mythfilldatabase instances and manually running it in order to update listing info.

Does anyone have any ideas?  

I'm happy to provide more information.

Thanks,

8

Mythbackend version information.  
```
mythbackend --version
Please include all output in bug reports.
MythTV Version   : 24158
MythTV Branch    : branches/release-0-23-fixes
Network Protocol : 56
Library API      : 0.23.20100314-1
QT Version       : 4.6.2
Options compiled in:
 linux debug using_oss using_alsa using_pulse using_jack using_pulseoutput using_backend using_dvb using_firewire using_frontend using_glx_proc_addr_arb using_hdhomerun using_hdpvr using_iptv using_ivtv using_joystick_menu using_libudev using_lirc using_mheg using_opengl_video using_opengl_vsync using_qtdbus using_qtwebkit using_v4l using_x11 using_xrandr using_xv using_xvmc using_xvmc_vld using_xvmcw using_bindings_perl using_bindings_python using_opengl using_vdpau using_ffmpeg_threads using_libavc_5_3 using_live using_mheg

```ps aux output of hung mythfilldatabase processes.
```
mythtv    2229  0.0  0.0   1832   492 ?        S    Feb16   0:00 sh -c /usr/bin/mythfilldatabase 
mythtv    2230  0.0  0.5  96180 21232 ?        SNl  Feb16   0:22 /usr/bin/mythfilldatabase

```Mythbackend log.
```

booze@mythic:~$ tail /var/log/mythtv/mythbackend.log
2011-03-29 21:18:04.284 mythfilldatabase still running, skipping checks.
2011-03-29 21:23:07.310 mythfilldatabase still running, skipping checks.
2011-03-29 21:25:39.170 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-29 21:28:10.335 mythfilldatabase still running, skipping checks.
2011-03-29 21:33:14.368 mythfilldatabase still running, skipping checks.
2011-03-29 21:36:50.344 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/video:
2011-03-29 21:36:50.414 UPnpMedia: BuildMediaMap Done. Found 90 objects
2011-03-29 21:38:19.401 mythfilldatabase still running, skipping checks.
2011-03-29 21:40:39.262 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2011-03-29 21:43:23.433 mythfilldatabase still running, skipping checks.

```

---

### Post by nickrout on 2011-03-30
are you really running it via cron? or is mythbackend firing it off automatically?

---

### Post by 8link on 2011-03-30
Mythbackend is firing off automatically.  

I'll edit the subject.  Apologizes for the confusion.

---

### Post by azmyth on 2011-03-30
I ran into this problem as well. I'd go to view the guide data and there wouldn't be any due to a hanging and still running mythfdb from 14 days ago. I never figured out what was causing the problem as it would happen every so often. I ended up adding a cron job to killall mythfdb each morning about an hour after the latest time set to run through the setup. I figure if it hasn't completed in an hour it has hung. I've been doing this for about a year and I haven't seen any issues.

---

### Post by klc5555 on 2011-03-30
If mythfilldatabase completes successfully when run as the main user, but not from mythtv, you might want to try setting up a crontab under your primary user's credentials and running the mythfilldatabase command daily (or at a specified time) that way. I've tended to run the mildly resource-intensive mythfilldatabase from cron for years, since I personally found it easier to integrate it that way with all the other mildly resource-intensive, but non-mythtv stuff my machine was doing routinely via cron.

Cron options as per the Ubuntu manpages for crontab here: [http://manpages.ubuntu.com/manpages/maverick/man1/crontab.1.html](http://manpages.ubuntu.com/manpages/maverick/man1/crontab.1.html)
and formatting the commands in the file here: [http://manpages.ubuntu.com/manpages/maverick/man5/crontab.5.html](http://manpages.ubuntu.com/manpages/maverick/man5/crontab.5.html)

---

### Post by 8link on 2011-03-30
If I manually run mythfdb using the mythtv user is completes correctly.  It only seems to fail when run from the built-in automatic mythbackend mythfdb.

It sounds like the consensus is not to use the built-in mythbackend functionality and go back to a manual cron job.  I know the built-in worked correctly in the past.  Annoying that the built-in won't do what it's supposed to any longer.  But it's likely easier to use a manually entered cron job than to chase the built-in bugs.

Thanks for the input!

---

### Post by 8link on 2011-04-01
Disabling the auto mythbackend mythtfdb and creating a crontab to run mythfdb has been working great for the last few days.  

Thanks everyone.

---

