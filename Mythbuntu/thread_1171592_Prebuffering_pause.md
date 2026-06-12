---
title: "Prebuffering pause"
date: 2009-05-27
forum: Mythbuntu
---

### Post by duffrecords on 2009-05-27
While watching live TV, I noticed a lot of prebuffering pauses in the frontend's log file, and solved this by selecting "Always stream recordings from the backend."  So after that, it was working smoothly.  

Now, however, I'm seeing prebuffering pauses late at night when I watch recorded programs.  The backend records several shows between 6 PM and 1 AM, so I'm wondering if the problem is disk throughput.  Any suggestions?```
2009-05-26 23:57:01.609 RingBuf(myth://192.168.1.210:6543/1041_20090526030400.mpg): Waited 1.0 seconds for data to become available...
2009-05-26 23:57:02.293 NVP: Prebuffer wait timed out 10 times.
2009-05-26 23:57:02.609 RingBuf(myth://192.168.1.210:6543/1041_20090526030400.mpg): Waited 2.0 seconds for data to become available...
2009-05-26 23:57:03.793 NVP: Prebuffer wait timed out 20 times.
2009-05-26 23:57:04.610 RingBuf(myth://192.168.1.210:6543/1041_20090526030400.mpg): Waited 4.0 seconds for data to become available...
2009-05-26 23:57:05.292 NVP: Prebuffer wait timed out 30 times.
2009-05-26 23:57:06.076 NVP: prebuffering pause
2009-05-26 23:57:07.709 NVP: prebuffering pause
2009-05-26 23:57:07.976 NVP: prebuffering pause
2009-05-26 23:57:08.243 NVP: prebuffering pause
2009-05-26 23:57:08.526 NVP: prebuffering pause
2009-05-26 23:57:08.875 NVP: prebuffering pause
```

---

### Post by duffrecords on 2009-06-04
It turns out this is a network problem.  After watching recorded video for several minutes, the frontend suddenly loses the connection to the backend.  From the frontend, I can ping my gateway as well as outside IP addresses, but not the backend's IP.  From the backend, I can ping everything and even ssh into the frontend.  Once I do that, the connection is immediately restored.  Or I can wait a few more minutes and the frontend eventually reconnects.  It's a real show-stopper, literally.  And it only seems to happen while watching recorded programs.

I wonder if it has anything to do with the way the gateway is set up.  I have two Linksys WRT54G routers; one is directly wired to my DSL modem and the backend, the other is configured as a wireless bridge which is wired to the frontend and my XBox 360 in another room.  I know wifi adds some unreliability to the system.

