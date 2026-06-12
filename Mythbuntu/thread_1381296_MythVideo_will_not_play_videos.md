---
title: "MythVideo will not play videos"
date: 2010-01-14
forum: Mythbuntu
---

### Post by bbruenfl on 2010-01-14
Hello community,

I am building my first mythbuntu system and have it running fairly well however I am having trouble with the mythVideo module.  Bascially, when I attempt to play a video (and I've tried several of varying sizes and sources) I get "Please Wait..." then it kicks me back to the gui.

mythfrontend.log
> 2010-01-14 16:16:49.603 TV: Attempting to change from None to Watching Video
2010-01-14 16:16:50.093 TV: StartPlayer(0, Watching Video, main) -- begin
2010-01-14 16:16:50.333 RingBuf(myth://Videos@192.168.2.193:6543/4.avi) Warning: Peek() requested 2048 bytes, but only returning 0
2010-01-14 16:16:50.333 NVP::OpenFile(): Error, couldn't read file: myth://Videos@192.168.2.193:6543/4.avi
2010-01-14 16:16:50.333 TV: StartPlayer(0, Watching Video, main) -- end error
2010-01-14 16:16:50.366 ScreenSaverX11Private: DPMS Deactivated 1
2010-01-14 16:20:46.875 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-01-14 16:20:48.114 Error loading image to scale, from file: myth://Coverart@192.168.2.193:6543/4.jpg
2010-01-14 16:20:52.645 Loading menu theme from /usr/share/mythtv/themes/defaultmenu//util_menu.xml
2010-01-14 16:20:53.700 Loading window theme from /usr/share/mythtv/themes/Mythbuntu/video-ui.xml
2010-01-14 16:20:53.956 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@mythtv-base/var/lib/mythtv/videos/)mythbackend.log
> 2010-01-14 16:16:49.604 MainServer::ANN Playback
2010-01-14 16:16:49.672 adding: mythtv-base as a client (events: 0)
2010-01-14 16:16:49.735 MainServer::HandleAnnounce FileTransfer
2010-01-14 16:16:49.815 adding: mythtv-base as a remote file transfer
2010-01-14 16:16:49.953 RingBuf(/var/lib/mythtv/videos//4.avi) Error: File exists but is not readable by MythTV!
2010-01-14 16:16:50.113 RingBuf(/var/lib/mythtv/videos//4.avi) Error: Invalid file descriptor in 'safe_read()'I used the default settings throughout the mythVideo setup.  
The port in question 6543 is open according to the port scan.
And the file plays fine in both mPlayer and VLC.

Any help would be greatly appreciated.

Thanks,
Bo

---

### Post by OffAxis on 2010-01-14
There's a line in the backend log...
> 2010-01-14 16:16:49.953 RingBuf(/var/lib/mythtv/videos//4.avi) Error: File exists but is not readable by MythTV!

Are the codecs available on the backend machine?

Does myth have permission to access the file?

The double slash before the file name usually isn't a problem, but you could try taking out one of the forward slashes.

---

### Post by williammanda on 2010-01-14
It sounds like you have the storage group problem. Refer to this link:

[http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide]("http://www.mythtv.org/wiki/MythVideo_.22_Transition_Guide")

A quick test would be to see if you have storage group setup in mythtv backend and remove it and retest your video.

---

### Post by benlyboy on 2010-01-14
Im having the same problem. 

If the videos are in the storage group "videos" I can't watch them, even though they show up in the menu. 

If I move the videos to a folder in my user directory and point to in in the frontend setting then I can watch them.

I guess I'm just not understanding this.

Are the recordings meant to be stored in the storage group or not? 

And if not what is these group for? 

If they are meant to be stored there, how should the player be configured so it can play them?

---

### Post by bbruenfl on 2010-01-15
> **benlyboy said:**
> 
If I move the videos to a folder in my user directory and point to in in the frontend setting then I can watch them.


I directed mythVideo to a different folder with videos and I was able to watch them.  Unfortunately the other components (covers, fanart, trailers, etc) are also broken in the same way.

I have a few hours this morning, I'm going to look for a proper solution.

---

### Post by benlyboy on 2010-01-15
if you come up with anything let me know 


thanks

---

### Post by williammanda on 2010-01-15
> **bbruenfl said:**
> I directed mythVideo to a different folder with videos and I was able to watch them.  Unfortunately the other components (covers, fanart, trailers, etc) are also broken in the same way.

I have a few hours this morning, I'm going to look for a proper solution.

Here is one possible solution for a frontend / master backend:
1. Remove the video storage group only! Keep the others. If you do not have any others then setup all the artwork storage groups.
2. Edit the video setting in the frontend, general setting, page 1 / 6, so that the entry: Directories that hold videos: /var/lib/mythtv/videos.

Now you should be able to view your videos. If you have a remote frontend you will need to setup NFS on the master backend and the remote frontend. This can be done via the control center. Once this done:
1. edit the /etc/export file on the master backend and add this line:
/var/lib/mythtv/videos    *(ro,async,no_root_squash,no_subtree_check)
2. Make sure you have a folder on the remote frontend: /var/lib/mythtv/videos
3. Edit the /etc/fstab file on the remote frontend and add this line:
192.168.1.101:/var/lib/mythtv/videos /var/lib/mythtv/videos nfs rsize=8192,wsize=8192,timeo=14,intr
The ip address should be the one for your master backend.
4. Reboot the master backend and when it is up reboot the remote frontend

Now you should be able to view videos on both frontends. In either case you will need to add the artwork by going to the video manager and selecting "w" for each video.

This isn't the only way but it works for me.

---

### Post by bbruenfl on 2010-01-15
At this point I'm simply running both the front and back end on a single box without any other front ends so I can't test the solution proposed by williamanda.

The solution I've settled on, but am not terribly happy with, is to set the directories for storage groups to /, assure the backend I know what I'm doing (even though I don't), set the source directories in the front end to the correct locations, and go through my entire video collection pressing w and making the necessary corrections to the metadata.

A thought occurred to me as I fumbled around this morning, I installed a fresh 9.10 64bit OS then, using Synaptic, updated the system and installed the mythtv packages and dependencies because the solution I found for getting my sound outputs to work used tools I couldn't find in the xfce interface.  I wonder if there is a configuration change that needs to be made to the main distro that the synaptic installation procedure doesn't catch.

I have a good mind to reinstall with the mythbuntu image to see if I can get a clue as to the problem.  I have a 30gb drive lying around here somewhere that would do nicely for a test...so much for working today. :D

---

### Post by williammanda on 2010-01-15
> **bbruenfl said:**
> At this point I'm simply running both the front and back end on a single box without any other front ends so I can't test the solution proposed by williamanda.

Yes you can...that was the first setup. Just follow the first two steps.

---

### Post by bbruenfl on 2010-01-15
Woo Fricken HOO!

OK, I found the problem.  Drum roll?  It was a permissions issue.

The automagic volume mounter for ntfs volumes loads the drive using root as owner and plugdev as group.  That's cool but it uses umask=007 to restrict access to user and group.  I'm assuming the backend doesn't fall into the plugdev group so it couldn't read the directories nor the files.  Further, I couldn't change permissions or ownership for any of the files on the volume.

So, the solution I used was to give read and execute permissions for the mounted volume to everyone by using umask=002. (7-2=5)

As a side note I successfully mounted the volume using mythtv as group but that didn't work either.

Thanks for everyones help and ideas.

---

### Post by benlyboy on 2010-01-16
bbruenfl it sounds like you may have crack it.


But can you give more detail on how you fixed it....

I am new to this and a step by step would be very very helpful 

thanks

---

