---
title: "Incorrect tuner status when accessing via ssh"
date: 2011-05-27
forum: Mythbuntu
---

### Post by bcg30506 on 2011-05-27
When I ssh into my backend/frontend server, it reports certain things like if upgrades are available, disk space usage, and tuner status.  However the tuner status always reads Idle even when I know for certain one or more are in use.

MythTV status for localhost
===========================
Status..........: Mon Apr 25 2011, 10:20 AM
Total Disk Space: Total space is 1,198.6 GB, with 631.1 GB used (52.7%)

Encoders:
mythbox (1) - Idle
mythbox (2) - Idle
mythbox (4) - Idle
mythbox (5) - Idle


What is doing this "report" upon login and where is it getting the encoder list?  At the time I captured the above screen, numbers 1 and 2 were recording shows.

---

### Post by ian dobson on 2011-05-27
Hi,

Mythtv-status is the command that creates the output:-

```

mythtv-status

MythTV status for localhost
===========================
Status: Fri May 27 2011, 8:57 PM

Encoders:
alpha2 (1) - 7
alpha2 (2) - Idle
alpha2 (3) - 7
alpha2 (4) - Idle
alpha2 (5) - Idle
alpha2 (6) - Idle

Recording Now:
The Mentalist (3+) Ends: 21:10:00
Doctor Who Confidential (BBC Three / CBBC Channel) Ends: 21:00:00

Scheduled Recordings:
2011-05-27 21:10:00 - The Mentalist (3+)
2011-05-27 22:00:00 - The Mentalist (3+)
2011-05-27 22:30:00 - Inspector Barnaby - Ein Männlein stirbt im Walde (ORF2 V)
2011-05-27 22:40:00 - War Wolves (SciFi)
2011-05-28 19:45:00 - Doctor Who (BBC 1 London)
2011-05-28 19:45:00 - Doctor Who (BBC 1 NI)
2011-05-28 20:30:00 - Doctor Who Confidential (BBC Three / CBBC Channel)
2011-05-28 21:15:00 - Doctor Who Confidential (BBC HD)

```

Note tuner 1 & 3 are active in the above output.

The script seems to use the web/xml status page from the backend (localhost:6544) maybe your backend it on a different ip/port?

Note it I go over the the backends IP address/port 6544 with internet explorer I see a HTML version of the status page.

Regards
Ian Dobson

---

### Post by bcg30506 on 2011-05-28
Everything is setup right with IP/port, and when I run it from the command line after ssh'ing in it looks okay.  It is only what is displaying in the login message when first getting into the box.

---

### Post by nickrout on 2011-05-29
@bcg90210 I sometimes et that result if mythtv-backend has just been started or restarted, I guess it sepnds some time "warming up".

@ian dobson - looks like something wrong with your system perhaps? It seems to be recording two of some programmes (viz dr who)?

---

### Post by ian dobson on 2011-05-29
> **nickrout said:**
> @bcg90210 I sometimes et that result if mythtv-backend has just been started or restarted, I guess it sepnds some time "warming up".

@ian dobson - looks like something wrong with your system perhaps? It seems to be recording two of some programmes (viz dr who)?

No, that's ok. Doctor who is comming on 2 different channels and I just delete one of them. I do that just incase one recording screws up.

Regards
Ian Dobson

---

### Post by bcg30506 on 2011-05-29
Unfortunately, I think it is more "sinister" than that for me.  Here is the screen output from just now with me logging into the machine via ssh and seeing the messages, then manually running mythtv-status.  You'll notice how the tuner numbers do not even match?

I was watching live TV as I did this.  The backend has not been restarted in over a day.  (Looks like some new updates were found too)

me@mythbox's password: 
Linux mythbox 2.6.35-22-generic-pae #34~lucid1-Ubuntu SMP Mon Oct 11 14:53:39 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  [https://help.ubuntu.com/](https://help.ubuntu.com/)

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

23 packages can be updated.
0 updates are security updates.

MythTV status for localhost
===========================
Status..........: Mon Apr 25 2011, 10:20 AM
Total Disk Space: Total space is 1,198.6 GB, with 631.1 GB used (52.7%)

Encoders:
mythbox (1) - Idle
mythbox (2) - Idle
mythbox (4) - Idle
mythbox (5) - Idle

Last login: Sat May 28 14:57:02 2011 from bradslaptop
me@mythbox:~$ mythtv-status 

MythTV status for localhost
===========================
Status..........: Sun May 29 2011, 10:13 AM
Total Disk Space: Total space is 1,198.6 GB, with 665.2 GB used (55.5%)

Encoders:
mythbox (4) - Idle
mythbox (5) - Watching LiveTV
mythbox (6) - Idle
mythbox (8) - Idle

