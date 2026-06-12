---
title: "Video stuttering: messages about RingBuf, waiting for data"
date: 2012-12-03
forum: Mythbuntu
---

### Post by Erik-NA on 2012-12-03
I'm having playback issues for liveTV on a separated two frontend with one backend mythbuntu 12.04 system using MythTV 0.26-0 with latest update from PPA.

```
Dec  3 20:37:19 myth mythlogserver: mythbackend[2641]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/mythtv/livetv/2409_20121203193057.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 360448
Dec  3 20:37:23 myth mythlogserver: mythbackend[2641]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/mythtv/livetv/2027_20121203193426.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 129780 < 131072
Dec  3 20:37:36 myth mythlogserver: mythbackend[2641]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/mythtv/livetv/2409_20121203193057.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 327680 < 360448
Dec  3 20:37:36 myth mythlogserver: mythbackend[2641]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/mythtv/livetv/2409_20121203193057.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 65536 < 360448
```

I have moved default storage group including liveTV-dir to a separate SSD with a xfs file system. 
When watching live HD-channels liveTV stutters when messages above are written to the log.

I have read the other thread about ringbuf causing video buffers. It seems to be a different problem?

Backend:
MythTV Version0.26.0+fixes.20121203.b28041a-0ubuntu0mythbuntu2 
Motherboard: Gigabyte PH67-UD3-B3
CPU: Intel(R) Core(TM) i3-2100T CPU @ 2.50GHz
Harddrives: two Intel X25M SSD, one for OS, one for default storage
2:0.26.0+fixes.20121203.b28041a-0ubuntu0mythbuntu2
Memory: 8GB
DVB-S: TBS 6984 - quad tuner card

Frontend: Two Asrock nettop ION 3D 1.8 2GB/320GB harddrive using VDPAU

---

### Post by nickrout on 2012-12-03
Does the stuttering continue if you pause for a few seconds and then resume? There was a bug at one stage where the playback was following the recording too closely and running out of data.

---

