---
title: "Frontends crash when opening video"
date: 2011-09-23
forum: Mythbuntu
---

### Post by uteck on 2011-09-23
Both of my frontends have this problem, one is 10.10 and the other 11.4.  When I try to play a video that is stored on my fileserver and shared by a videogroup, the frontend locks then crashes.  The backend is 10.10, and I get this in the backend log:

```
2011-09-23 12:57:03.945 MainServer::ANN Playback
2011-09-23 12:57:03.946 MainServer::ANN Playback
2011-09-23 12:57:03.953 adding: bedroom as a client (events: 0)
2011-09-23 12:57:03.961 adding: bedroom as a client (events: 0)
2011-09-23 12:57:03.970 MainServer::HandleAnnounce FileTransfer
2011-09-23 12:57:03.986 MainServer::HandleAnnounce FileTransfer
2011-09-23 12:57:04.001 adding: bedroom as a remote file transfer
2011-09-23 12:57:04.009 adding: bedroom as a remote file transfer
2011-09-23 12:57:04.034 ERROR: LocalFilePath unable to find local path for '07-Ghost Season 1x1_screenshot.jpg'.
2011-09-23 12:57:04.049 RingBuf() Error: RingBuffer::RingBuffer(): Failed to open remote file ()
2011-09-23 12:57:04.049 ERROR: LocalFilePath unable to find local path for '07-Ghost Season 1x2_screenshot.jpg'.
2011-09-23 12:57:04.066 QueryBasename found no entry for 0 @ 2011-09-23T12:57:04
2011-09-23 12:57:04.080 RingBuf() Error: RingBuffer::RingBuffer(): Failed to open remote file ()
2011-09-23 12:57:04.090 QueryBasename found no entry for 0 @ 2011-09-23T12:57:04
2011-09-23 12:57:04.106 QueryBasename found no entry for 0 @ 2011-09-23T12:57:04
2011-09-23 12:57:04.129 QueryBasename found no entry for 0 @ 2011-09-23T12:57:04
2011-09-23 12:57:04.130 MainServer::ANN Playback
2011-09-23 12:57:04.153 adding: bedroom as a client (events: 0)
2011-09-23 12:57:04.153 MainServer::ANN Playback
2011-09-23 12:57:04.170 MainServer::HandleAnnounce FileTransfer
2011-09-23 12:57:04.176 adding: bedroom as a client (events: 0)
2011-09-23 12:57:04.193 adding: bedroom as a remote file transfer
2011-09-23 12:57:04.210 MainServer::HandleAnnounce FileTransfer
2011-09-23 12:57:04.232 adding: bedroom as a remote file transfer
2011-09-23 12:57:04.225 ERROR: LocalFilePath unable to find local path for '07-Ghost Season 1x3_screenshot.jpg'.
2011-09-23 12:57:04.255 ERROR: LocalFilePath unable to find local path for '07-Ghost Season 1x4_screenshot.jpg'.
2011-09-23 12:57:04.257 RingBuf() Error: RingBuffer::RingBuffer(): Failed to open remote file ()
2011-09-23 12:57:04.272 RingBuf() Error: RingBuffer::RingBuffer(): Failed to open remote file ()
:

```

The ringbuffer errors look odd.  I can see the file from the backend which is NFS mounted to the server, so why is their a message about not finding the file?

I also have a lot of errors like these;
```
2011-09-23 17:48:09.206 Could not find channel 20_1 in TVCT
2011-09-23 17:48:09.213 
VCT Terra: channels(4) tsid(0x3ef) seclength(221)
Channel #0 name(WTTW-HD) 11-1 mod(ATSC 8-VSB) cTSID(0x3ef)
 pnum(3) ETM_loc(1) access_ctrl(0) hidden(0) hide_guide(1) service_type(ATSC TV) source_id(1)
 descriptors length(23) count(1)
  Service Location Descriptor (0xa1) length(21)

Channel #1 name(WTTW-DT) 11-2 mod(ATSC 8-VSB) cTSID(0x3ef)
 pnum(4) ETM_loc(0) access_ctrl(0) hidden(0) hide_guide(1) service_type(ATSC TV) source_id(2)
 descriptors length(23) count(1)
  Service Location Descriptor (0xa1) length(21)

Channel #2 name(WTTW-DT) 11-3 mod(ATSC 8-VSB) cTSID(0x3ef)
 pnum(5) ETM_loc(0) access_ctrl(0) hidden(0) hide_guide(1) service_type(ATSC TV) source_id(3)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)

Channel #3 name(WTTW-DT) 11-4 mod(ATSC 8-VSB) cTSID(0x3ef)
 pnum(6) ETM_loc(0) access_ctrl(0) hidden(0) hide_guide(1) service_type(ATSC TV) source_id(4)
 descriptors length(17) count(1)
  Service Location Descriptor (0xa1) length(15)
```
I ran myth-setup and rescaned my over-the-air channels and it found some new ones and removed old ones, so what are these errors about?

---

### Post by nickrout on 2011-09-25
your vide problem is possibly permissions. As the user that runs the frontend (usually he name you set up on installing mythbuntu) can you read the file at a terminal?

---

### Post by uteck on 2011-09-26
I set permissions to 777, but no difference.  When I navigate to the Video directory the system hangs at the "loading videos, or no videos present" screen for a few minutes then the frontend crashes.  When I try a second time it opens the storage group fine, but then hangs and crashes when I try to open a video.

---

