---
title: "MythVideo Playback Problem"
date: 2011-09-28
forum: Multimedia Software
---

### Post by Pariah819 on 2011-09-28
Hello,

Recently I decided to add some features to my MythTV setup and I've been having some issues with something I thought would be simple.  I added some .mpg video files (DVD Rips) to my storage directories on the Myth Backend, and my Myth Frontend can see the video files but when I actually try to play the videos it doesn't do anything.  When I select to watch the video it hangs at the menu screen for a few seconds then the screen flickers and nothing happens.  I've attached my mythfrontend.log so you can see the error.

Any help would be greatly appreciated!

thanks

---

### Post by Pariah819 on 2011-09-30
Well I have a small update but I haven't made much progress.  I found some documentation that said that the version of MythTV I was running on my frontend (0.24.1) didn't support streaming directly from the storage directories.  So I followed a procedure that said I had to setup a network share for the MythVideo internal player to stream from.  So I created an NFS share at /media/Storage/videos on my backend server, then I mapped that to /home/mythtv/videos on my frontend pc.  Once again when I did a "Scan for Changes" the library updated with the videos I had in this directory showed up but I could not play them. 

The error reported in the mythfrontend.log is the same as before...
```

-09-30 16:12:45.002 TV: Attempting to change from None to WatchingVideo
2011-09-30 16:12:45.524 RingBuf(myth://[Videos@192.168.1.65:6543/The]("http://Videos@192.168.1.65:6543/The") Adjustment Bureau.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2011-09-30 16:12:45.555 RingBuf(myth://[Videos@192.168.1.65:6543/The]("http://Videos@192.168.1.65:6543/The") Adjustment Bureau.mpg) Warning: Peek() requested 2048 bytes, but only returning -1
2011-09-30 16:12:45.556 Player(0), Warning: OpenFile() waiting on data
2011-09-30 16:12:45.566 RingBuf(myth://[Videos@192.168.1.65:6543/The]("http://Videos@192.168.1.65:6543/The") Adjustment Bureau.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed


```

---

