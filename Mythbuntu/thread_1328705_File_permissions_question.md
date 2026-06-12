---
title: "File permissions question"
date: 2009-11-16
forum: Mythbuntu
---

### Post by Al_Vampyre on 2009-11-16
Hi all,

The simple way of posing this question is - Is it possible to get a file to automatically inherit the permissions from a parent folder?

My Mythbuntu box is a combined FE/BE and I run a great program called TED in conjunction with Transmission that downloads TV shows for me. My media drive is mounted as /mythtv/ and contains all the folders set up via storage groups. The format is as below

/videos/Show Name/Season/S01E01 etc

Transmission downloads the shows and puts them into /mythtv/videos and then I manually sort them into the correct show and season folder.

The problem is that I cannot delete the shows from the video manager once I have watched them because the owner is showing as me, the group is showing as MythTV, but MythTV has Read Only access.

I have checked that I am a member of the MythTV group and all seems to be correct. I thought that would give MythTV the same permissions as me but it doesn't seem to. 

Am I missing something? If not is there a way that I can force a file moved into /videos to be owned by MythTV rather than me?

I know I can run CHOWN each time I move the video files but I was hoping for a more elegant solution.

Thanks in advance for your help.

---

### Post by dannyboy79 on 2009-11-16
if the files are owned by you but in mythtv group and your in mythtv group and there is mythtv group read/write/ access on the video folder and the files in that folder you should have an issue. you could write a bash script that moves the files and chowns them all in one command.

---

### Post by Al_Vampyre on 2009-11-17
Thanks dannyboy79, as I say I thought that me being a member of the mythtv group would mean that mythtv would have the same permissions as me, if thats not the case or there is no way to force it then it looks like a move/chown bash script is the way to go.

---

### Post by tgm4883 on 2009-11-17
> **Al_Vampyre said:**
> Thanks dannyboy79, as I say I thought that me being a member of the mythtv group would mean that mythtv would have the same permissions as me, if thats not the case or there is no way to force it then it looks like a move/chown bash script is the way to go.

No, that gives you the same permissions as the MythTV group (well really it lets you access things owned by the MythTV group).

---

### Post by ZedThou on 2009-11-17
Here's what I would do,

```

# set videos directory to group mythtv, make it group-writeable and setgid

chgrp mythtv /mythtv/videos
chmod g+ws /mythtv/videos

# now all new files/directories created in the videos dir belong to group mythtv, and
# any process which creates new files/directories under the videos dir should first set

umask 002

# which makes the new entries group-writeable

```

---

### Post by Al_Vampyre on 2009-11-17
Thanks ZedThou, thats really handy, when you say 'create' does that include files copied/pasted and files moved by Tansmission?

---

### Post by ZedThou on 2009-11-17
Well the umask might be problematic if you're moving files around with a file manager instead of a more automated approach with a script or somesuch, so it might just be easiest to go back to the original plan and chmod -R g+w /mythtv/videos after you've got everything in place.

---

### Post by Al_Vampyre on 2009-11-17
Thanks again, you've been a great help

---