Here is another excerpt from last night's /var/log//mythtv/mythfrontend.log:```
2009-06-03 21:30:28.467 OSD Theme Dimensions W: 1280 H: 720
2009-06-03 21:30:28.874 TV: Changing from None to WatchingPreRecorded
2009-06-03 21:30:28.877 The realtime priority setting is not enabled.
2009-06-03 21:30:28.981 OpenGLVideoSync()
2009-06-03 21:30:29.039 WriteAudio: buffer underrun
2009-06-03 21:30:29.265 WriteAudio: buffer underrun
2009-06-03 21:30:29.288 Video timing method: SGI OpenGL
2009-06-03 21:33:55.572 NVP: prebuffering pause
2009-06-03 21:33:57.055 NVP: Prebuffer wait timed out 10 times.
2009-06-03 21:33:58.556 NVP: Prebuffer wait timed out 20 times.
2009-06-03 21:33:59.041 RingBuf(myth://192.168.1.210:6543/1041_20090528203000.mpg): Waited 4.0 seconds for data to become available...
2009-06-03 21:34:00.056 NVP: Prebuffer wait timed out 30 times.
2009-06-03 21:34:01.556 NVP: Prebuffer wait timed out 40 times.
2009-06-03 21:34:03.043 RingBuf(myth://192.168.1.210:6543/1041_20090528203000.mpg): Waited 8.0 seconds for data to become available...
2009-06-03 21:34:03.056 NVP: Prebuffer wait timed out 50 times.
2009-06-03 21:34:04.557 NVP: Prebuffer wait timed out 60 times.
2009-06-03 21:34:06.057 NVP: Prebuffer wait timed out 70 times.
2009-06-03 21:34:07.557 NVP: Prebuffer wait timed out 80 times.
2009-06-03 21:34:09.057 NVP: Prebuffer wait timed out 90 times.
2009-06-03 21:34:10.424 MythSocket(94ae638:23): readStringList: Error, timeout (quick).
2009-06-03 21:34:10.424 RemoteFile::Read(): No response from control socket.
2009-06-03 21:34:10.424 RingBuf(myth://192.168.1.210:6543/1041_20090528203000.mpg) Error: RingBuffer::safe_read(RemoteFile* ...): read failed
2009-06-03 21:34:10.425 ~OpenGLVideoSync() -- begin
2009-06-03 21:34:10.425 ~OpenGLVideoSync() -- middle
2009-06-03 21:34:10.426 ~OpenGLVideoSync() -- end
```

---

### Post by duffrecords on 2009-06-11
I've isolated this problem to the backend, and it doesn't seem to be related to MythTV.  I was using tightvncviewer to connect to the backend's desktop from work and the client became unresponsive for a few minutes.  Now it's ok again.  So periodically the connection gets momentarily interrupted and outside IPs can't reach it, but it can reach outside IPs.  None of the other computers on my network are having this problem.  This also eliminates the wireless bridge from the problem, as the backend is connected directly to the router, which is connected directly to the modem.  Is there a log I should look at?

---

### Post by ian dobson on 2009-06-12
Hi,

Have a look in /var/log/syslog or dmesg.

I had a problem with my frontend that the network connection would break for afew seconds once or twice per day when transfering large files or watching HD (My backend is on a seperate machine). The funny thing is that I could ping any computer on my network for days on end without any problem.

Ended up "just" replacing all the wiring/connectors/wall plates with CAT 6e wiring. Since then I've not had any problems.

Regards
Ian Dobson

---

### Post by duffrecords on 2009-06-14
Thanks.  I'm not sure if it's related but /var/log/syslog is giving me some interesting information:```
Jun 13 20:10:20 burbank kernel: [174840.164289] FAT: FAT read failed (blocknr 34080)
Jun 13 20:10:22 burbank kernel: [174841.984751] FAT: FAT read failed (blocknr 33938)
Jun 13 20:10:22 burbank kernel: [174841.985575] FAT: FAT read failed (blocknr 18384)
Jun 13 20:10:24 burbank kernel: [174843.904781] FAT: FAT read failed (blocknr 14839)

```This is strange because the only FAT device connected is an unused FAT32 partition.  Other than that, this is the only error that occurred during one of the times I noticed the interruption.

---

### Post by ian dobson on 2009-06-14
Hi,

Try running a fsck on th fat partition. Are you sure it's not used? Do a df to see if which partitions are mounted.

Could it be that the fat partition is on an external USB harddisk and linux it seeing this drive and trying to mount it but due to disk errors, it drops it then trys to mount it again and again.

Regards
Ian Dobson

---

### Post by duffrecords on 2009-06-14
I'm certain the FAT32 partition is unused.  I originally wanted to install Windows on it as a "just in case" OS but the Windows installer couldn't find it.  I gave up on that because having Windows wasn't a huge priority.

The interesting thing is that df shows my iPod (which is FAT) still mounted, even though I unmounted and disconnected it yesterday.  I used the GUI to unmount it, and in my experience the GUI is often less trustworthy than the command line.  I'll have to see if that has any effect now.

---

### Post by duffrecords on 2009-06-14
Looks like that iPod was causing all kinds of trouble.  The syslog is full of those FAT read errors.  And it's interesting that it affected NetworkManager in the process.  If I don't see any more interruptions I'll mark this solved.

---

### Post by duffrecords on 2009-06-14
This definitely improved the network latency.  Last night ping results between the frontend and backend were sometimes > 50ms.  Now they're only about 1-2ms.  Wish I was at home so I could test out the playback!

---

### Post by duffrecords on 2009-06-14
I spoke too soon.  Both my SSH and VNC sessions stopped responding but then resumed three minutes later.  Something else is causing the problem.

---

### Post by duffrecords on 2009-06-19
This problem is happening because of the custom real-time kernel I've been using.  After rebooting with the vanilla kernel the problem went away.  I'm going to experiment with a real-time kernel that's maintained by a distribution and see if that works.  I absolutely need -rt because this system is primarily an audio workstation with MythTV running when I'm not recording.

---

