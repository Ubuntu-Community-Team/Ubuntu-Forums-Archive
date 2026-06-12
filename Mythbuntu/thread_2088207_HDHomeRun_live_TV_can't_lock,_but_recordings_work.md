---
title: "HDHomeRun live TV can't lock, but recordings work"
date: 2012-11-25
forum: Mythbuntu
---

### Post by davidstoll on 2012-11-25
I have a strange situation where I can't get a lock on channels when I try live tv, but if I use the channel guide to set a recording, the show records and plays back just fine.

I've even set 2 shows to record at the same time using the HDHomeRun and they record fine.  I was thinking that maybe one tuner was goofed up, but that doesn't appear to be the case.

How do I go about troubleshooting this?  I've checked the backend, but I don't see anything suspicious.

---

### Post by BicyclerBoy on 2012-11-26
Start the frontend with extra verbose logging..

There is a separate fast-tuning option for liveTV & recording..
Fast tuning is less reliable..

Did you see this in the mailing-list
[http://www.mythtv.org/pipermail/mythtv-users/2012-September/339163.html](http://www.mythtv.org/pipermail/mythtv-users/2012-September/339163.html)

---

### Post by davidstoll on 2012-11-26
> **BicyclerBoy said:**
> Start the frontend with extra verbose logging..

There is a separate fast-tuning option for liveTV & recording..
Fast tuning is less reliable..

Did you see this in the mailing-list
[http://www.mythtv.org/pipermail/mythtv-users/2012-September/339163.html](http://www.mythtv.org/pipermail/mythtv-users/2012-September/339163.html)

It seems that guy had low signal on his cable, but in any case, I did change the fast tuning to "never".  It was set to always, but it didn't help.

Here is the verbose log.  The issue I replicated was when changing to channel 3_1.  I looked through for when I attempted to change to channel 3_1, but it is a bit greek to me reading through this.

---

### Post by BicyclerBoy on 2012-11-26
The backend is what controls the tuners..
The FE log seems to show that a "failed to open socket" error

The end of that thread suggests signal level is not the cause..

So need to see part of the BE log..

You might want to go into the theme chooser & update the themes you have used.

---

### Post by davidstoll on 2012-11-26
> **BicyclerBoy said:**
> The backend is what controls the tuners..
The FE log seems to show that a "failed to open socket" error

The end of that thread suggests signal level is not the cause..

So need to see part of the BE log..

You might want to go into the theme chooser & update the themes you have used.

Oh, yeah, I see that.  I updated the theme to the new version.  Thanks.

Here is a chunk of the backend log from /var/log/mythtv/mythbackend.log at a time when I re-created the issue.

```
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 1)
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 22:59:58 MythBuntu mythbackend[4335]: I ProcessRequest recorderbase.cpp:386 (GetKeyframePositions) RecBase(3:/home/david/dev/videocable2): GetKeyframePositions(691,9223372036854775807,#11) out of 57
Nov 26 23:02:55 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 23:02:55 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 23:02:55 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 23:02:55 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 1)
Nov 26 23:02:58 MythBuntu mythbackend[4335]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Nov 26 23:03:36 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:36 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 23:03:36 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:3720 (HandleRecorderQuery) MainServer::HandleRecorderQuery() Unknown encoder: 6
Nov 26 23:03:36 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(7): Changing from None to WatchingLiveTV
Nov 26 23:03:36 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(7): HW Tuner: 7->7
Nov 26 23:03:36 MythBuntu mythbackend[4335]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/home/david/dev/videoHDPVR): SetInputAndFormat(6, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Nov 26 23:03:36 MythBuntu mythbackend[4335]: W TVRecEvent channelbase.cpp:675 (HandleScript) ChannelBase(7): A channel changer is set, but the freqid field is empty.#012#011#011#011We will return success to ease setup pains, but no script is will actually run.
Nov 26 23:03:36 MythBuntu mythbackend[4335]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 10 min
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9a4c768)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab7488)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9aa9520)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9aba098)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9a7b1f0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab96d0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99a2858)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99a5a78)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab2930)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab1a08)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab6ee0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99f31e0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab72a8)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9abb9a8)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99f04d0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99fb808)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99fb918)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99face0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9abbee8)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab9d60)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab2050)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab51e8)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab3dd8)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ab2ff0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9a1d470)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x99e9200)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1477 (HandleAnnounce) adding: mythbuntu as a remote file transfer
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:6068 (LocalFilePath) ERROR: LocalFilePath unable to find local path for 'none'.
Nov 26 23:03:37 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:1547 (HandleAnnounce) Empty filename, cowardly aborting!
Nov 26 23:03:37 MythBuntu mythbackend[4335]: W Socket mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9a1ca48)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: mythbuntu as a client (events: 0)
Nov 26 23:03:37 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1475 (HandleAnnounce) MainServer::HandleAnnounce FileTransfer
Nov 26 23:03:42 MythBuntu mythbackend[4335]: E ProcessRequest mainserver.cpp:3720 (HandleRecorderQuery) MainServer::HandleRecorderQuery() Unknown encoder: 6
Nov 26 23:03:44  mythbackend[4335]: last message repeated 4 times
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(7): Changing from WatchingLiveTV to None
Nov 26 23:03:44 MythBuntu mythbackend[4335]: E RecThread mpegrecorder.cpp:1017 (run) MPEGRec(/home/david/dev/videoHDPVR): Device EOF detected
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:816 (FinishedRecording) TVRec(7): FinishedRecording(10000_2012-11-26T23:03:38) damaged recq:<RecordingQuality overall_score="0" key="10000_2012-11-26T23:03:38" countinuity_error_count="0" packet_count="10530">#012    <Gap start="2012-11-26T23:03:44" end="2012-11-26T23:30:00" duration="1576" />#012</RecordingQuality>
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Playback
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(5): Changing from None to WatchingLiveTV
Nov 26 23:03:44 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:3495 (TuningCheckForHWChange) TVRec(5): HW Tuner: 5->5
Nov 26 23:03:44 MythBuntu mythbackend[4335]: N CoreContext autoexpire.cpp:263 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 9 min
Nov 26 23:03:44 MythBuntu mythbackend[4335]: W ProcessRequest mainserver.cpp:5801 (connectionClosed) MainServer: Unknown socket closing MythSocket(0x9ad78f0)
Nov 26 23:03:44 MythBuntu mythbackend[4335]: E ProcessRequest mythsocket.cpp:358 (writeStringList) MythSocket(9ad78f0:-1): writeStringList: Error, socket went unconnected.#012#011#011#011We wrote 0 of 10 bytes with 1 errors#012#011#011#011starts with: 2       ok
Nov 26 23:03:51 MythBuntu mythbackend[5562]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Nov 26 23:03:52 MythBuntu mythbackend[4335]: I TVRecEvent tv_rec.cpp:1029 (HandleStateChange) TVRec(5): Changing from WatchingLiveTV to None
Nov 26 23:04:45 MythBuntu mythbackend[4335]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 10000 at 2012-11-26T23:03:36 => Unknown
Nov 26 23:04:45 MythBuntu mythbackend[4335]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 1 MB for 10000 at 2012-11-26T23:03:38 => Unknown
Nov 26 23:05:32 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 23:05:32 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 0)
Nov 26 23:05:32 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1360 (HandleAnnounce) MainServer::ANN Monitor
Nov 26 23:05:32 MythBuntu mythbackend[4335]: I ProcessRequest mainserver.cpp:1362 (HandleAnnounce) adding: MythBuntu as a client (events: 1)
```

---

### Post by BicyclerBoy on 2012-11-27
This looks suspect ?
```

Nov 26 23:03:36 MythBuntu mythbackend[4335]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/home/david/dev/videoHDPVR): SetInputAndFormat(6, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Nov 26 23:03:36 MythBuntu mythbackend[4335]: W TVRecEvent channelbase.cpp:675 (HandleScript) ChannelBase(7): A channel changer is set, but the freqid field is empty.#012#011#011#011We will return success to ease setup pains, but no script is will actually run.

```

Do you have to use a channel changer script with HDHomerun ? I don't think that is right..

The backend is showing a similar socket error..
I don't know what that really means.
You have a livetv storage group setup on the backend partnered with the network tuner ?

Does that livetv storage group have any files in it ?

---

### Post by nickrout on 2012-11-27
> **BicyclerBoy said:**
> This looks suspect ?
```

Nov 26 23:03:36 MythBuntu mythbackend[4335]: I TVRecEvent v4lchannel.cpp:661 (SetInputAndFormat) V4LChannel(/home/david/dev/videoHDPVR): SetInputAndFormat(6, NTSC) (v4l v2) input_switch: 0 mode_switch: 0
Nov 26 23:03:36 MythBuntu mythbackend[4335]: W TVRecEvent channelbase.cpp:675 (HandleScript) ChannelBase(7): A channel changer is set, but the freqid field is empty.#012#011#011#011We will return success to ease setup pains, but no script is will actually run.

```

Do you have to use a channel changer script with HDHomerun ? I don't think that is right..

The backend is showing a similar socket error..
I don't know what that really means.
You have a livetv storage group setup on the backend partnered with the network tuner ?

Does that livetv storage group have any files in it ?It looks quite wrong that it is referring to a device that seems to be an HDPVR!

In fact an HDHR doesn't have a device anyway, it is accessed over your network.

---

### Post by davidstoll on 2012-11-27
> **nickrout said:**
> It looks quite wrong that it is referring to a device that seems to be an HDPVR!

In fact an HDHR doesn't have a device anyway, it is accessed over your network.

The HDPVR is linked to a device.

The HDHomeRun is linked to an IP.

For some reason (I believe because of the order by which I added my tuner cards), the HDPVR is the first one it tries.  After it's initial live TV tune (to the HDPVR), I changed the channel to 3_1 which is an OTA channel on the HDHomeRun.

And yes, the HDPVR requires a channel change script.  The HDHomeRun does not have a channel change script.

The reason I use a symbolic link for my tuner devices is because the devices seem to load in random orders each time the computer reboots, so I have to run the backend to correct it.  The symbolic links seem to track that.  But in any case the HDHomeRun does not use a dev, it is set to an IP.

---

### Post by nickrout on 2012-11-27
> **davidstoll said:**
> The HDPVR is linked to a device.

The HDHomeRun is linked to an IP.

For some reason (I believe because of the order by which I added my tuner cards), the HDPVR is the first one it tries.  After it's initial live TV tune (to the HDPVR), I changed the channel to 3_1 which is an OTA channel on the HDHomeRun.

And yes, the HDPVR requires a channel change script.  The HDHomeRun does not have a channel change script.

The reason I use a symbolic link for my tuner devices is because the devices seem to load in random orders each time the computer reboots, so I have to run the backend to correct it.  The symbolic links seem to track that.  But in any case the HDHomeRun does not use a dev, it is set to an IP.so you are switching tuners, i don't think that was clear on your earlier posts!

At which line of your output do you switch to the hdhr?

If you switch to another channel on the hdpvr does it work?

If you start live tv on the hdhr does it work? and can you then switch to another channel?

---

### Post by davidstoll on 2012-11-27
> **nickrout said:**
> so you are switching tuners, i don't think that was clear on your earlier posts!

At which line of your output do you switch to the hdhr?

If you switch to another channel on the hdpvr does it work?

If you start live tv on the hdhr does it work? and can you then switch to another channel?

I can not tune live tv with the HDHR.  The HDPVR works just fine.  It doesn't really change channels because it is connected to a static device (WDLive or Roku or whatever), but it still requires a channel change script of /bin/true or an actual channel change script if you are using a cable set top box.

I can change to another input, which is an analog PCI tuner card and that works on live tv just fine.

However, like I mentioned before, the HDPVR is always the first device that is tuned and I must change to a different input from there...whether it be the analog card or my HDHR.

I'm not sure which line in the log is the change to the HDHR, but it is right after it first automatically tunes to the HDPVR.  In respect to time, it is probably within 5 seconds after that.

---

### Post by BicyclerBoy on 2012-11-28
I don't have one of these devices..
The HDHomerun only works by IP address if the device is always given the same IP from DHCP server or the HDHomerun is setup with fixed static IP (or both).

[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)
suggests using the unique device ID..

Have you configured that device with fixed IP?

Are you sharing the HDHomerun tuners with other applications outside of "connected" backend ?

Maybe the problems relate to the random tuner ordering on reboot.
The soln to that is udev rules or modprobe options.

Are you using mythtv-setup to rearrange the tuners on a regular basis?

From a very limited use of udev rules:
modprobe options are simple & readable but not very flexible.
udev rules look more complicated than they are but have pedantic syntax

I would try to find a working example udev rule & use it as a template.
[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

Interesting info here **but don't blindly copy any cmds**..
[http://www.silicondust.com/forum/viewtopic.php?t=13398](http://www.silicondust.com/forum/viewtopic.php?t=13398)

---

### Post by davidstoll on 2012-11-28
> **BicyclerBoy said:**
> I don't have one of these devices..
The HDHomerun only works by IP address if the device is always given the same IP from DHCP server or the HDHomerun is setup with fixed static IP (or both).

[http://www.mythtv.org/wiki/Silicondust_HDHomeRun](http://www.mythtv.org/wiki/Silicondust_HDHomeRun)
suggests using the unique device ID..

Have you configured that device with fixed IP?

Are you sharing the HDHomerun tuners with other applications outside of "connected" backend ?

Maybe the problems relate to the random tuner ordering on reboot.
The soln to that is udev rules or modprobe options.

Are you using mythtv-setup to rearrange the tuners on a regular basis?

From a very limited use of udev rules:
modprobe options are simple & readable but not very flexible.
udev rules look more complicated than they are but have pedantic syntax

I would try to find a working example udev rule & use it as a template.
[http://www.mythtv.org/wiki/Device_Filenames_and_udev](http://www.mythtv.org/wiki/Device_Filenames_and_udev)

Interesting info here **but don't blindly copy any cmds**..
[http://www.silicondust.com/forum/viewtopic.php?t=13398](http://www.silicondust.com/forum/viewtopic.php?t=13398)

The devices has a fixed IP based on the MAC in my router...as does basically everything in my network.

The random tuner loading will affect some devices, but it will affect live tv the same as a scheduled recording.  When that problem occurs, it is easily noticed and fixable.  This is why I use the symbolic links to point to the devices.  I've been doing this for some time.  I did setup udev rules a while back, but it is a little bit of a pain each time I re-install and found that symbolic links gave me the same satisfactory result.

I only have to re-arrange the device's in the backend setup if I don't have udev or symbolic links setup to properly deal with an otherwise random loading of the devices.

With all of that being said, the HDHomeRun is not a /dev, but rather setup as an IP.  I know that you know that, but for clarification, messing with the udev or symbolic links for the devices isn't going to help the situation with the HDHomeRun live tv because it isn't a video "dev".  However, I appreciate the suggestion of udev.

In any case, the live TV tuning of the HDHomeRun is just not locking, whereas a scheduled recording seems to work fine...on both tuners no less.

---

### Post by nickrout on 2012-11-28
> **davidstoll said:**
> The devices has a fixed IP based on the MAC in my router...as does basically everything in my network.

The random tuner loading will affect some devices, but it will affect live tv the same as a scheduled recording.  When that problem occurs, it is easily noticed and fixable.  This is why I use the symbolic links to point to the devices.  I've been doing this for some time.  I did setup udev rules a while back, but it is a little bit of a pain each time I re-install and found that symbolic links gave me the same satisfactory result.

I only have to re-arrange the device's in the backend setup if I don't have udev or symbolic links setup to properly deal with an otherwise random loading of the devices.

With all of that being said, the HDHomeRun is not a /dev, but rather setup as an IP.  I know that you know that, but for clarification, messing with the udev or symbolic links for the devices isn't going to help the situation with the HDHomeRun live tv because it isn't a video "dev".  However, I appreciate the suggestion of udev.

In any case, the live TV tuning of the HDHomeRun is just not locking, whereas a scheduled recording seems to work fine...on both tuners no less.FWIW my HDHR works on liveTv as well as recordings, did a stress test on the network and had 4 frontends doing livetv (I have 2 hdhrs).

It may be something to do with switching from the hdpvr to the hdhr. 

What happens if you go hdpvr-->pci card--->hdhr?

You could also set the livetv starting channel to something from the hdhr (in mythtv-setup) and see if it works.

---

### Post by davidstoll on 2012-11-28
> **nickrout said:**
> FWIW my HDHR works on liveTv as well as recordings, did a stress test on the network and had 4 frontends doing livetv (I have 2 hdhrs).

It may be something to do with switching from the hdpvr to the hdhr. 

What happens if you go hdpvr-->pci card--->hdhr?

You could also set the livetv starting channel to something from the hdhr (in mythtv-setup) and see if it works.

when I go hdpvr-->pci card (analog)-->hdhr I do have the same issue.

Where is it that I set the start channel?  I can't seem to find the setting?

---

### Post by davidstoll on 2012-12-01
Well, I seem to have the HDHomeRun working again.  I had to remove it and re-add it, although, it just so happened I did it a couple of times as I was trying to sort out the order of which tuner starts with live tv first...but it is working now!

Any ideas on how to change with tuner is chosen at start?

I changed the priority numbers all around.  I even loaded one HDHomeRun tuner before and one after adding the HDPVR as a tuner.

---

### Post by topcat5 on 2012-12-01
My recommendation is that you don't use the DVB driver to configure the HD Homerun and instead use the MythTV direct interface to the device.  I found the random loading of the drivers can cause lockups and lost recordings and/or failure to tune a live TV channel.   The problem is magnified greatly if you have more than one hdhomerun or another DVB device in the BE.   

Silicon Dust is aware of the issue and says they might release an update to fix it, but so far there is no date.

---

### Post by davidstoll on 2012-12-01
> **topcat5 said:**
> My recommendation is that you don't use the DVB driver to configure the HD Homerun and instead use the MythTV direct interface to the device.  I found the random loading of the drivers can cause lockups and lost recordings and/or failure to tune a live TV channel.   The problem is magnified greatly if you have more than one hdhomerun or another DVB device in the BE.   

Silicon Dust is aware of the issue and says they might release an update to fix it, but so far there is no date.

I thought I was using the MythTV (backend) interface to configure the device...I guess I need clarification.

---

### Post by topcat5 on 2012-12-01
I couldn't tell from your post.  One of the posts above had instructions for installing the kernal drivers for the HDHomerun.  If you do this then the device is configured like a DVB device instead of a HDHomerun device.   

If using DVB your HD Homerun tuner would appear as something like 
[INDENT]/dev/dvb/adapter0/frontend0[/indent]
If using the Myth driver then it appears as 
[indent]HDHOMERUN : nnnnannn-0[/indent]

It's the DVB case that causes the issue if you have more than one hardware tuner configured.

---

### Post by nickrout on 2012-12-01
> **topcat5 said:**
> I couldn't tell from your post.  One of the posts above had instructions for installing the kernal drivers for the HDHomerun.  If you do this then the device is configured like a DVB device instead of a HDHomerun device.   

If using DVB your HD Homerun tuner would appear as something like 
[INDENT]/dev/dvb/adapter0/frontend0[/indent]
If using the Myth driver then it appears as 
[indent]HDHOMERUN : nnnnannn-0[/indent]

It's the DVB case that causes the issue if you have more than one hardware tuner configured.

There is no suggestion that he is using the hdhomerun dvb drivers. He has a separate dvb card.

---

### Post by davidstoll on 2012-12-01
> **topcat5 said:**
> I couldn't tell from your post.  One of the posts above had instructions for installing the kernal drivers for the HDHomerun.  If you do this then the device is configured like a DVB device instead of a HDHomerun device.   

If using DVB your HD Homerun tuner would appear as something like 
[INDENT]/dev/dvb/adapter0/frontend0[/indent]
If using the Myth driver then it appears as 
[indent]HDHOMERUN : nnnnannn-0[/indent]

It's the DVB case that causes the issue if you have more than one hardware tuner configured.

Oh, ok, I see.  No, the HDHomeRun is not a /dev/.....

---

### Post by topcat5 on 2012-12-03
> **nickrout said:**
> There is no suggestion that he is using the hdhomerun dvb drivers. He has a separate dvb card.

Actually the instructions for configuring the HDhomerun as a dvb device are given above.  As I said in my post, I said I couldn't tell if he followed them or not.  As it seems now, I can see that he didn't.  

Still it's worth noting because it causes a similar issue if there is more than one tuner available to the system.

---

### Post by pjbgravely on 2012-12-03
> **davidstoll said:**
> Well, 

Any ideas on how to change with tuner is chosen at start?



Mythbackend setup / input connections /choose tuner/ second page/  live tv order, 1 for tuner you want, 2 and up for all other tuners. It took me bit to figure that out LOL.

---

### Post by davidstoll on 2012-12-11
> **pjbgravely said:**
> Mythbackend setup / input connections /choose tuner/ second page/  live tv order, 1 for tuner you want, 2 and up for all other tuners. It took me bit to figure that out LOL.

My OTA (HDHomeRun) is a 1 (both tuners), my analog tuners are a 3 and my HDPVR is a 5.

It still tunes the HDPVR first.  I reordered just to see what would happen, but it didn't help.

And my HDHomeRun still won't tune live TV, but records just fine. :(

---

### Post by topcat5 on 2012-12-11
I was going to try an run a scan and do some logging to see what was going on and it started to work again.  I don't have an explanation for it except that I have installed the next update and rebooted.

---

### Post by davidstoll on 2012-12-12
> **topcat5 said:**
> I was going to try an run a scan and do some logging to see what was going on and it started to work again.  I don't have an explanation for it except that I have installed the next update and rebooted.

Are you talking about live tv tuning on the HDHomeRun or the tuner order?

My main issue is not being able to tune live TV with my HDHomeRun.

---

