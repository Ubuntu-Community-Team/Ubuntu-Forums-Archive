---
title: "PVR-150 doesn't come back after standby"
date: 2008-12-01
forum: Mythbuntu
---

### Post by lemaymd on 2008-12-01
I have a PVR-150 MCE working great with MythTV...until I put the computer to sleep (standby or hibernate) and wake it up again later.  Then, watch TV doesn't work.  I get the black screen for about 10 seconds, and then drop back to the MythTV main page.  I'm running 0.21.20080304-1 on 8.10 (upgraded from 8.04), and have seen this problem with kernels 2.6.24-19 and 2.6.27-10 at least.  There is no interesting output in mythbackend.log by default, but here's what I see from mythfrontend:
```

2008-12-01 15:03:57.998 RingBuf(/var/myth/1060_20081201150350.mpg): Invalid file (fd -1) when opening '/var/myth/1060_20081201150350.mpg'.
2008-12-01 15:03:58.022 NVP::OpenFile(): Error, file not found: /var/myth/1060_20081201150350.mpg
2008-12-01 15:03:58.022 TV Error: StartPlayer(): NVP is not playing after 20000 msec

```

Here's what I get from the frontend if I enable -v all:

```

2008-12-01 15:10:09.338 TV: Attempting to change from None to WatchingLiveTV
2008-12-01 15:10:09.339 MythSocket(b1f650:28): new socket
2008-12-01 15:10:09.339 MythSocket(b1f650:28): attempting connect() to (0.0.0.0:6543)
2008-12-01 15:10:09.339 MythSocket(b1f650:28): state change Idle -> Connected
2008-12-01 15:10:09.339 write -> 28 21      MYTH_PROTO_VERSION 40
2008-12-01 15:10:09.339 read  <- 28 13      ACCEPT[]:[]40
2008-12-01 15:10:09.339 Using protocol version 40
2008-12-01 15:10:09.339 write -> 28 27      ANN Playback atom-desktop 0
2008-12-01 15:10:09.339 MSqlQuery: SELECT name, skipback FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND skipback <> 0 ORDER BY name = 'Default';
2008-12-01 15:10:09.340 MSqlQuery: SELECT name, jump FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND jump <> 0 ORDER BY name = 'Default';
2008-12-01 15:10:09.340 MSqlQuery: SELECT name, timestretch FROM playgroup WHERE (name = 'Default' OR name = 'Default')       AND timestretch <> 0 ORDER BY name = 'Default';
2008-12-01 15:10:09.340 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVIdleTimeout' AND hostname = 'atom-desktop' ;
2008-12-01 15:10:09.340 MSqlQuery: SELECT data FROM settings WHERE value = 'LiveTVIdleTimeout' AND hostname IS NULL;
2008-12-01 15:10:09.340 MSqlQuery: SELECT keylist FROM keybindings WHERE context = 'TV Playback' AND action = 'GUIDE' AND hostname = 'atom-desktop' ;
2008-12-01 15:10:09.345 read  <- 28 2       OK
2008-12-01 15:10:09.345 write -> 28 86      QUERY_RECORDER 1[]:[]SPAWN_LIVETV[]:[]live-atom-desktop-2008-12-01T15:10:09[]:[]0[]:[]
2008-12-01 15:10:16.345 MythSocket(b1f650:28): readStringList: Error, timeout (quick).
2008-12-01 15:10:16.345 MythSocket(b1f650:28): state change Connected -> Idle
2008-12-01 15:10:16.345 RemoteEncoder::SendReceiveStringList(): No response.
2008-12-01 15:10:16.345 MSqlQuery: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = 'live-atom-desktop-2008-12-01T15:10:09' ORDER BY chainpos;
2008-12-01 15:10:16.345 GetEntryAt(-1) failed.
2008-12-01 15:10:16.346 MSqlQuery: SELECT recorded.chanid,starttime,endtime,title, subtitle,description,channel.channum, channel.callsign,channel.name,channel.commmethod, channel.outputfilters,seriesid,programid,filesize, lastmodified,stars,previouslyshown,originalairdate, hostname,recordid,transcoder,playgroup, recorded.recpriority,progstart,progend,basename,recgroup, storagegroup FROM recorded LEFT JOIN channel ON recorded.chanid = channel.chanid WHERE recorded.chanid = '0' AND starttime = '1969-12-31T18:00:00' ;
2008-12-01 15:10:16.346 EntryToProgram(0@Wed Dec 31 18:00:00 1969) failed to get pginfo
2008-12-01 15:10:16.346 TV Error: LiveTV not successfully started
2008-12-01 15:10:16.346 MythSocket(b1f650:-1): DownRef: -1
2008-12-01 15:10:16.346 MythSocket(b1f650:-1): delete socket
2008-12-01 15:10:16.346 TV Error: LiveTV not successfully started
2008-12-01 15:10:16.445 TV: Deleting TV Chain in destructor
2008-12-01 15:10:16.446 MSqlQuery: DELETE FROM tvchain WHERE chainid = 'live-atom-desktop-2008-12-01T15:10:09' ;
2008-12-01 15:10:16.446 MythEvent: PLAYBACK_END atom-desktop
2008-12-01 15:10:16.449 DPMS Deactivated 
2008-12-01 15:10:16.450 DPMS Reactivated.

```

