---
title: "Mythtv backend won't start after 9.10 upgrade"
date: 2009-11-01
forum: Mythbuntu
---

### Post by Mephi on 2009-11-01
Hi guys,

I've got a seperate backend/frontend setup, and I've upgrades my ubuntu-server based backend to 9.10, and now I can't start the mythtv-backend service.

I've tried both:
sudo service mythtv-backend start
and
sudo /etc/init.d/mythtv-backend start

and they both give a message like:
mythtv-backend start/running, process 25549

But it never starts the process.

However, if I run:
sudo mythbackend

Then it seems to work fine, just not as a service. So at the moment I have it running in a seperate terminal through screen.

mythbackend.log shows nothing, then only logfile that is showing anything is syslog which just shows:
Nov  1 16:11:47 home init: mythtv-backend main process (27307) terminated with status 1
Nov  1 16:11:47 home init: mythtv-backend main process ended, respawning
Nov  1 16:11:47 home init: mythtv-backend main process (27323) terminated with status 1
Nov  1 16:11:47 home init: mythtv-backend main process ended, respawning
Nov  1 16:11:47 home init: mythtv-backend main process (27339) terminated with status 1
Nov  1 16:11:47 home init: mythtv-backend main process ended, respawning
Nov  1 16:11:47 home init: mythtv-backend main process (27355) terminated with status 1
Nov  1 16:11:47 home init: mythtv-backend main process ended, respawning
Nov  1 16:11:47 home init: mythtv-backend main process (27372) terminated with status 1
Nov  1 16:11:47 home init: mythtv-backend respawning too fast, stopped

Which isn't much help...

Any ideas?

Cheers,

Matt

Any ideas what's wrong?

---

### Post by jt_04 on 2009-11-01
I'm having the same problem.  I did notice during the 9.10 upgrade that it said it was going to remove package "mythtv-backend", and i thought, wow, that's a strange thing to do.  but now, sure enough, when i type "dpkg --get-selections|grep backend", it says "mythtv-backend  deinstall".

i'm a little hesitant to reinstall the backend in case i lose my entire mythtv configuration, but i'm not sure what else to do.

---

### Post by Mephi on 2009-11-01
When it's running I've got access to all my old recordings, and it's remembered all the upcoming recordings too. I did have to setup the tuners and channels again though.

It's just that getting it running that's the problem... ;)

Matt

---

### Post by jt_04 on 2009-11-02
yes, i have the same situation.  i just can't watch tv without the backend running.  have you tried re-installing the backend?  i'm a little apprehensive of doing that

---

### Post by Lido on 2009-11-03
Just did the upgrade to 9.10 and MythTV isn't working for me either. I can't find the error for the backend in my log files. The backend config program is no longer in my system/administration menu either.

This is all the myth info I can see in /var/log/messages:
```
Nov  2 23:41:57 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:41:58 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:01 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:02 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:02 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:52 MythTV-LR kernel: [  547.640129] mythfrontend.re[2691]: segfault at a1 ip 00007f850d0bcad5 sp 00007fff16cdcb80 error 4 in libqt-mt.so.3.3.8[7f850ca98000+808000]
Nov  2 23:46:56 MythTV-LR kernel: [  791.727093] mythfrontend.re[2939]: segfault at a1 ip 00007f8edf6eead5 sp 00007fffc48cf760 error 4 in libqt-mt.so.3.3.8[7f8edf0ca000+808000]
Nov  2 23:47:06 MythTV-LR kernel: [  801.168256] mythfrontend.re[2970]: segfault at a1 ip 00007f5a106b6ad5 sp 00007fff5b03e4b0 error 4 in libqt-mt.so.3.3.8[7f5a10092000+808000]
Nov  2 23:59:06 MythTV-LR kernel: [ 1521.197568] mythfrontend.re[3091]: segfault at a1 ip 00007f1e4a6d6ad5 sp 00007fff46f1b300 error 4 in libqt-mt.so.3.3.8[7f1e4a0b2000+808000]

```

---

### Post by madverb on 2009-11-04
Yeah, this happened to me also. I just reinstalled the backend. Everything came up fine afterwards.
My problem is that the backend now doesn't start on boot. I have to manually start it.

---

### Post by jyavenard on 2009-11-04
> **Lido said:**
> Just did the upgrade to 9.10 and MythTV isn't working for me either. I can't find the error for the backend in my log files. The backend config program is no longer in my system/administration menu either.