### Post by Erik-NA on 2012-12-03
Yes, the stuttering continues if I pause for a few seconds and then resume. :(

If I download a  live recording from the livetv directory and watch it in VLC on Windows, the stuttering is visible in the recording.

I shall make a test with mplayer to verify that the DBS S2 signal to MythTV is not the cause.

---

### Post by nickrout on 2012-12-03
So it appears to be a recording issue, not a playback issue.

Could be bad reception (check antenna and all cables), bad network between your tuner and your backend (if it is a network tuner), bad IO or backend otherwise swamped. What does iotop tell you?

---

### Post by uteck on 2012-12-04
I have a similar problem on my 12.04 system running the fixes .26 ppa.  I can't use the frontends at the same time anymore to watch Live TV while the other is watching a recording.  This worked fine before, but seems to have crept into an update sometime in the last month or so.  They both stutter and buffer then live tv errors out with a ring buffer error, then the recording playback resumes.

I have a dedicated backend, and the only thing I can think of is that maybe the ext4 partition were the recordings and live tv buffer is having an issue?  When I rebuilt the system about 2 years I took the default option of using ext4 and not xfs.

---

### Post by Erik-NA on 2012-12-05
> **nickrout said:**
> So it appears to be a recording issue, not a playback issue.

Could be bad reception (check antenna and all cables), bad network between your tuner and your backend (if it is a network tuner), bad IO or backend otherwise swamped. What does iotop tell you?

I have repositioned my PCI and PCIe cards to allow the DVB-card to have its own interrupt. I cannot see anything strange with iotop. The stuttering is still there, so reposition the DVB-card did not solved my problem.

I am going to check the input signal from LNB, but due to bad weather conditions I have not done that yet.

I am starting to believe that maybe this is an issue in the myth backend recording?

---

### Post by Erik-NA on 2012-12-05
> **uteck said:**
> I have a similar problem on my 12.04 system running the fixes .26 ppa.  I can't use the frontends at the same time anymore to watch Live TV while the other is watching a recording.  This worked fine before, but seems to have crept into an update sometime in the last month or so.  They both stutter and buffer then live tv errors out with a ring buffer error, then the recording playback resumes.

I have a dedicated backend, and the only thing I can think of is that maybe the ext4 partition were the recordings and live tv buffer is having an issue?  When I rebuilt the system about 2 years I took the default option of using ext4 and not xfs.

What errors do you have in your mythtv-backend.log? Same as me as in the first post in this thread?

---

### Post by Erik-NA on 2012-12-12
Now I have reinstalled the backend with other motherboard and a newer CPU.I have realigned my sat antenna, check all the cabling an so on. But it did not solved the problem. The video sometimes stutters, even if I download a LiveTv recording and watch it with VLC.

My DVB-S2 card is a PCIe quad tuner card, TBS 6984

HD channels are only affected, I have not seen any stutter on SD channels.

---

### Post by jksj on 2012-12-13
High - looking at your hardware configuration you seem to have most of your disc storage on the frontends. If this is correct the bandwidth on the network while recording could be the cause of the problem.
Alternatively a quad tuner card has the potential to generate very high system loads. I remember seeing a driver update on the TBS website to sort out an interrupt problem. Have you downloaded and built the latest version.
Best of luck.

---

### Post by Erik-NA on 2012-12-13
The backend is equipped with a 3TB Raid 5 disc array. I have configured a 700MB XFS partition to be used as the standard storage group for the mythtv-backend.

I have also changed motherboard to a Asus P8H77-V to get the TBS-card on an own interrupt. And I have also changed CPU to an Intel Core I5 3470S 2,9GHz.

The TBS-card is installed with the latest TBS-drivers, currently v121119. 

I am also investigating if my cable signal is to low since I cannot get higher signallevel than 74% displayed in MythTvFrontend. But there are others reporting that they cannot get higher signal level than 74% using TBS-cards.

I shall also rescan the channels, I notified during last scan that some HD channels got two neighboring SIDs (is it called SID? Or channel numbers?) which is a bit suspicious.

---

### Post by Erik-NA on 2012-12-20
Problem solved. One problem was that the raid-array was to slow when writing. I swapped first to a SSD and now to a singe hard drive (not raid) and that solved a part of the problem.

Some days ago I updated MythTV and my feeling is that the update made some changes in a positive way. The problem is now minimized.

---

### Post by Erik-NA on 2012-12-22
Since last time I posted in this thread, I have taken a few steps forward and some step backwards.

Now I have a singe 2TB harddrive storing both MythTv recordings and live TV.

MythTv has been updated to v0.26.0-64-g637d6d8 some days ago. Stuttering in live Tv has nearly vanished, it appears sometimes, mostly on HD channels.

After upgrading to v0.26.0-64-g637d6d8 recordings are now the victim for worse stuttering than ever before - I cannot watch recordings any longer.

I also having trouble with channel locking. Something is happening sometimes when I am leaving live TV mode or not watching live TV for a couple of hours. After that something has happened, channel locking cannot be done any longer, I have to restart the backend computer.

---

### Post by nickrout on 2012-12-22
2 important words:  log files.

---

### Post by Erik-NA on 2012-12-23
Now I made a short recording which stutters enormously. Below are a section of mythbackend.log where the recording took place.

Watching LiveTv is normal, watching a live Tv recording is also normal.

```

Dec 23 11:32:19 mm mythlogserver: mythbackend[3057]: I CoreContext scheduler.cpp:655 (UpdateRecStatus) Updating status for "Grinchen - julen Ã&#402;Â¤r stulen" on cardid 7 (Tuning => Recording)
Dec 23 11:32:20 mm mythlogserver: mythbackend[3057]: I TVRecEvent tv_rec.cpp:4056 (TuningNewRecorder) TVRec(7): rec->GetPathname(): '/mnt/mythtv/recordings/5109_20121223103200.mpg'
Dec 23 11:32:34 mm mythlogserver: mythbackend[3057]: N Expire autoexpire.cpp:641 (SendDeleteMessages) Expiring 39 MB for 2025 at 2012-12-23T10:30:00Z => "Winx Club"
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:41 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 23 11:32:43 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:43 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 23 11:32:43 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:43 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Grinchen - julen Ã&#402;Â¤r stulen
Dec 23 11:32:57 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Grinchen - julen Ã&#402;Â¤r stulen
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 8871
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: How the Grinch Stole Christmas 0 0
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:32:58 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for MATCH 33 0 0 - PHP
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I Scheduler scheduler.cpp:2232 (HandleReschedule) Reschedule interrupted, will retry
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for PLACE Interrupted
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I Scheduler scheduler.cpp:2241 (HandleReschedule) Scheduled 5 items in 0.0 = 0.00 match + 0.00 check + 0.01 place
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Grinchen - julen Ã&#402;Â¤r stulen
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Grinchen - julen Ã&#402;Â¤r stulen
Dec 23 11:33:04 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -D 8871
Dec 23 11:33:05 mm mythlogserver: mythbackend[3057]: I MetadataDownload metadatadownload.cpp:144 (run) Returning Metadata Results: How the Grinch Stole Christmas 0 0
```

---

### Post by Erik-NA on 2012-12-23
Sorry for this. You made me check my adapters. I have four of them. 

Watching Live Tv is using adapters in the following seuqence 1,2,3 and 4. While recordings are using adapters in the following seuqence 4, 3, 2 and 1.

Swapping live tv adapter in frontend to adapter 4 revealed why recordings are stuttering, the fourth adapter is faulty, probably due to a bad connection to my sat dish.

---

### Post by Erik-NA on 2012-12-25
Now I have located and fixed the bad cabling. It is working much better now :)