Here's what I get in mythbackend.log if I enable -v all in its init script:
```

2008-12-01 15:14:29.078 MythSocket(888b80:10): socket is readable
2008-12-01 15:14:29.081 MythSocket(888b80:10): cb->readyRead()
2008-12-01 15:14:29.081 MythSocket(888b80:10): UpRef: 2
2008-12-01 15:14:29.082 read  <- 10 23      GET_FREE_RECORDER_COUNT
2008-12-01 15:14:29.084 write -> 10 1       1
2008-12-01 15:14:29.085 MythSocket(888b80:10): DownRef: 1
2008-12-01 15:14:29.085 MythSocket(888b80:10): socket is readable
2008-12-01 15:14:29.088 MythSocket(888b80:10): cb->readyRead()
2008-12-01 15:14:29.089 MythSocket(888b80:10): UpRef: 2
2008-12-01 15:14:29.089 read  <- 10 29      GET_NEXT_FREE_RECORDER[]:[]-1
2008-12-01 15:14:29.092 Getting next free recorder after : -1
2008-12-01 15:14:29.093 Card 1 is local.
2008-12-01 15:14:29.093 write -> 10 24      1[]:[]localhost[]:[]6543
2008-12-01 15:14:29.094 MythSocket(888b80:10): DownRef: 1
2008-12-01 15:14:29.094 MythSocket(7f9ad8001890:19): new socket
2008-12-01 15:14:29.096 MythSocket(7f9ad8001890:19): setSocket: 18
2008-12-01 15:14:29.097 MythSocket(7f9ad8001890:18): state change Idle -> Connected
2008-12-01 15:14:29.097 MythSocket(7f9ad8001890:18): UpRef: 1
2008-12-01 15:14:29.098 MythSocket(7f9ad8001890:18): socket is readable
2008-12-01 15:14:29.112 MythSocket(7f9ad8001890:18): cb->readyRead()
2008-12-01 15:14:29.113 MythSocket(7f9ad8001890:18): UpRef: 2
2008-12-01 15:14:29.113 read  <- 18 21      MYTH_PROTO_VERSION 40
2008-12-01 15:14:29.120 write -> 18 13      ACCEPT[]:[]40
2008-12-01 15:14:29.120 MythSocket(7f9ad8001890:18): DownRef: 1
2008-12-01 15:14:29.120 MythSocket(7f9ad8001890:18): socket is readable
2008-12-01 15:14:29.127 MythSocket(7f9ad8001890:18): cb->readyRead()
2008-12-01 15:14:29.128 MythSocket(7f9ad8001890:18): UpRef: 2
2008-12-01 15:14:29.129 read  <- 18 27      ANN Playback atom-desktop 0
2008-12-01 15:14:29.136 MainServer::HandleAnnounce Playback
2008-12-01 15:14:29.136 adding: atom-desktop as a client (events: 0)
2008-12-01 15:14:29.137 write -> 18 2       OK
2008-12-01 15:14:29.138 MythSocket(7f9ad8001890:18): DownRef: 1
2008-12-01 15:14:29.138 MythSocket(7f9ad8001890:18): socket is readable
2008-12-01 15:14:29.144 MythSocket(7f9ad8001890:18): cb->readyRead()
2008-12-01 15:14:29.144 MythSocket(7f9ad8001890:18): UpRef: 2
2008-12-01 15:14:29.145 read  <- 18 86      QUERY_RECORDER 1[]:[]SPAWN_LIVETV[]:[]live-atom-desktop-2008-12-01T15:14:29[]:[]0[]:[]
2008-12-01 15:14:29.152 MSqlQuery: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = 'live-atom-desktop-2008-12-01T15:14:29' ORDER BY chainpos;
2008-12-01 15:14:29.153 MSqlQuery: SELECT chanid, starttime, endtime, discontinuity, chainpos, hostprefix, cardtype, channame, input FROM tvchain WHERE chainid = 'live-atom-desktop-2008-12-01T15:14:29' ORDER BY chainpos;
2008-12-01 15:14:29.908 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:29.916 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:29.917 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:30.918 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:30.919 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:30.919 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:31.920 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:31.921 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:31.922 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:32.923 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:32.924 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:32.925 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:33.926 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:33.927 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:33.928 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:34.929 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:34.942 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:34.943 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:35.944 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:35.945 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:35.946 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:36.947 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:36.948 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:36.948 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:37.949 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:37.950 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:37.951 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:38.952 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:38.953 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:38.954 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:39.955 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:39.956 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:39.956 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060
2008-12-01 15:14:40.957 MSqlQuery: SELECT chanid FROM channel WHERE channum  = '60' AND       sourceid = 1
2008-12-01 15:14:40.958 MSqlQuery: SELECT inputname, sourceid, cardid FROM cardinput WHERE cardinputid = 1
2008-12-01 15:14:40.959 MSqlQuery: SELECT mplexid FROM channel WHERE chanid = 1060

```

