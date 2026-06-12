---
title: "Ubuntu 12.04 and Mythtv 0.25 - Slow channel changing"
date: 2014-01-07
forum: Mythbuntu
---

### Post by mcapaldo on 2014-01-07
Well I hosed my old ubuntu 10.10 with mythtv 0.24 install so I yanked that drive and put a new drive in and got 12.04 & 0.25 running.  Still can't seem to import my old recordings there is an old script that is really unsupported anymore.   only safe theing is to move the old data to the /mythtv/videos folder and run M to re-scan.   I have moved old data to another folder for now.  

Well I got 12.04 64 bit edition running mythtv 0.25 running fine.  BUT changing channels via keyboard or the remote takes like 10 seconds per channel change.  

Recordings run fine.

Any idea as to why channel change is so slow in new release?  I ran update manager via mythbuntu control center and installed all available updates and rebooted.  I have a 37" Vizio and have video drivers installed and resolution set to highest.

Any help is appreciated, thanks.

---

### Post by newlinux on 2014-01-08
Probably best to start with looking at your frontend and backend logs for error messages. You can post them here and we can take a look.

---

### Post by khPWXxF on 2014-01-09
A point of comparison on channel changing with dvbt in the uk and Hauppauge usb stick tuner.
Press channel digit only - about 12 seconds
Press channel number then enter:  about 7 seconds.

As for your recordings, did you have a database backup before you migrated?
Phil

---

### Post by mcapaldo on 2014-01-11
mythtvbackend log file

Jan 11 20:30:21 mythtvserver mythbackend[3250]: N Expire autoexpire.cpp:640 (SendDeleteMessages) Expiring 0 MB for 1072 at 2014-01-11T20:27:49 => "Sister Act 2: Back in the Habit"
Jan 11 20:30:23 mythtvserver mythbackend[3250]: W DeviceReadBuffer DeviceReadBuffer.cpp:530 (Poll) DevRdB(/dev/video0): Poll took an unusually long time 2502 ms
Jan 11 20:30:31  mythbackend[3250]: last message repeated 2 times
Jan 11 20:30:31 mythtvserver mythbackend[3250]: W DeviceReadBuffer DeviceReadBuffer.cpp:530 (Poll) DevRdB(/dev/video0): Poll took an unusually long time 2503 ms
Jan 11 20:30:33 mythtvserver mythbackend[3250]: W DeviceReadBuffer DeviceReadBuffer.cpp:530 (Poll) DevRdB(/dev/video0): Poll took an unusually long time 2502 ms
Jan 11 20:30:41  mythbackend[3250]: last message repeated 2 times
Jan 11 20:30:41 mythtvserver mythbackend[3250]: W DeviceReadBuffer DeviceReadBuffer.cpp:530 (Poll) DevRdB(/dev/video0): Poll took an unusually long time 2503 ms
Jan 11 20:30:43 mythtvserver mythbackend[3250]: W DeviceReadBuffer DeviceReadBuffer.cpp:530 (Poll) DevRdB(/dev/video0): Poll took an unusually long time 2502 ms
Jan 11 20:30:45 mythtvserver mythbackend[3250]: I TVRecEvent tv_rec.cpp:1030 (HandleStateChange) TVRec(1): Changing from WatchingLiveTV to None
Jan 11 20:30:45 mythtvserver mythbackend[3250]: E RecThread mpegrecorder.cpp:1016 (run) MPEGRec(/dev/video0): Device EOF detected
Jan 11 20:31:23 mythtvserver mythbackend[3250]: I HouseKeeping housekeeper.cpp:225 (RunHouseKeeping) Running housekeeping thread
Jan 11 20:31:25 mythtvserver mythbackend[3250]: I Metadata_1708 jobqueue.cpp:2151 (DoMetadataLookupThread) JobQueue: Metadata Lookup Starting for "Sister Act 2: Back in the Habit" recorded from channel 1072 at 2014-01-11T20:27:50
Jan 11 20:31:26 mythtvserver mythbackend[3250]: E Metadata_1708 jobqueue.cpp:2215 (DoMetadataLookupThread) JobQueue: Metadata Lookup Errored: "Sister Act 2: Back in the Habit" recorded from channel 1072 at 2014-01-11T20:27:50 (Failed with exit status 128)

mythtvfrontend log file

