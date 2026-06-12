---
title: "remote front end watching recordings works, but can't watch videos."
date: 2013-04-08
forum: Mythbuntu
---

### Post by rusty0101 on 2013-04-08
I have a setup with a master back-end using storage groups for media storage, and multiple front ends, some dedicated, some just the front end software installed on a desktop or laptop along with an existing desktop. 

The problem I'm running into is that one of the front ends is unable to play back video from the master back end. Note that I'm not saying it won't play back recordings. Those work. It's Video that is not working. This is not directly an issue on other systems, which is not to say that other systems are not demonstrating problems, I have to be careful which system I run 'check for updates' on, as some of the systems just wipe the database of video information and say that there's nothing there, even though it's perfectly happy to play the content and show the library if it's built on other systems.

All systems are using release 0.25 of Mythtv. 

This looks to me like the front end is configured to look for the videos locally, and is not finding them. However the media setting general settings 1/4 'Directories that hold videos:' entry is blank on each of the front ends, since the videos are stored in a storage group on the back end.

Pretty sure that I'm missing something that should be easy to find as to what's going on with the host that's unable to play video content. I'm not finding anything obvious when doing a google search, though I am getting hits, they are mostly related to content on a slave backend which is not pertinent to this problem as there are no slave backends setup at this time.

If anyone has a recommendation, I'd love to tag this thread as [SOLVED] before the next LTS update comes out. And I'd prefer the solution not be 'upgrade to 0.26' or 'run from the git source', as neither of those are going to happen any time soon. (Not running 12.10, and won't even look at 13.04)

Thanks,

~Rusty

---

### Post by newlinux on 2013-04-10
On the frontends that don't work are you able to see the videos? Have you looked in your frontend logs? What happens when the videos don't work (error message of any kind).

---

### Post by tgm4883 on 2013-04-11
> **rusty0101 said:**
> I have a setup with a master back-end using storage groups for media storage, and multiple front ends, some dedicated, some just the front end software installed on a desktop or laptop along with an existing desktop. 

The problem I'm running into is that one of the front ends is unable to play back video from the master back end. Note that I'm not saying it won't play back recordings. Those work. It's Video that is not working. This is not directly an issue on other systems, which is not to say that other systems are not demonstrating problems, I have to be careful which system I run 'check for updates' on, as some of the systems just wipe the database of video information and say that there's nothing there, even though it's perfectly happy to play the content and show the library if it's built on other systems.

All systems are using release 0.25 of Mythtv. 

This looks to me like the front end is configured to look for the videos locally, and is not finding them. However the media setting general settings 1/4 'Directories that hold videos:' entry is blank on each of the front ends, since the videos are stored in a storage group on the back end.

Pretty sure that I'm missing something that should be easy to find as to what's going on with the host that's unable to play video content. I'm not finding anything obvious when doing a google search, though I am getting hits, they are mostly related to content on a slave backend which is not pertinent to this problem as there are no slave backends setup at this time.


We'll need to see backend logs and frontend logs from a time that you attempted to watch something and it failed. We'll also need the time you did this and the filename that you tried to watch. 

> **rusty0101 said:**
> 
If anyone has a recommendation, I'd love to tag this thread as [SOLVED] before the next LTS update comes out. And I'd prefer the solution not be 'upgrade to 0.26' or 'run from the git source', as neither of those are going to happen any time soon. (Not running 12.10, and won't even look at 13.04)

Thanks,

~Rusty

We provide mythtv updates for older releases. You can currently update to 0.26 on 12.04. Not saying you should upgrade to 0.26, but you should at least enable the 0.25 updates as things do get fixed in that branch.

---

### Post by rusty0101 on 2013-04-16
0.25 updates are being applied. my problem is that I have 4 dedicated front ends, and at least 3 stand alone computers with front end software running on them in addition to the master backend, and a back-end that is sitting waiting on a new DTV receiver or card to be useful again. I've had problems with every non-backwards compatible update of MythTV, and MythTV seems to think that's the best route to go. To be clear if either the front-end of 0.26 or the back-end of 0.26 would talk to the other at 0.25, without breaking, I could walk through each system and update it as needed. But that's not the way that the developers like to do things, so I get to dedicate a day to going through each of the devices, and making sure that all of the front ends are ready to have software updates done, back-up and update the back-end, then walk through each of the front ends, do the front-end, including making sure that everything actually works (as the myth-music plugin broke the 0.25 experience leaving the screen blank with no indication that there was even a problem, and has had to be removed manually when it had been installed) before I am going to be comfortable with going ahead and breaking my (mostly) functioning 0.25 to switch to 0.26. I understand this is beta software, in that there is no guarantee that anything will work. I'm just noting that the upgrade procedure needs a major overhaul.

In response to the question on 'can I see the videos?' question, to be clear, I can see the entire library of videos as available. All the cover photos and content descriptions are visible. When I manually run 'mythtv-frontend -v' from a command line, there are no error messages on the command line indicating that it had a problem with showing the video. The video that I'm trying to view in the capture logs below is "2001: a Space Odyssey" which is on the mythtv-backend server Beast, and the 'ls -lah 2001*' of the folder that contains the file is:

[FONT=Courier New][COLOR="#008000"]rusty@beast:/mnt/beast/samba/videos$ ls -lh 2001*
-rwxrwxrwx 1 mythtv mythtv 910M May 13  2011 2001.avi[/COLOR]
[/FONT]

Of course it would be nice if the log-grabber talked the new pastebin API, but apparently that's something that hasn't been fixed either. Ok, manually:
mythfront.cap - [http://pastebin.com/L6PGQwHs](http://pastebin.com/L6PGQwHs) - capture of an xterm session where I performed 'myth-frontend -v'
mythfront.log - [http://pastebin.com/1tw8xtiD](http://pastebin.com/1tw8xtiD) - frontend log file for that session - exceprt from /var/log/mythtv/mythfrontend.log on system katskorner.
mythbackend.log - [http://pastebin.com/GiggCyPz](http://pastebin.com/GiggCyPz) - mythtv backend log file excerpt from the back-end server that katskorner is talking to, beast.

Scenerio that generated these captures:
 - in an xterm session on the front end execute the command 'myth-frontend -v'
 - wait for main menu to appear
 - select videos menus
 - wait for videos menu to appear
 - scroll to video for 2001 a space odyssey and select
 - wait for video content dialog to appear with 'play' and 'exit' menu items
 - select 'play'
 - video content dialog goes away and re-appears immediately
 - escape out of content dialog
 - escape out of video menu
 - escape out of main menu
 - agree to exit.

The backend log is not from a '-v' session of mythtv-backend. Beast launches mythtv-backend via an upstart job, and it is unclear to me what file I need to modify to make sure that the '-v' parameter is applied to the backend, vs upstart or some other portion of the upstart process. Advice would be appreciated on that. Mythtv is installed on the backend in what should be a standard install for mythtv-backend on a Mythbuntu system.

Thank you,

-Rusty

---

### Post by BicyclerBoy on 2013-04-16
I see nothing in the log files.
You not using samba share with any of the myth frontends?

You realise you have to trigger the re-scan of videos (after any change)?

AFAIK 
You are not allowed to have samba/NFS share in FE local Videos path if it overlaps with master BE video storage group.
Local FE Videos path must not overlap the BE Video storage group.
You can find "chapter & verse" on this problem in the mythtv mailing lists..

I believe Mythbuntu uses upstart & a fake target /usr/bin/mythbackend which runs "real" program.

---

### Post by rusty0101 on 2013-04-16
The 'samba' is simply the mount point, It's descriptive to me as the point where I have mounted a local drive that contains directories that are going to be shared via samba. It is not mounted on the front ends, and considering that I am viewing files from this share on other front ends, is not, or should not be, a part of the issue.

I will do a re-scan on this front end, as I have on others, when I get home, or early tomorrow to see if that makes a difference. If so, then the difference is likely to be that the change in path (videos at one time were in /var/lib/mythtv/videos, however the filesystem that is on was running out of capacity so moved it and a few other things onto a separate hard drive now mounted as noted above.)

I will look at /usr/bin/mythbackend to see if I can modify it's logging behaviour when I get a chance as well, and will update with a pastebin post with any new information I can show then.

---

### Post by BicyclerBoy on 2013-04-16
AFAIK
If one FE can access the BEs videos (via myth not a share) then the videos must be in a defined storage group..then the videos should still be visible (without rescan) in any FE.
The first scan (from any FE) should trigger a rescan by master BE of all video storage groups.

The mythbackend can be stopped & re-launched from terminal with verbose logging to stdout or syslog.
Look for /usr/(local/)bin/mythbackend.real.

Make sure the FEs local video search path is empty &/or ensure it is not looking at samba/NFS shares..

---

### Post by tgm4883 on 2013-04-17
You gave us 1 minute of backend logs with no context.  I'd like to see a bit longer set of backend logs when you do two things.

1) On a working frontend, go play "2001: a Space Odyssey", note the time that you did this.

2) On the non-working frontend, attempt to play "2001: a Space Odyssey", note the time that you did this.

Post the backend logs, frontend logs (from both systems), and the times you ran each test.

---