---

### Post by lemaymd on 2008-12-02
As it turns out, the ivtv driver for the PVR-150 doesn't have any support for standby or hibernate.  So, it's necessary for me to rmmod it before suspending and then modprobe it after resuming.

---

### Post by xinix on 2009-01-30
Another option would be to edit your acpi-support file to unload the pvr-150 modules and reload them on resume.  It's in /etc/default

Close to the beginning of the file there is a line that looks like this```
MODULES=""
```. Add these modules in between the quotes separating them with a space```
cx23885 cx25840 ivtv
```

---

### Post by rodercot on 2009-03-04
A note about this guys, if you are using 8.10 with pm-suspend adding those modules Actually ivtv only is needed to acpi-defaults does not work. 

 you need to make a plain text file called modules or config and place that in the /etc/pm/sleep.d/ directory. in the text file you only need

 SUSPEND_MODULES="ivtv"

 do not chmod this file. it works on mine finally.

 Dave

---

### Post by 4dognight on 2009-03-04
> **rodercot said:**
> A note about this guys, if you are using 8.10 with pm-suspend adding those modules Actually ivtv only is needed to acpi-defaults does not work. 

 you need to make a plain text file called modules or config and place that in the /etc/pm/sleep.d/ directory. in the text file you only need

 SUSPEND_MODULES="ivtv"

 do not chmod this file. it works on mine finally.

 Dave

Is this from experience of upgrading to 8.10? Did it overwrite the /usr/lib/pm-utils/defaults file? 
I have suspended the v4l2_common module, in order to get my tuners to work after a resume. I also found that if you suspend too many modules, it can mess things up too.

---

