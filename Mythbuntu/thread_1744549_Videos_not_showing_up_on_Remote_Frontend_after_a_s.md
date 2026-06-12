---
title: "Videos not showing up on Remote Frontend after a scan"
date: 2011-04-30
forum: Mythbuntu
---

### Post by bryan.sailer on 2011-04-30
I have setup NFS on my Master backend and I have mounted to directory on my remote frontend. When I navigate to the mounted diectory the videos are there and the fies up date when I add more videos to my Master backend. When I open the remote frontend I have verified that the correct file is being scanned, but when I scan for videos non of the videos that are in the directory show up. What else do I need to check to get my videos to show up and play on my remote frontend?

Myhtbuntu 10.10

---

### Post by kja999 on 2011-05-01
Is the path to the videos the same  on the client as on the main backend ?

---

### Post by David Grigor on 2011-05-02
What format are the videos in ? Are they iso files ?

---

### Post by bryan.sailer on 2011-05-03
Yes, the file path on the remote frontend is the same as the backend. The file types are mp4. I am connecting over a wireless connection I do not know if that has anything to do with the files not opening.

---

### Post by nickrout on 2011-05-03
why are you using nfs? myth has storage groups for that :)

---

### Post by bryan.sailer on 2011-05-03
I was familiar with nfs so I had set it up prior to researching storage groups. Do I need to disable my nfs exports to have the storage groups share the videos to the remote frontend?

---

### Post by bryan.sailer on 2011-05-03
Ok I went and removed the nfs server and all of the exports. I have also unmounted  the directories on the remote frontend. Now when I go and scan for changes none of the videos show up. I have verified that the directories are the same on the storage group and on the frontend. So what should I check now.

---

### Post by nickrout on 2011-05-03
> **bryan.sailer said:**
> Ok I went and removed the nfs server and all of the exports. I have also unmounted  the directories on the remote frontend. Now when I go and scan for changes none of the videos show up. I have verified that the directories are the same on the storage group and on the frontend. So what should I check now.


In the front end where the videos do not show up, make sure the setting (in mythvideo settings) called "Directories that hold videos" is empty.

You shouldn't need to scan from that frontend if the scan has already been done from another frontend, they all share the same database. scan can be run from any frontend and the movies should show up in all frontends. 

In mythvideo on the errant frontend try some of the browse option, from the menu.

(I assume you are using myth 0.24)

---

### Post by bryan.sailer on 2011-05-03
That was a good point I thought that since I installed from the Ubuntu Software Center on my that I would have installed the latest version. After double checking the version is 0.23.1. I am going to download 0.24 and see what that does. on my Master backend I am running MythBuntu so that should be the lastest version of mythtv correct?

---

### Post by nickrout on 2011-05-03
if you want to use 0.24 you need to use mythbuntu-repos and install 0.24 on the backend first, then the frontend. This is so whether you use mythbuntu, or ubuntu with myth added on.

---

