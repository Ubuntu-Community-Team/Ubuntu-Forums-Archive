---
title: "Recordings with size B"
date: 2009-01-03
forum: Mythbuntu
---

### Post by Vague Craig on 2009-01-03
On a fresh install of 8.10 I've set up one machine as a standalone backend/ frontend, and everything seemed to be going well. 

Everything I set to record yesterday evening and through the night claims to be recorded but the file doesn't exist. The file size is shown as "B" when viewed using mythweb, even when I came back and had a look, a program that was being recorded had a file size of B also.

When I tried to view the log the machine locked up and I had to reboot so I don't know quite what has gone on. Today everything seems to be working fine again and it's been recording everything on teh schedule fine.

The only curious thing in the log is a warning at the top of the window telling me I'm using the root which may harm my system. I have no idea what is using the root as this is just a fresh default myth install?

Any Ideas greatly appreciated.

---

### Post by uncle hammy on 2009-01-03
This happened to me once, turned out my tuner was on the fritz, and it was unable to get a lock when attempting to tune to record.  The database record itself was written, but nothing was ever able to record.

Once I had my tuner repaired (it was an HDHomeRun that was plagued by there power adapter issue), I was fine again.

---

### Post by ian dobson on 2009-01-04
Hi,

What tuner are you using? I've seen 0Byte recordings afew times, once on my DVB-C tuner when the tuner couldn't lock onto the channel due to a bad cable link and several times due to a screwed up IVTV configuration for my PVR-500.

Regards
Ian Dobson

---

### Post by Vague Craig on 2009-01-04
Hi, 

I'm using a Haupaugge Win TV TD Nova card which works normally after a reset (same thing has happened this morning) but just stops working. When I went to live TV after noticing the fault again it shows 99 percent signal (so none) and no lock.

I've got a feeling that if I go down the hardware route it may be tricky as linux support is sketchy from hauppagge, though I'm wondering if just buying a new card to test is the way to go (I was going to get another anyway).

The backend log is this:

> ==> /var/log/mythtv/mythbackend.log <==
2009-01-04 06:39:42.428 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 06:54:42.464 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 07:09:42.516 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 07:24:42.551 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 07:39:42.584 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 07:54:42.618 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 08:09:42.828 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 08:24:42.864 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 08:39:42.900 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 08:54:42.935 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 09:09:42.968 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 09:24:43.003 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-01-04 09:27:50.878 Reschedule requested for id 0.
2009-01-04 09:27:50.982 Scheduled 23 items in 0.1 = 0.00 match + 0.10 place
2009-01-04 09:28:20.029 TVRec(1): ASK_RECORDING 1 29 0 0
2009-01-04 09:28:20.826 TVRec(2): ASK_RECORDING 2 29 0 0
2009-01-04 09:28:51.282 TVRec(1): Changing from None to RecordingOnly
2009-01-04 09:28:51.285 TVRec(1): HW Tuner: 1->1
2009-01-04 09:28:52.048 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 09:28:52.053 Started recording: Scrapheap Challenge: channel 9442 on cardid 1, sourceid 1
2009-01-04 09:39:43.040 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 09:54:43.083 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:09:43.124 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:24:43.166 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:32:50.202 Reschedule requested for id 0.
2009-01-04 10:32:50.279 Scheduled 23 items in 0.1 = 0.00 match + 0.07 place
2009-01-04 10:34:29.919 TVRec(2): ASK_RECORDING 2 29 0 0
2009-01-04 10:34:30.209 TVRec(1): ASK_RECORDING 1 29 0 0
2009-01-04 10:35:02.297 TVRec(1): Changing from RecordingOnly to None
2009-01-04 10:35:02.758 Finished recording Scrapheap Challenge: channel 9442
2009-01-04 10:35:02.819 TVRec(1): Changing from None to RecordingOnly
2009-01-04 10:35:02.821 TVRec(1): HW Tuner: 1->1
2009-01-04 10:35:02.985 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:35:02.989 Started recording: Scrapheap Challenge: channel 9442 on cardid 1, sourceid 1
2009-01-04 10:35:03.993 Reschedule requested for id 0.
2009-01-04 10:35:04.072 Scheduled 22 items in 0.1 = 0.00 match + 0.08 place
2009-01-04 10:39:43.207 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:54:43.253 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-01-04 10:58:19.666 MainServer::HandleAnnounce Monitor
2009-01-04 10:58:19.668 adding: Gerald as a client (events: 0)
2009-01-04 10:58:24.295 MainServer::HandleAnnounce Monitor
2009-01-04 10:58:24.299 adding: Gerald as a client (events: 0)
2009-01-04 10:58:24.432 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Gerald/9442_20090104103500.mpg'
2009-01-04 10:58:24.434 MainServer: Failed to make preview image.
2009-01-04 10:58:24.445 Preview Error: Run() file not local: '9442_20090104103500.mpg'
2009-01-04 10:58:24.456 Preview Error: Run() file not local: '/GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/Gerald/9442_20090104092900.mpg'
2009-01-04 10:58:24.460 MainServer: Failed to make preview image.
2009-01-04 10:58:24.470 Preview Error: Run() file not local: '9442_20090104092900.mpg'
2009-01-04 10:58:56.935 MainServer::HandleAnnounce Monitor
2009-01-04 10:58:56.936 adding: Gerald as a client (events: 0)
2009-01-04 10:58:57.034 MythSocket(8fa8a28:-1): writeStringList: Error, socket went unconnected.
2009-01-04 10:59:04.205 Reschedule requested for id 0.
2009-01-04 10:59:04.294 Scheduled 22 items in 0.1 = 0.00 match + 0.09 place
2009-01-04 11:01:07.050 MainServer::HandleAnnounce Playback
2009-01-04 11:01:07.054 adding: Gerald as a client (events: 0)
2009-01-04 11:01:07.057 TVRec(5): Changing from None to WatchingLiveTV
2009-01-04 11:01:07.068 TVRec(5): HW Tuner: 5->5
2009-01-04 11:01:09.489 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 8 min
2009-01-04 11:01:32.598 TVRec(5): Changing from WatchingLiveTV to None
2009-01-04 11:01:32.638 Finished recording Hollyoaks Omnibus: channel 9384
2009-01-04 11:04:43.285 Expiring 0 MBytes for 9384 @ Sun Jan 4 10:00:00 2009 => Hollyoaks Omnibus