### Post by rodercot on 2009-03-04
> **4dognight said:**
> Is this from experience of upgrading to 8.10? Did it overwrite the /usr/lib/pm-utils/defaults file? 
I have suspended the v4l2_common module, in order to get my tuners to work after a resume. I also found that if you suspend too many modules, it can mess things up too.

 It is not experience to an upgrade per say but all the posts including the pm-utils guide on the Suse page warn against it and if you check out the config file in /usr/lib/pm-utils at the very top of the page when it open it says Do Not edit this file.

 I could not get the ivtv module to suspend when placed in the acpi-support file only when I placed the new text file in the /etc/pm/sleep.d directory did it work. I now have created new scripts and placed them in /etc/pm/sleep.d for

 07LCDd - stop and start LCDd
 08lirc - stop and restart lirc (start does not work)
 01mythtv - stop and start frontend.

 I could now try and stop using the 50modules hook if I wanted BUT it all works now and I do not want to break it. if you do want to try and run pm-suspend without certain hooks in /usr/lib/pm-utils/sleep.d again in the /etc/pm/sleep.d directory create a blank file for the hook you do not want to use. IE 50modules and do not chmod it. reboot and then try a suspend if you tail the log file from SSH you will see that the 50modules is now not being used. you can ofcourse reverse this by removing the 50modules file from /etc/pm/sleep.d
 I tried it with a couple for testing and it made no difference on my system. 
 
 rgds,

 Dave

---

### Post by 4dognight on 2009-03-05
> **rodercot said:**
> It is not experience to an upgrade per say but all the posts including the pm-utils guide on the Suse page warn against it and if you check out the config file in /usr/lib/pm-utils at the very top of the page when it open it says Do Not edit this file.

 

hmmm. I checked my file and it doesnt mention to not edit it. I then checked my desktop at work,running Suse 10.3 and it did have the line about not to edit it.

---

### Post by rodercot on 2009-03-06
So it looks like I may have been mistaken about needing only "ivtv" in the modules section. I noticed last night that after the WAF resumed from sleep on the slave machine, the tuner was still was reported as unavailable by the master b/e - DOH. It did play live tv BUT it grabbed the pvr-150 and source from the master instead of the slave.

 how do I get a list of all the modules the pvr-150 needs to resume. I tried lsmod but there are ton of modules in there. 
 
 Thanks,

 Dave

---

### Post by 4dognight on 2009-03-06
[QUOTE=
 how do I get a list of all the modules the pvr-150 needs to resume. I tried lsmod but there are ton of modules in there. 
 
 Thanks,

 Dave[/QUOTE]

I have the pvr350 and pvr500. I suspend v4l2_common only, and my cards back back after resume.

---

### Post by rodercot on 2009-03-06
> **4dognight said:**
> I have the pvr350 and pvr500. I suspend v4l2_common only, and my cards back back after resume.

 Well I tried that on mine and it was a no go, I added this to my resume script that I have pm-suspend call on resume

 irsend --device=/dev/lircd1 SET_TRANSMITTERS 1
 irsend --device=/dev/lircd1 SEND_ONCE dish select 

 and put the only ivtv modules in the modules files and it looks like all is fine now, I have tried it about 4 times each time power off the stb manually and each time it powers it on just fine and when I load live tv it is using the right tuner and proper source name. 

 rgds,

 Dave

---

### Post by rodercot on 2009-03-06
Now I have a new problem, Everything works great after a resume now, liveTV etc, BUT after 10 minutes I have a screensaver activating that I cannot disable with the remote. This happens in liveTV, menu's etc... THIS ONLY HAPPENS ON RESUME AND NOT FROM A NORMAL POWER UP.

 So what is the difference in interaction between starting mythfrontend with a regular boot up sequence and the screensaver and the interaction between the two on a resume. I have this in my resume script as my mythfrontend startup line, mabe it needs to be modified some.

 /usr/bin/mythfrontend &

 and this is my pm-utils 01mythtv script

 ```
#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
  suspend|hibernate)
    # kill existing mythfrontend as it will more than likely not work correctly after resume
    killall mythfrontend.real
    ;;

  resume|thaw)
    # restart mythfrontend
    sudo -H -u xbmc sh -c 'DISPLAY=:0.0 /home/xbmc/install/scripts/mythtv-resume'
    ;;
esac

```

 I hope you guys may have a thought.

 Dave

---

