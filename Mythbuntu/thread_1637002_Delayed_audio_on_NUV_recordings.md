---
title: "Delayed audio on NUV recordings"
date: 2010-12-03
forum: Mythbuntu
---

### Post by kyphos on 2010-12-03
I am building a new mythtv system installed from Mythbuntu 10.04 Live CD. Hence, mythtv 0.23.
I have two tuners: a PVR-150 that encodes MPEG (configured as Tuner 1), and an Asus 7135 sampler (configured as Tuner 2). Both are connect to analog cable service.  I need some help debugging an audio problem.

Shows recorded with Tuner 2 exhibit a sizable delay in the audio when played back. I generally need to manually add 300-400 msec of delay compensation every time I play back a recording created by the Asus tuner to get the audio to sync with the video.

When a playback event starts on a show recorded with tuner 2, I find this in the FE log:
```
2010-12-03 19:11:51.339 TV: Attempting to change from WatchingPreRecorded to None
2010-12-03 19:11:51.377 TV: Changing from WatchingPreRecorded to None
2010-12-03 19:11:51.404 Preview: Grabbed preview '/home/mythtv/recordings/1007_20101202210000.nuv' 704x480@64s
2010-12-03 19:11:51.850 ~MythContext waiting for threads to exit.
2010-12-03 19:12:18.541 TV: Attempting to change from None to WatchingPreRecorded
2010-12-03 19:12:18.640 AO: Using resampler. From: 32000 to 48000
2010-12-03 19:12:18.642 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-03 19:12:18.643 Opening ALSA audio device 'default'.
2010-12-03 19:12:18.661 AO: Using resampler. From: 32000 to 48000
2010-12-03 19:12:18.663 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-03 19:12:18.663 Opening ALSA audio device 'default'.
2010-12-03 19:12:18.676 AO: Using resampler. From: 32000 to 48000
2010-12-03 19:12:18.677 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-12-03 19:12:18.677 Opening ALSA audio device 'default'.
2010-12-03 19:12:18.702 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2010-12-03 19:12:18.773 OSD Theme Dimensions W: 640 H: 480
2010-12-03 19:12:18.851 TV: Changing from None to WatchingPreRecorded
2010-12-03 19:12:18.856 Realtime priority would require SUID as root.
2010-12-03 19:12:18.866 Video timing method: USleep with busy wait
```Note the repeated messages that a resampler is needed to convert from 32000 to 48000. My (amateur) assessment is that the audio signal was sampled at 32kHZ when recorded, and is now being resampled to 48 kHZ for playback.  My system has but a humble 1.6GHz Sempron chip, so I'm guessing that the CPU is working hard to resample the audio during playback, thus delaying it from the video.  Does this make sense?

If so, why can't the sophisticated Myth software play back at the original sample rate (32 kHz)?  If it didn't have to resample, it seems to me that the audio delay would disappear. Do I need to configure something to enable variable rate playback when a NUV file is the source?

Conversely, can I change the sampling rate for the recording? If the NUV file contained audio at 48 kHZ, the resample process wouldn't be needed, and less CPU cycles consumed (but the file would be a bit bigger).

I'm also wondering about the log message "**Realtime priority would require SUID as root**".  Is this anything to worry about? Might it also contribute to my audio delay problem?

Thanks for your help.

---

