---
title: "Ignoring errors from external 6200ch?"
date: 2012-02-22
forum: Mythbuntu
---

### Post by RideMan on 2012-02-22
Okay, I have a rather annoying problem.  To make matters worse, it's an annoying problem on a system that is 2,300 miles away.

The system is configured so that most recording happens via the digital and analog tuners.  There are a select few channels, though, that are only available via the Motorola digital cable box.  When I set up the system, I determined that I could not record via FireWire (thanks, Time-Warner...) so I set it up to use the S-Video and audio inputs on the card to do the recording.

Before I went home, I determined that the S-video input was working nicely, and I thought that the 6200ch instance was very nicely changing channels.  I'm using an external version of 6200ch...that is, I am using the following command for changing channels:

/usr/local/bin/6200ch -g [GUID of CATV box]

I am told that every time a scheduled recording attempts to change the channel on the box, the channel dutifully changes.  But every time a scheduled recording uses that input, I get a zero-byte recording.  A look in the backend indicates an error that the "Channel change failed."

My guess is that this error is coming courtesy of 6200ch because once the channel changes, there is a series of errors returned from the box, which relates to my inability to actually record via FireWire.  But the reality is that the channel IS changing, and I AM (presumably) getting clean video on the S-Video input #2 of the tuner board.  In fact, I should ALWAYS be getting clean video on the S-Video input #2 of the tuner board because when not watching MythTV, the owners are typically watching something off the cable box, fed directly to the TV.

So is there any way I can suppress these errors or get MythTV to ignore them?  I suppose a log sample would be helpful...it's been a few weeks since the system tried to record from the cable box, but let me see what I can find...

Ah; this one is somewhat typical.  Comments added...

```

2012-01-02 05:00:02.897 TVRec(9): Changing from None to RecordingOnly
2012-01-02 05:00:02.979 TVRec(9): HW Tuner: 9->9

# HW Tuner 9 = S-Video input #2 on the Hauppauge card.

rom1394_0 warning: read failed: 0x0000fffff000040c

# I think this is the error causing problems

2012-01-02 05:00:03.210 AutoExpire: CalcParams(): Max required Free Space: 2.0 GB w/freq: 15 min
2012-01-02 05:00:03.295 Started recording: NCIS:Bait: channel 4132 on cardid 9, sourceid 4

# Channel 4132 on the system = Channel 132 on the cable box.
# System owners never watch that channel; if the box is tuned there it's because MythTV did it.

rom1394_0 warning: read failed: 0x0000fffff0000410
2012-01-02 05:00:03.331 scheduler: Started recording: NCIS:Bait: channel 4132 on cardid 9, sourceid 4
2012-01-02 05:00:33.044 SignalMonitor: channel change failed
2012-01-02 05:00:33.135 SignalMonitor: channel change failed

# But, in fact, I am informed that the CATV box DID, in fact, change channels

2012-01-02 05:00:33.173 Updating status for NCIS:Bait on cardid 9 (Tuning => Recorder Failed)

# So MythTV aborts the recording even though the channel changed just fine.

2012-01-02 05:00:33.212 Reschedule requested for id 0.

# At least it is nice enough to offer to try again...

```

Just to make sure the error sequence IS typical...sometime after this I tried increasing the timeout on the tuner card to make sure the box had time to change channels and lock up the video.  So let me see if I can find a more recent example from after I made that change...

```


2012-02-09 12:00:02.393 TVRec(9): HW Tuner: 9->9
couldn't set port: Invalid argument
2012-02-09 12:00:02.801 Started recording: NCIS:"Lost & Found": channel 4132 on cardid 9, sourceid 4
2012-02-09 12:00:02.912 scheduler: Started recording: NCIS:"Lost & Found": channel 4132 on cardid 9, sourceid 4
2012-02-09 12:00:02.932 SignalMonitor: channel change failed
2012-02-09 12:00:02.986 MainServer::ANN Monitor
2012-02-09 12:00:03.066 adding: Farnsworth as a client (events: 1)
2012-02-09 12:00:03.074 SignalMonitor: channel change failed
2012-02-09 12:00:03.199 SignalMonitor: channel change failed
2012-02-09 12:00:03.291 SignalMonitor: channel change failed
2012-02-09 12:00:03.383 SignalMonitor: channel change failed
2012-02-09 12:00:03.475 SignalMonitor: channel change failed
2012-02-09 12:00:03.566 SignalMonitor: channel change failed
2012-02-09 12:00:03.658 SignalMonitor: channel change failed
2012-02-09 12:00:03.700 Updating status for NCIS:"Lost & Found" on cardid 9 (Tuning => Recorder Failed)
2012-02-09 12:00:03.986 Reschedule requested for id 0.
2012-02-09 12:00:04.024 Reschedule requested for id 0.

```

Hmmm...Obviously there's something else going on here as well, as the most recent  occurrence has that bit about not being able to set the port.  Not sure what the invalid argument might be, as that never changed....But the fact remains, we're getting channel changes, but errors are causing MythTV to give up on what should be a routine recording.

Any ideas or advice?  Thanks!

--Dave Althoff, Jr.

---

### Post by RideMan on 2012-02-23
On further review...

This may be a moot point.  It seems that the machine in question has forgotten that it has a FireWire interface.  And, again, it's 2,300 miles away, so reseating the card is kind of difficult.  I may have to put off work on 6200.ch until I can get the Firewire working again...

--Dave Althoff, Jr.

---

### Post by uteck on 2012-02-26
I am using firewire to change channels only so I did not configure the firewire turner and it works fine this way.  
So remove any channels that may be associated with it and either delete it or give it a very low priority so it is not used.

---

