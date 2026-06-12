---
title: "What's the best way to update channels when a cable provider makes changes?"
date: 2012-05-14
forum: Mythbuntu
---

### Post by Kantalias on 2012-05-14
I use an HDHR to record clear QAM through Comcast.  Recently, one of the carriers (e.g. channel 115) which they use to send FOX and PBS was modified.  I'm not sure I fully understand what happened, but the symptoms were:

[LIST]
[*]When a scheduled recording was attempted the front end would indicate under "Previous Recordings" that "Recorder Failed"
[*]When trying to tune to an affected channel in Live TV the tuner wouldn't lock and MythTV would time out suggesting I check my component connections
[*]When I would use the HD HomeRun GUI to tune to the affected carrier (e.g. channel 115) the subchannels (e.g. 4 or 802), which used to show the network broadcast channels and callsigns (e.g. "5.1 K<whatever>-DT HD"), were listed simply as "0".
[/LIST]
I did a channel scan in the backend and it deleted the four channels then added a bunch of stuff.  The desired channels showed up under their carrier, the subchannel number, and (an apparently) random integer.  To get schedules direct information to load I had to edit the backend channel list and manually enter the XMLTV ID for the desired channels then run mythfilldatabase.

However, this approach has caused:

[LIST]
[*]All of my channel recording rules to be broken
[*]All of my previous recordings from the affected channels to say they were recorded on integers representing a recorder (e.g. "#3051 #3051") instead of the channel callsigns (e.g. "K<whatever>-DT HD")
[*]Possibly coincidentally, mythfilldatabase to run REALLY slowly, like 5-30 minutes per day (i.e. a total of several hours for a refresh), with no notable CPU or disk utilization
[/LIST]
What's the right way to "move" a channel assignment, when I get Comcraptic service adjustments, so that recording rules are preserved?

---

### Post by Kantalias on 2012-05-18
> **Kantalias said:**
> [LIST]
[*]All of my channel recording rules to be broken
[/LIST]

This worked itself out once mythfilldatabase ran all the way through.

> **Kantalias said:**
> [LIST]
[*]Possibly coincidentally, mythfilldatabase to run REALLY slowly, like 5-30 minutes per day (i.e. a total of several hours for a refresh), with no notable CPU or disk utilization
[/LIST]

This was apparently coincidental as it seems to be a widely reported issue.  I used a commonly suggested fix:

1. Create tmpfs by adding to fstab:
```
tmpfs   /tmp   tmpfs   nodev,nosuid    0 0
```
2. Append to /etc/mysql/init.d/mythtv.cnf:[/LIST]
```
default_storage_engine=MyISAM
```
3. Restart mysql
```
sudo service mysql start/stop
```

My steps are compiled from various sources, but the origin of this fix seems to be [this thread]("http://ubuntuforums.org/showpost.php?p=11919106&postcount=38").

> **Kantalias said:**
> [LIST]
[*]All of my previous recordings from the affected channels to say they were recorded on integers representing a recorder (e.g. "#3051 #3051") instead of the channel callsigns (e.g. "K<whatever>-DT HD")
[/LIST]

> **Kantalias said:**
> [LIST]
What's the right way to "move" a channel assignment, when I get Comcraptic service adjustments, so that recording rules are preserved?

Still open to suggestions on the underlying question and how to resolve the cryptic recorder IDs being put in place of channel names for my past recordings...

---

