---
title: "&quot;error encountered while displaying video&quot; = Missing codec?"
date: 2009-09-16
forum: Mythbuntu
---

### Post by badger_fruit on 2009-09-16
Hello again,

Ubuntu 9.04
MythTV installed from Mythbuntu (added to existing installation as need this machine for other things other than Myth)
Intel P4HT, 1GB ram and NV6200 card.

I managed to get my Myth front-end working - to a degree - on this machine: it starts and lets me do everything except watch TV! I presume this is due to a missing codec (I've just checked on a suse machine and it works 100% so it's not a server or back-end problem). 

The error is a rather generic "error encountered while displaying video".  The EPG appears and is correct (ie it's current) and it picks a tuner OK so it looks like it's starting up OK but failing when trying to initialise the display.

**What codecs are needed and how do I install them in Ubuntu?**

I'm sorry, I'm new to ubby but have used linux (suse) for some time now so familiar with the concepts of linux and not afraid of konsole (or gnome-terminal I think it's called here!)

;)

---

### Post by ian dobson on 2009-09-16
Hi,

Have a look in the /var/log/frontend.log just after trying to watch TV. Usually it includes alot more information than just "woops it didn't work".

Do you mean live TV or a recording by "Watch TV"?

Regards
Ian Dobson

---

### Post by badger_fruit on 2009-09-17
> **ian dobson said:**
> Hi,

Have a look in the /var/log/frontend.log just after trying to watch TV. Usually it includes alot more information than just "woops it didn't work".

Do you mean live TV or a recording by "Watch TV"?

Regards
Ian Dobson

Argh, I am away from the PC and ssh is disabled by default!!
I'll have to re-post tonight with the log (unless I can figure out the issue that is).
As for Live TV or Recordings, I mean Live TV.

---

### Post by badger_fruit on 2009-09-17
OK, so I managed to get openssh-server installed using a VNC connection; I did a 
sudo tail -f /var/log/frontend.log and was told the file does not exist :(

---

### Post by badger_fruit on 2009-09-17
> **badger_fruit said:**
> I did a  sudo tail -f /var/log/frontend.log and was told the file does not exist :(

OK, so a little bit of a change to the path and I've found it; 
```
/var/log/mythtv/mythfrontend.log
```Shows:-

```

2009-09-17 11:35:10.703 OSD Theme Dimensions W: 1280 H: 720
2009-09-17 11:35:11.087 TV: Changing from None to WatchingLiveTV
2009-09-17 11:35:11.089 Realtime priority would require SUID as root.
2009-09-17 11:35:11.192 Video timing method: USleep with busy wait
2009-09-17 11:35:12.103 ProgramInfo, Error: GetPlaybackURL: '1019_20090917113505.mpg' should be local, but it can not be found.
2009-09-17 11:35:12.107 ProgramInfo, Error: GetPlaybackURL: '1019_20090917113505.mpg' should be local, but it can not be found.
2009-09-17 11:35:18.607 RingBuf(/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1019_20090917113505.mpg): Could not open /GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/ubuntu/1019_20090917113505.mpg.
2009-09-17 11:35:18.607 NVP, Error: JumpToProgram's OpenFile failed.
2009-09-17 11:35:18.607 NVP, Error: Unknown error, exiting decoder
2009-09-17 11:35:18.608 TV: Attempting to change from WatchingLiveTV to None

```

Looks like it's simply confused as to where to get the MPEG file from (this is a front-end, installed and configured using the Mythbuntu addon --> [http://www.mythbuntu.org/existing-ubuntu](http://www.mythbuntu.org/existing-ubuntu))

I may be wrong in this but how I understand Myth to work is the front end connects to the back end. When the front-end is told to do something like watch live TV, the backend starts to record to a file to /the/folder/from/setup/ and the front-end plays this file.

I guess the front-end on this client is messed up because if i go to my opensuse front-end machine, it plays just fine - in my eyes that means the backend is configured correctly.

I wonder if this is something to do with the mythbuntu "add-on" as it seems to automatically presume it's a single back and front end machine that will be used and so installs apache, mysql and so on onto the local machine.  You then have to change roles using the Myth Config utility in System > Admin to say "this is just a front-end".

Anyone got any suggestions please?
Oh, please be gentle, Im new to Ubuntu so not sure where things are or how to do things

---