### Post by bryan.sailer on 2011-05-05
W:Failed to fetch [http://ppa.launchpad.net/mythbuntu/0.24.x/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mythbuntu/0.24.x/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

I have added the Mythbuntu repos to my backend and when I attempted to update the above error popped up. What do i need to do now. It appears that 0.24 is not available.

---

### Post by bryan.sailer on 2011-05-06
Ok I do not know why I got error showed up when I first started the upgrade but after trying a second time I now have a backend and remote frontend running 0.24. All of my videos show up on the remote frontend but they still do not play. The file types are .m4v. I am trying to stream the videos over my wireless network. What is my next option to play my videos?

---

### Post by nickrout on 2011-05-07
what does the frontend log say when you try to play a m4v file?

Also the output of mediainfo on one of the files in question might be helpful.

---

### Post by tgm4883 on 2011-05-07
> **bryan.sailer said:**
> Ok I do not know why I got error showed up when I first started the upgrade but after trying a second time I now have a backend and remote frontend running 0.24. All of my videos show up on the remote frontend but they still do not play. The file types are .m4v. I am trying to stream the videos over my wireless network. What is my next option to play my videos?

There was a small error in the package that I've taken care of. You likely upgrade the -repos package with that fix.

---

### Post by bryan.sailer on 2011-05-08
That makes since as to why the upgrade now has fix next to it. 

I have gone to Information Center, System Status, Log Entries and there were no log entries. How do I enable logging so I can troubleshoot my problem of videos not playing?

---

### Post by nickrout on 2011-05-08
the file is /var/log/mythtv/mythfrontend.log

---

### Post by bryan.sailer on 2011-05-08
Thank you, that is what I was looking for. Below is the information that shows up in the log when I try to open a video.

2011-05-07 23:37:54.329 MythVideo::ScanVideoDirectory Scanning Group (myth://Videos@MediaCenter/var/lib/mythtv/videos/)
2011-05-07 23:38:01.740 TV: Attempting to change from None to WatchingVideo
2011-05-07 23:38:03.025 Pulse: PulseAudio suspend OK
2011-05-07 23:38:05.351 RingBuf(myth://Videos@192.168.1.105:6543/Aristocats.m4v): Waited 0.2 seconds for data 
			to become available... 730376 < 854612
2011-05-07 23:38:09.520 AFD Warning: ScanATSCCaptionStreams() called with no PMT
2011-05-07 23:38:09.523 AFD: Opened codec 0x96423f0, id(H264) type(Video)
2011-05-07 23:38:09.523 AFD: codec AAC has 2 channels
2011-05-07 23:38:09.537 AFD: Opened codec 0x9390f50, id(AAC) type(Audio)
2011-05-07 23:38:09.539 AFD Error: Could not find decoder for codec (Unknown Codec ID), ignoring.
2011-05-07 23:38:09.751 Pulse: PulseAudio resume OK
2011-05-07 23:38:10.054 Pulse: PulseAudio suspend OK
2011-05-07 23:38:10.177 AO: Opening audio device 'default' ch 2(2) sr 48000 sf signed 16 bit reenc 0
2011-05-07 23:38:10.196 AudioOutput Warning: mmap not available, attempting to fall back to slow writes
2011-05-07 23:38:10.363 ALSA, Error: no playback control PCM found on mixer device default
2011-05-07 23:38:10.364 ALSA, Error: Unable to open audio mixer. Volume control disabled
2011-05-07 23:38:10.365 AudioPlayer: Enabling Audio
2011-05-07 23:38:11.305 VideoOutputXv: XVideo Adaptor Name: 'Intel(R) Textured Video'
2011-05-07 23:38:11.487 OSD: Base theme size: 1280x720
2011-05-07 23:38:11.489 OSD: Scaling factors: 0.553125x0.663889
2011-05-07 23:38:11.845 OSD: Base theme size: 1280x720
2011-05-07 23:38:11.846 OSD: Scaling factors: 0.553125x0.663889
2011-05-07 23:38:11.900 Player(0): Video timing method: USleep with busy wait
2011-05-07 23:38:11.902 TV: Changing from None to WatchingVideo
2011-05-07 23:38:11.961 ScreenSaverX11Private: DPMS Deactivated 1
2011-05-07 23:38:12.094 VideoOutput: Created YV12 OSD.
2011-05-07 23:38:28.902 Player(0): Waited 100ms for video buffers AAAAAAAAAAAAAAAAAAAUUUUUUUUUuuL

---

### Post by bryan.sailer on 2011-05-22
To have the video file show up on my MythBuntu remote front end I needed to ensure that my master frontend had scanned for updated files. Then I was able to see the videos on my remote frontend. 
I have now switched to using XBMC as my frontend and I like the control and layout better then MythTV. The files are shared using Samba and I have now problems viewing the files. The main reason for the switch is that I do not plan on recording live TV so I did not need that funtionality that MythTV provided. I plan on storing all of my photos, videos and music on my home server and pulling them across my network to my HTPC or any other device that I need to on my network.

---

### Post by nickrout on 2011-05-23
Yes the core fuctionality of mythtv is not needed by you so XBMC can be a good option.

However one thing you will notice is that each instance of XBMC has it's own database, so you need to scan for metadata on each instance. 

By the way there is no concept of "master frontend" on mythtv. You can scan on any frontend and all other frontends can see the results.

---