Jan 11 20:30:05 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 6388 < 32768
Jan 11 20:30:06 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 6388 < 32768
Jan 11 20:30:08 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 596 < 32768
Jan 11 20:30:08 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 596 < 32768
Jan 11 20:30:08 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 596 < 32768
Jan 11 20:30:08 mythtvserver mythfrontend[3618]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 104ms for video buffers UUUUUUUUUUULLAAAAAAAAAAAAAAAAAUP
Jan 11 20:30:10 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 32016 < 32768
Jan 11 20:30:10 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 32016 < 32768
Jan 11 20:30:13 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 3824 < 32768
Jan 11 20:30:13 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 3824 < 32768
Jan 11 20:30:13 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 3824 < 32768
Jan 11 20:30:13 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 3824 < 32768
Jan 11 20:30:13 mythtvserver mythfrontend[3618]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 104ms for video buffers UUUuLAAAAAAAAAAAAAAAAAAAUUUUUUUP
Jan 11 20:30:15 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 29524 < 32768
Jan 11 20:30:15 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 29524 < 32768
Jan 11 20:30:20 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 20416 < 32768
Jan 11 20:30:20 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 20416 < 32768
Jan 11 20:30:21 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 20416 < 32768
Jan 11 20:30:21 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 20416 < 32768
Jan 11 20:30:23 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 7692 < 32768
Jan 11 20:30:23 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 7692 < 32768
Jan 11 20:30:25 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 28480 < 32768
Jan 11 20:30:25 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 28480 < 32768
Jan 11 20:30:26 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 28480 < 32768
Jan 11 20:30:28 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 32308 < 32768
Jan 11 20:30:28 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 32308 < 32768
Jan 11 20:30:28 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 32308 < 32768
Jan 11 20:30:28 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 32308 < 32768
Jan 11 20:30:28 mythtvserver mythfrontend[3618]: N CoreContext mythplayer.cpp:2078 (PrebufferEnoughFrames) Player(0): Waited 104ms for video buffers AAAAAAAAAAUUUUUUUUUUuLAAAAAAAAAP
Jan 11 20:30:30 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 31080 < 32768
Jan 11 20:30:30 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 31080 < 32768
Jan 11 20:30:31 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 31080 < 32768
Jan 11 20:30:33 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 7376 < 32768
Jan 11 20:30:33 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 7376 < 32768
Jan 11 20:30:33 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 7376 < 32768
Jan 11 20:30:33 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.5 seconds for data #012#011#011#011to become available... 7376 < 32768
Jan 11 20:30:41 mythtvserver mythfrontend[3618]: I Decoder ringbuffer.cpp:1086 (WaitForAvail) RingBuf(/mnt/mythtv/livetv/1072_20140111202750.mpg): Waited 0.2 seconds for data #012#011#011#011to become available... 7080 < 32768
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: I CoreContext tv_play.cpp:2121 (HandleStateChange) TV: Attempting to change from WatchingLiveTV to None
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: I CoreContext audio/audiopulsehandler.cpp:320 (SuspendInternal) Pulse: PulseAudio resume OK
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: I CoreContext tv_play.cpp:2360 (HandleStateChange) TV: Changing from WatchingLiveTV to None
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: I CoreContext tv_play.cpp:380 (StartTV) TV: Exiting main playback loop.
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: I CoreContext screensaver-x11.cpp:161 (RestoreDPMS) ScreenSaverX11Private: DPMS Reactivated 1
Jan 11 20:30:45 mythtvserver mythfrontend[3618]: N CoreContext mythmainwindow.cpp:2591 (PauseIdleTimer) Resuming idle timer
Jan 11 20:30:55  mythfrontend[3618]: last message repeated 2 times
Jan 11 20:30:55 mythtvserver mythfrontend[3618]: I CoreContext bonjourregister.cpp:27 (~BonjourRegister) Bonjour: De-registering service '_mythfrontend._tcp.' on 'Mythfrontend on mythtvserver'
Jan 11 20:30:55 mythtvserver mythfrontend[3618]: I CoreContext mythraopdevice.cpp:82 (Cleanup) RAOP Device: Cleaning up.
Jan 11 20:30:55 mythtvserver mythfrontend[3618]: I CoreContext mythairplayserver.cpp:260 (Cleanup) AirPay: Cleaning up.
Jan 11 20:30:55 mythtvserver mythfrontend[3618]: I CoreContext audio/audiopulsehandler.cpp:46 (Suspend) Pulse: Cleaning up PulseHandler
Jan 11 20:30:55 mythtvserver mythfrontend[3618]: I CoreContext main.cpp:244 (cleanup) Deleting UPnP client...
Jan 11 20:30:56 mythtvserver mythfrontend[3618]: I CoreContext mythcontext.cpp:1115 (~MythContext) Waiting for threads to exit.

---