However, when watching HD channels live on two frontends simultaneously as I am recording two HD channels makes live TV stutter sometimes. 

Here is the ringbuffer *information* message. It is a lot of them. Can they have something to do with the stuttering? Or something else? 

And what are the ringbuf (WaitForAvail) meaning in a technically point of view? 

```
Dec 25 14:15:12 mm mythlogserver: mythbackend[3237]: I TVRecEvent tv_rec.cpp:4056 (TuningNewRecorder) TVRec(5): rec->GetPathname(): '/mnt/mythtv/recordings/5208_20121225131500.mpg'
Dec 25 14:15:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
Dec 25 14:15:27 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:15:31 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 458752
Dec 25 14:15:34 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
Dec 25 14:15:43 mm mythlogserver: mythbackend[3237]: E DVBRead mpeg/mpegstreamdata.cpp:360 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Dec 25 14:15:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 393216 < 458752
Dec 25 14:15:46 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:15:48 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 98304 < 458752
Dec 25 14:15:49 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 458752
Dec 25 14:15:50 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 163840 < 458752
Dec 25 14:15:51 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 229376 < 458752
Dec 25 14:15:52 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 425984 < 458752
Dec 25 14:15:53 mm mythlogserver: mythbackend[3237]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Dec 25 14:15:56 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:16:02 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 327680 < 458752
Dec 25 14:16:05 mm mythlogserver: mythbackend[3237]: E DVBRead mpeg/mpegstreamdata.cpp:360 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Dec 25 14:16:07 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Dec 25 14:16:07 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2232 (HandleReschedule) Reschedule interrupted, will retry
Dec 25 14:16:07 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for PLACE Interrupted
Dec 25 14:16:07 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2241 (HandleReschedule) Scheduled 2 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Dec 25 14:16:08 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 65536 < 458752
Dec 25 14:16:16 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 98304 < 458752
Dec 25 14:16:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:16:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 425984 < 458752
Dec 25 14:16:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 425984 < 458752
Dec 25 14:16:18 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:16:19 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 425984 < 458752
Dec 25 14:16:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:16:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:16:43 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 229376 < 458752
Dec 25 14:16:53 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 229376 < 458752
Dec 25 14:16:57 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:16:59 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:17:03 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: E ProcessRequest programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(2406_20121224174500.mpg): GetPlaybackURL: '2406_20121224174500.mpg' should be local, but it can not be found.
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: E HttpServer100 programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(2406_20121224174500.mpg): GetPlaybackURL: '2406_20121224174500.mpg' should be local, but it can not be found.
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:15 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 25 14:17:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 25 14:17:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 25 14:17:17 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:17:21 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -N Chihuahuan frÃƒÂ¥n Beverly Hills (HD)
Dec 25 14:17:22 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Chihuahuan frÃƒÂ¥n Beverly Hills
Dec 25 14:17:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 327680 < 458752
Dec 25 14:17:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 25 14:17:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:23 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for MATCH 38 0 0 - PHP
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2241 (HandleReschedule) Scheduled 2 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:29 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -N Chihuahuan frÃƒÂ¥n Beverly Hills (HD)
Dec 25 14:17:29 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Chihuahuan frÃƒÂ¥n Beverly Hills
Dec 25 14:17:30 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: E ProcessRequest programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(2406_20121224174500.mpg): GetPlaybackURL: '2406_20121224174500.mpg' should be local, but it can not be found.
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:33 mm mythlogserver: mythbackend[3237]: E HttpServer100 programinfo.cpp:2284 (GetPlaybackURL) ProgramInfo(2406_20121224174500.mpg): GetPlaybackURL: '2406_20121224174500.mpg' should be local, but it can not be found.
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Livet pÃƒÂ¥ savannen
Dec 25 14:17:39 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Livet pÃƒÂ¥ savannen
Dec 25 14:17:40 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:40 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 0)
Dec 25 14:17:40 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:40 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 1)
Dec 25 14:17:40 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 458752
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for MATCH 39 0 0 - PHP
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I Scheduler scheduler.cpp:2241 (HandleReschedule) Scheduled 2 items in 0.0 = 0.00 match + 0.00 check + 0.00 place
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1395 (HandleAnnounce) MainServer::ANN Monitor
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest mainserver.cpp:1397 (HandleAnnounce) adding: mm as a client (events: 2)
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Movie/tmdb.py -l en -M Livet pÃƒÂ¥ savannen
Dec 25 14:17:44 mm mythlogserver: mythbackend[3237]: I MetadataDownload metadatadownload.cpp:222 (runGrabber) Running Grabber: /usr/share/mythtv/metadata/Television/ttvdb.py -l en -M Livet pÃƒÂ¥ savannen
Dec 25 14:17:50 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:17:50 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:17:55 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:17:55 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 327680 < 458752
Dec 25 14:17:57 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 32768 < 458752
Dec 25 14:17:59 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:18:08 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
Dec 25 14:18:10 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:18:28 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:18:28 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:18:32 mm mythlogserver: mythbackend[3237]: E DVBRead dtvrecorder.cpp:808 (FindH264Keyframes) DTVRec(1): PES start code not found in TS packet with PUSI set
Dec 25 14:18:33 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 458752
Dec 25 14:18:35 mm mythlogserver: mythbackend[3237]: E DVBRead mpeg/mpegstreamdata.cpp:360 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Dec 25 14:18:35 mm mythlogserver: mythbackend[3237]: E DVBRead mpeg/mpegstreamdata.cpp:360 (AssemblePSIP) Error: offset>181, pes length & current cannot be queried
Dec 25 14:18:36 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
Dec 25 14:18:42 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:18:48 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:18:58 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 340564 < 458752
Dec 25 14:18:58 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 340564 < 458752
Dec 25 14:18:59 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 340564 < 458752
Dec 25 14:19:00 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 2.0 seconds for data #012#011#011#011to become available... 340564 < 458752
Dec 25 14:19:06 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 393216 < 458752
Dec 25 14:19:10 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 163840 < 458752
Dec 25 14:19:13 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 229376 < 458752
Dec 25 14:19:13 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 458752
Dec 25 14:19:24 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 294912 < 458752
Dec 25 14:19:25 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:19:26 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
Dec 25 14:19:30 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 458752
Dec 25 14:19:35 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 458752
Dec 25 14:19:43 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2406_20121225130843.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 425984
Dec 25 14:19:44 mm mythlogserver: mythbackend[3237]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/5102_20121225131042.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 360448 < 458752
```

