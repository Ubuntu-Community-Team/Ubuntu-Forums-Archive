---
title: "RingBuffer: Failed to open remote file"
date: 2008-05-18
forum: Mythbuntu
---

### Post by tedder on 2008-05-18
I'm getting the following error very frequently, though only when recording. It appears to coincide with "HDTV dropouts" that I've started to experience since the Heron upgrade.

```
2008-05-18 17:06:48.381 MainServer::HandleAnnounce Playback
2008-05-18 17:06:48.382 adding: mythtv1 as a client (events: 0)
2008-05-18 17:06:48.384 MainServer::HandleAnnounce FileTransfer
2008-05-18 17:06:48.384 adding: mythtv1 as a remote file transfer
2008-05-18 17:06:48.385 RemoteFile::openSocket(control socket):
2008-05-18 17:06:48.386 RemoteFile::openSocket(file data socket):
2008-05-18 17:06:48.387 RingBuffer::RingBuffer(): Failed to open remote file ()
```

It looks like people have seen this when the hostname is incorrect ([thread 1](http://ubuntuforums.org/showthread.php?t=759784), [thread 2](http://ubuntuforums.org/showthread.php?t=594254)), though that doesn't seem to be the problem on mine. Here are the first two entries from my hosts file:
```
127.0.0.1       localhost
127.0.1.1       mythtv1
```

Video plays okay, though I do get some sporadic dropouts, as if my signal wasn't working well. That could easily be a red herring.

In other words, my mythbox is mostly working well, and has been. So what is causing these errors?

---

