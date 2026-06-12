---
title: "newb mythbuntu 9.10 beta installation w/hd-pvr"
date: 2009-10-11
forum: Mythbuntu
---

### Post by robgue on 2009-10-11
hi. I'm trying to finally set-up mythbuntu with my hd-pvr. i installed the distro. rebooted. updated everything via aptitude. Configured the backend to the best of my ability. The hd pvr is recognized. waited for the database to pull info. I go to watch tv. it says please wait.. and nothing happens. I'm pretty new to mythtv and couldn't find a walk through. My source is directv btw using schedules direct. i figure im doing something wrong. i'd be happy with just getting a picture right now. figure configuring channels and remote can be done later.
heres my log:
[http://mythbuntu.pastebin.com/f482e75b7](http://mythbuntu.pastebin.com/f482e75b7)

---

### Post by dhughes on 2009-10-12
It's late here and I didn't read all that but I know I had trouble when setting up the tuner card and chose the wrong driver e.g. v4l instead of ivtv. The hint I guess was the 'scan channels' option was not available, I guess that should have been my first clue.

---

### Post by robgue on 2009-10-12
the hd pvr is recognized. To be more specific it's a hauppauge 1212. set to component. spdif sound.

---

### Post by bsntech on 2009-10-12
As dhughes indicated, did you scan for channels after installing the card?  Even if it is hooked in to DirectTV, it should pick up at least channel 3/4 or whatever channel your dish receiver provides the video on.

Lastly, where are your videos stored for recordings/live TV?  You can find this by going into the Backend - Storage Directories and it should show you the path to your videos.  Make sure that you do a:

sudo chmod 777 /path/to/videos

Sometimes if you change this from the default location, you need to ensure that the 'mythtv' user can write to this path - otherwise you will get the same kind of result you are current experiencing.

---

### Post by robgue on 2009-10-12
ok i ran sudo chmod 777 /path/to/videos (to the mythtv directory var/lib/mythtv)

under backend set up, i go to option 4 input connections. from there it has input connections [hddpvr: /dev/video0] (Component) -> directv

under "connect source to input" i have preset tuner to channel: 4
i manually put 4. not sure what to put here?? "starting channel" is set to 4.
"scan for channels" is greyed out. only have "fetch channels from listing source"
how do i determine what driver and or change the driver from v4l or ivtv?

just some more information. My directv source is an hr23. i ran a test. cat /dev/video0 > test.ts. i do get a video. happy about that.

---

### Post by robgue on 2009-10-13
i got a picture! :guitar:
looked at the wiki page on it. I left this out: Enter option 4, "Input Connections." Connect the video source to the appropriate input on the HD-PVR. Important Note: You must set a channel change script for the HD-PVR to work properly. If you don't care about channel changes, you can set it to /bin/true, but there absolutely must be a channel change script defined. Important Note 2: You must leave Preset tuner to channel empty or LiveTV and channel changes will not work. 

it works. just temporarily set it to /bin/true. now to sort everything else out....
thanks for your help. I'll probably need it again in the near future:)

---