This is all the myth info I can see in /var/log/messages:
```
Nov  2 23:41:57 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:41:58 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:01 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:02 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:02 MythTV-LR pulseaudio[2310]: sink-input.c: Failed to create sink input: sink is suspended.
Nov  2 23:42:52 MythTV-LR kernel: [  547.640129] mythfrontend.re[2691]: segfault at a1 ip 00007f850d0bcad5 sp 00007fff16cdcb80 error 4 in libqt-mt.so.3.3.8[7f850ca98000+808000]
Nov  2 23:46:56 MythTV-LR kernel: [  791.727093] mythfrontend.re[2939]: segfault at a1 ip 00007f8edf6eead5 sp 00007fffc48cf760 error 4 in libqt-mt.so.3.3.8[7f8edf0ca000+808000]
Nov  2 23:47:06 MythTV-LR kernel: [  801.168256] mythfrontend.re[2970]: segfault at a1 ip 00007f5a106b6ad5 sp 00007fff5b03e4b0 error 4 in libqt-mt.so.3.3.8[7f5a10092000+808000]
Nov  2 23:59:06 MythTV-LR kernel: [ 1521.197568] mythfrontend.re[3091]: segfault at a1 ip 00007f1e4a6d6ad5 sp 00007fff46f1b300 error 4 in libqt-mt.so.3.3.8[7f1e4a0b2000+808000]

```

You're running the wrong Qt ... are you sure this is 0.22 ?

Qt 3 is only used for mythtv 0.21

---

### Post by Mephi on 2009-11-04
Yeah, that looks like a different issue to mine, I get nothing in /var/log/messages

This really has got me stumped, anyone got any ideas?

Cheers,

Matt

---

### Post by Mephi on 2009-11-04
I don't know if it'll provide any usefull info, but when I run sudo mythbackend I get this:

```
2009-11-04 19:32:45.279 mythbackend version: branches/release-0-22-fixes [22594] www.mythtv.org
2009-11-04 19:32:45.280 Using runtime prefix = /usr
2009-11-04 19:32:45.280 Using configuration directory = /home/mephi/.mythtv
2009-11-04 19:32:45.280 Unable to read configuration file mysql.txt
2009-11-04 19:32:45.280 Empty LocalHostName.
2009-11-04 19:32:45.280 Using localhost value of home.mephi.co.uk
2009-11-04 19:32:45.286 New DB connection, total: 1
2009-11-04 19:32:45.289 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:45.289 Closing DB connection named 'DBManager0'
2009-11-04 19:32:45.290 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:45.294 Current MythTV Schema Version (DBSchemaVer): 1244
2009-11-04 19:32:45.296 MythBackend: Starting up as the master server.
2009-11-04 19:32:45.304 New DB connection, total: 2
2009-11-04 19:32:45.304 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:45.480 New DB connection, total: 3
2009-11-04 19:32:45.481 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:45.482 New DB connection, total: 4
2009-11-04 19:32:45.483 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:46.401 DTVMux, Error: Invalid S2 modulation system parameter '1', aborting.
2009-11-04 19:32:46.402 DVBChan(3:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(1011): Failed to initialize multiplex options
2009-11-04 19:32:46.487 DTVMux, Error: Invalid S2 modulation system parameter '1', aborting.
2009-11-04 19:32:46.487 DVBChan(4:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(1011): Failed to initialize multiplex options
2009-11-04 19:32:46.553 DTVMux, Error: Invalid S2 modulation system parameter '1', aborting.
2009-11-04 19:32:46.553 DVBChan(5:/dev/dvb/adapter1/frontend0) Error: SetChannelByString(1011): Failed to initialize multiplex options
2009-11-04 19:32:46.601 New DB scheduler connection
2009-11-04 19:32:46.601 Connected to database 'mythconverg' at host: localhost
2009-11-04 19:32:46.643 Enabling Upnpmedia rebuild thread.
2009-11-04 19:32:47.936 Main::Registering HttpStatus Extension
2009-11-04 19:32:47.936 Enabled verbose msgs:  important general
2009-11-04 19:32:47.941 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-11-04 19:32:49.611 Reschedule requested for id -1.
2009-11-04 19:32:49.899 Scheduled 19 items in 0.3 = 0.01 match + 0.27 place
2009-11-04 19:32:49.901 Seem to be woken up by USER
2009-11-04 19:32:56.645 UPnpMedia: BuildMediaMap - no VideoStartupDir set,  skipping scan.

```

Matt

---

### Post by ian dobson on 2009-11-04
Hi,

the "DTVMux, Error: Invalid S2 modulation system parameter '1', aborting." error message means that something is screwed up in your channels/dvb_multiplex table. The best solution would be to delete all channels then do a channel scan again.

Regards
Ian Dobson

---

### Post by Lido on 2009-11-05
> **madverb said:**
> Yeah, this happened to me also. I just reinstalled the backend. Everything came up fine afterwards.
My problem is that the backend now doesn't start on boot. I have to manually start it.

When I try to install the backend, I get this:
```
mythtv-backend:
  Depends: mythtv-common (=0.22.0+fixes22594-0ubuntu1) but 1:0.21.0+fixes-20462-openglvdpau-0ubuntu3 is to be installed
  Depends: mythtv-transcode-utils (=0.22.0+fixes22594-0ubuntu1) but 1:0.21.0+fixes-20462-openglvdpau-0ubuntu3 is to be installed
```

and if I go to mythtv-common "mark for re-installation" is greyed out.

---

### Post by Lido on 2009-11-05
> **jyavenard said:**
> You're running the wrong Qt ... are you sure this is 0.22 ?

Qt 3 is only used for mythtv 0.21

The front end and mythtv-common looks like they're .21, but most of everything is .22.