Recording Now:
America's News HQ (Fox News Channel) Ends: 12:00:00

Scheduled Recordings:
2011-05-29 11:00:00 - The Indianapolis 500: A Centennial Celebration (WSB HD)
2011-05-29 12:00:00 - 2011 Indianapolis 500 (WSB HD)

---

### Post by nickrout on 2011-05-29
> **ian dobson said:**
> No, that's ok. Doctor who is comming on 2 different channels and I just delete one of them. I do that just incase one recording screws up.

Regards
Ian Dobson

a dedicated fan!

---

### Post by bcg30506 on 2011-05-29
As for my issue, I got it showing the current status now, but in doing so, I've lost all the other useful motd info when accessing the box thru ssh.

```
me@mythbox's password: 

MythTV status for localhost
===========================
Status..........: Sun May 29 2011, 4:00 PM
Total Disk Space: Total space is 1,198.6 GB, with 673.0 GB used (56.1%)

Encoders:
mythbox (4) - Idle
mythbox (5) - Idle
mythbox (6) - Recording
mythbox (8) - Idle

Recording Now:
2011 Indianapolis 500 (WSB HD) Ends: 15:30:00

Last login: Sun May 29 15:23:40 2011 from bradslaptop

```
I did this by adding a 50-mythtv-status script in /etc/update-motd.d directory.  Obviously, this was not the ideal way to solve it since it broke the apt-get status, disk space usage, and upcoming recordings.

Also, as a side note, odd that it says the recording ends at 15:30 when it was already 16:00.  This has been an anomaly for a while in mythtv when you setup extra time for Sports Events.  I have it at 60 minutes so it will record until 16:30, but the schedule should reflect that.

With the extra time not being included in the schedule, I cannot stop recording from the frontend recordings screen if it has past the scheduled 15:30 time and is in the extra time alloted for sports events.  So the Status page in frontend says it is recording, but the indicator on the Watch Recordings page say it is not.  Guess I should report this as a separate issue.

---

### Post by bcg30506 on 2011-05-29
It gets stranger.  Remember those 23 updates that it said were needed.  I checked and they were all mythtv updates, so I did an apt-get upgrade and rebooted.

Now when I ssh in, I get:
```
Linux mythbox 2.6.35-22-generic-pae #34~lucid1-Ubuntu SMP Mon Oct 11 14:53:39 UTC 2010 i686 GNU/Linux
Ubuntu 10.04.2 LTS

Welcome to Ubuntu!
 * Documentation:  https://help.ubuntu.com/

Your CPU appears to be lacking expected security protections.
Please check your BIOS settings, or for more information, run:
  /usr/bin/check-bios-nx --verbose

MythTV status for localhost
===========================
Status...........: Sun May 29 2011, 4:45 PM
Total Disk Space.: Total space is 1,198.6 GB, with 673.8 GB used (56.2%)
Next Recording In: Never

Encoders:
mythbox (4) - Idle
mythbox (5) - Idle
mythbox (6) - Idle
mythbox (8) - Idle


MythTV status for localhost
===========================
Status..........: Mon Apr 25 2011, 10:20 AM
Total Disk Space: Total space is 1,198.6 GB, with 631.1 GB used (52.7%)

Encoders:
mythbox (1) - Idle
mythbox (2) - Idle
mythbox (4) - Idle
mythbox (5) - Idle

```
So I'm getting the new current status from my script first, then the old cached one that sits in the motd file, and I still don't have all the other stuff it used to show.

---

### Post by bcg30506 on 2011-05-29
Well, I just ssh'd into my backend box again, and lo and behold, the motd looks good.  All info is present and up to date.  I made no other changes since the last reboot, but maybe the last upgrade fixed something and it just took a little time to "propagate"?  No idea.  Anyway, here is the latest screen cap:
```
me@mythbox's password: 

MythTV status for localhost
===========================
Status..........: Sun May 29 2011, 6:50 PM
Total Disk Space: Total space is 1,198.6 GB, with 661.2 GB used (55.2%)

Encoders:
mythbox (4) - Idle
mythbox (5) - Idle
mythbox (6) - Idle
mythbox (8) - Watching LiveTV

Recording Now:
NASCAR Racing (WAGA HD) Ends: 23:00:00


```

---

### Post by nickrout on 2011-05-29
You haven't said what versions you are using, but I have noticed that at some stages of it's life my backend did not give the mythtv-status output on logon. Then after some update it did again. weird, but it didn't bother me.

---

### Post by bcg30506 on 2011-05-29
It's mythbuntu 10.04 with mythtv 0.24.1.

---

