---
title: "trouble with videos and storage groups"
date: 2010-05-12
forum: Mythbuntu
---

### Post by sciguy125 on 2010-05-12
I decided to attempt to start using storage groups for my videos.  I tried to make the change between scheduled recordings.  Unfortunately, I've run out of time to play, so I'm coming here for help before trying again.

My frontends are able to see the videos that are in the storage groups, but it won't let me play them.

The situation:
- MBE hosts both the master backend and a frontend
- SBE hosts a slave backend and the videos on its local filesystem
- RFE hosts a remote frontend

I've setup SBE to have storage groups that point to the appropriate local directories.  MBE has no storage groups and its frontend has MythVideo pointing to empty local directories (Videos, Banners, etc. are local but empty.  RFE has the same MythVideo setup as MBE.

RFE frontend log:

```
2010-05-11 21:03:07.451 TV: Attempting to change from None to WatchingVideo
2010-05-11 21:03:07.451 RemoteFile::openSocket(control socket), Error: 
			Could not connect to server 127.0.0.1:6543
2010-05-11 21:03:07.452 RemoteFile::openSocket(file data socket), Error: 
			Could not connect to server 127.0.0.1:6543
2010-05-11 21:03:07.452 RingBuffer::RingBuffer(): Failed to open remote file (myth://Videos@127.0.0.1:6543/2012 (2009).avi)
```

MBE frontend log shows same about not being able to open remote file.  MBE backend log when trying to play from MBE frontend:

```
2010-05-11 20:53:46.211 ERROR: LocalFilePath unable to find local path for '2012 (2009).avi'.
2010-05-11 20:53:46.217 RingBuffer::RingBuffer(): Failed to open remote file ()
QFileInfo::absolutePath: Constructed with empty filename
2010-05-11 20:53:46.339 RingBuf() Error: Invalid file descriptor in 'safe_read()'
```

SBE backend log shows nothing of interest.

I suspect that the problem is that it's trying to look for the video at 127.0.0.1.  However, I my understanding of the inner workings of MythTV is limited, so I could be wrong.

---

### Post by sciguy125 on 2010-05-12
I got it.

I had the IP address of the slave backend set to 127.0.0.1.

On SBE: mythtv-setup > General > Host Address Backend Setup.  IP address of Local Backend should be set to the externally accessible address.

---