I did enable some vdpau non-ubuntu repositories a couple of upgrades ago, but it didn't seem to negatively impact anything on my last update (jaunty).

Here's synaptic with all the myth stuff showing:
[IMG]http://img269.imageshack.us/img269/5297/screenshotis.png[/IMG]

---

### Post by madverb on 2009-11-05
> **Lido said:**
> When I try to install the backend, I get this:
```
mythtv-backend:
  Depends: mythtv-common (=0.22.0+fixes22594-0ubuntu1) but 1:0.21.0+fixes-20462-openglvdpau-0ubuntu3 is to be installed
  Depends: mythtv-transcode-utils (=0.22.0+fixes22594-0ubuntu1) but 1:0.21.0+fixes-20462-openglvdpau-0ubuntu3 is to be installed
```

and if I go to mythtv-common "mark for re-installation" is greyed out.

Sorry, I forgot that I actually had to remove other parts of mythtv and then reinstall them.
I didn't lose any information in doing so.

---

### Post by Mephi on 2009-11-05
> **ian dobson said:**
> 
the "DTVMux, Error: Invalid S2 modulation system parameter '1', aborting." error message means that something is screwed up in your channels/dvb_multiplex table. The best solution would be to delete all channels then do a channel scan again.

Hi Ian,

Thanks for the suggestion. I've deleted and re-scanned the channels, but Myth still doesn't start as a service. But it did get rid of the S2 modulation errors :-)

Matt

---

### Post by SnafuFlux on 2009-11-05
I'm posting to say that I had this issue too.  I just blew away 9.04 and clean installed 9.10

---

### Post by Lido on 2009-11-05
> **madverb said:**
> Sorry, I forgot that I actually had to remove other parts of mythtv and then reinstall them.
I didn't lose any information in doing so.

Thanks. I uninstalled common and then reinstalled everything and it all seems to work though I've got no sound and the video seems like it's in slo-mo. Turning off compiz fusion seems to help the video, but the sound has me stumped. Changing various settings in Alsamixer and the sound pref tool didn't seem to help.

---

### Post by Mephi on 2009-11-06
> **SnafuFlux said:**
> I'm posting to say that I had this issue too.  I just blew away 9.04 and clean installed 9.10

I really hope I don't have to do that, this server's running a lot more than just myth. 

I've now tried apt-get remove mythtv-common, which pulled out all of the backend packages as well. I then reinstalled them, but I still get the same syslog messages when I start it:

```
Nov  6 18:28:46 home init: mythtv-backend main process (16878) terminated with status 1
Nov  6 18:28:46 home init: mythtv-backend main process ended, respawning
Nov  6 18:28:46 home init: mythtv-backend main process (16894) terminated with status 1
Nov  6 18:28:46 home init: mythtv-backend main process ended, respawning
Nov  6 18:28:46 home init: mythtv-backend main process (16910) terminated with status 1
Nov  6 18:28:46 home init: mythtv-backend main process ended, respawning
Nov  6 18:28:46 home init: mythtv-backend main process (16926) terminated with status 1
Nov  6 18:28:46 home init: mythtv-backend respawning too fast, stopped
```

Matt

---

### Post by madverb on 2009-11-06
Just try uninstall everything MythTV related. Your database will stay in tact. Possibly even rename your ~/.mythtv to .mythtv.old as well.
Then install the main mythtv package.

---

### Post by Mephi on 2009-11-07
Ok, I've done an apt-get remove on the following packages:
mythbuntu-repos
mythtv-backend
mythtv-common
mythtv-database
mythtv-frontend
mythweb

I then did an 'apt-get autoremove' and an 'apt-get autoclean'.

Then I renamed my ~/.mythtv directory

Then I reinstalled the mythbuntu repos package:
wget [http://www.mythbuntu.org/files/mythbuntu-repos.deb](http://www.mythbuntu.org/files/mythbuntu-repos.deb)
sudo dpkg --install mythbuntu-repos.deb

Then one by one I reinstalled the above packages.

And still it doesn't work

During  the re-install I get:
```
Setting up mythtv-database (0.22.0+fixes22750-0ubuntu0+mythbuntu3) ...
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
```

And my DB username/password are both mythtv.

Matt

---

### Post by Mephi on 2009-11-08
Found it!!!! :D:D:D

I've been doing some digging to find out what the upstart daemon does differently to just running sudo mythbackend.

I've found the init script (/etc/init/mythtv-backend.conf) which contains the command:
exec /bin/su -c "/usr/bin/mythbackend $ARGS" $USER

Looking at the man page for su it states:
In particular, an argument of -c will cause the next argument to be treated as a command by most command interpreters. The command will be executed by the shell specified in /etc/passwd for the target user.

I checked my /etc/passwd file and the mythtv user was set to /bin/false. I set it to /bin/sh and now it works.

I don't know why it was set to /bin/false, but I'm not going to rule out some over-zealous system securing on my part.

Matt

---

### Post by jt_04 on 2009-11-13
i also had to remove/add my capture cards and video sources in the backend before I could actually watch tv.  i also had to reinstall mythvideo to get my video library back.

---