---

### Post by Vague Craig on 2009-01-15
I've been trying to get around this problem by changing some of the setting in myth e.g. the card would start working again if I cleared it on the back end and set it back up. I set the cards up as one recording per tuner, and changed the setting to only open the card when recording. I've also fiddled with the tuning time to no avail.

I also added: options dvb-usb-dib0700 force_lna_activation=1
to: /etc/modprobe.d/options
This has made no difference to the normal signal reception (50% ish) and no diference to the random 99% signal total failure to lock problem. Is there any way to find out if the lna has been activated?

Why does myth not realise that the tuner has no lock when it's recording?

Have I got the right firmware for my card? How do I find out?

This is all the info I have:

[   13.785470] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in cold state, will try to load a firmware
[   13.785475] firmware: requesting dvb-usb-dib0700-1.10.fw
[   15.793139] dvb-usb: downloading firmware from file 'dvb-usb-dib0700-1.10.fw'
[   16.520044] dvb-usb: found a 'Hauppauge Nova-TD-500 (84xxx)' in warm state.
[   16.522046] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.522344] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   16.761469] DVB: registering frontend 0 (DiBcom 7000PC)...
[   16.949006] dvb-usb: will pass the complete MPEG2 transport stream to the software demuxer.
[   16.949284] DVB: registering new adapter (Hauppauge Nova-TD-500 (84xxx))
[   17.109153] DVB: registering frontend 1 (DiBcom 7000PC)...
[   17.296940] dvb-usb: Hauppauge Nova-TD-500 (84xxx) successfully initialized and connected.
[   17.297244] usbcore: registered new interface driver dvb_usb_dib0700


Cheers,

Craig

---

### Post by ian dobson on 2009-01-16
Hi,

Can you try increasing the tuner timeout(it's in myth-setup under tuners). Increasing this value gives the tuner bit more time to lock onto the signal. I found it helped me with one of my DVB-c cards.

Regards
Ian Dobson

---

### Post by Vague Craig on 2009-01-16
Hi Ian

Yes I've tried increasing the tuning time, I think it's set to 800 mS at the moment. This seemed to improve things to start with though it still stops working after about a day.

When the fault occurs it happens to both tuners on the card and never works again unless I reboot, then it's all hunky dory again.

---

### Post by utar on 2009-01-16
> **Vague Craig said:**
> Hi Ian

Yes I've tried increasing the tuning time, I think it's set to 800 mS at the moment. This seemed to improve things to start with though it still stops working after about a day.

When the fault occurs it happens to both tuners on the card and never works again unless I reboot, then it's all hunky dory again.

I was having similar problems with my Nova T-500.  Try disabling EIT scanning on the second tuner.  You can get away with less tuning delay as well, I use 150ms.

---

### Post by Vague Craig on 2009-01-16
Cheers Utar, I'll try that when I get home.

---

### Post by Vague Craig on 2009-01-18
Well it's looking rather good, think you may have sorted out my irritating problem, Cheers Utah.

Removed the eit scanning on the second tuner on friday and I've been away for the whole weekend. The myth box has recorded all the shows and the tuners are still working!

Thanks again!

---

### Post by utar on 2009-01-19
> **Vague Craig said:**
> Well it's looking rather good, think you may have sorted out my irritating problem, Cheers Utah.

Removed the eit scanning on the second tuner on friday and I've been away for the whole weekend. The myth box has recorded all the shows and the tuners are still working!

Thanks again!

No problem, glad I could help.

---