---

### Post by Erik-NA on 2012-12-25
There are a lot of ringbuf i my log now. Only watching one HD channel now. No stuttering.
Is curios about what this ringbuf really means. Is it related to hard disc IO or is it related to the DVB device, reading from the DVB driver etc?

```
Dec 25 17:20:14 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 172240 < 229376
Dec 25 17:20:17 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 200248 < 229376
Dec 25 17:20:22 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 128000 < 229376
Dec 25 17:20:25 mm mythlogserver: mythbackend[9444]: I HouseKeeping housekeeper.cpp:221 (RunHouseKeeping) Running housekeeping thread
Dec 25 17:20:34 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 13496 < 196608
Dec 25 17:21:09 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 177164 < 196608
Dec 25 17:21:19 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 41720 < 163840
Dec 25 17:21:32 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 121652 < 131072
Dec 25 17:21:46 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 193012 < 196608
Dec 25 17:21:54 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 193768 < 229376
Dec 25 17:21:57 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 176988 < 196608
Dec 25 17:22:10 mm mythlogserver: mythbackend[9444]: I Scheduler scheduler.cpp:2128 (HandleReschedule) Reschedule requested for MATCH 0 0 0 - EITScanner
Dec 25 17:22:10 mm mythlogserver: mythbackend[9444]: I Scheduler scheduler.cpp:2241 (HandleReschedule) Scheduled 0 items in 0.0 = 0.01 match + 0.00 check + 0.00 place
Dec 25 17:22:15 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 101728 < 196608
Dec 25 17:22:16 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 103040 < 196608
Dec 25 17:22:16 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 103040 < 196608
Dec 25 17:22:18 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 196608
Dec 25 17:23:05 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 66344 < 163840
Dec 25 17:23:13 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 179384 < 196608
Dec 25 17:23:15 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 180268 < 196608
Dec 25 17:23:31 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 37792 < 98304
Dec 25 17:23:37 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 892 < 360448
Dec 25 17:23:38 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 322268 < 360448
Dec 25 17:23:47 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 269308 < 294912
Dec 25 17:23:48 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 270684 < 294912
Dec 25 17:23:53 mm mythlogserver: mythbackend[9444]: W ProcessRequest ringbuffer.cpp:1035 (WaitForReadsAllowed) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Taking too long to be allowed to read..
Dec 25 17:23:55 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 196608 < 294912
Dec 25 17:23:55 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 32768 < 262144
Dec 25 17:23:58 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 256216 < 393216
Dec 25 17:23:58 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 256216 < 393216
Dec 25 17:23:58 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 1.0 seconds for data #012#011#011#011to become available... 256216 < 393216
Dec 25 17:23:59 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 2796 < 360448
Dec 25 17:24:02 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 185116 < 360448
Dec 25 17:24:02 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 185116 < 360448
Dec 25 17:24:03 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 232392 < 327680
Dec 25 17:24:04 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 232392 < 327680
Dec 25 17:24:04 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 231276 < 327680
Dec 25 17:24:04 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 231276 < 327680
Dec 25 17:24:10 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 116120 < 294912
Dec 25 17:24:10 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 116120 < 294912
Dec 25 17:24:16 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 261556 < 262144
Dec 25 17:24:17 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 254124 < 262144
Dec 25 17:24:23 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 196608 < 229376
Dec 25 17:24:29 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 0 < 229376
Dec 25 17:24:29 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 0 < 229376
Dec 25 17:24:30 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 183148 < 229376
Dec 25 17:24:41 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 196608 < 229376
Dec 25 17:24:42 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 209820 < 229376
Dec 25 17:24:44 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 175288 < 229376
Dec 25 17:24:46 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 65536 < 196608
Dec 25 17:24:54 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 167092 < 196608
Dec 25 17:25:01 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 77880 < 196608
Dec 25 17:25:04 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 99496 < 196608
Dec 25 17:25:04 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 64312 < 196608
Dec 25 17:25:09 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131676 < 196608
Dec 25 17:25:12 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 131072 < 196608
Dec 25 17:25:15 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 195812 < 196608
Dec 25 17:25:23 mm mythlogserver: mythbackend[9444]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/2405_20121225145647.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 262144 < 294912
```

---

### Post by clint01 on 2013-06-08
Hi Erik-na did you ever resolve this I have exactly the same symptoms, video stuttering when watching HD channels and same Ring buffer logs on the backend

mythlogserver: mythbackend[2041]: I ProcessRequest ringbuffer.cpp:1098 (WaitForAvail) RingBuf(/mnt/mythstorage/livetv/1003_20130608114553.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 76088 < 131072

---

### Post by Erik-NA on 2013-08-17
The problem was solved after I changed to better cabling from LNB to my DVB-S card. I also swapped to a bugger dish which increased both signal level and snr.

---

