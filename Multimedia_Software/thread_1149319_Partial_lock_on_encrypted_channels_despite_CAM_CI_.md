---
title: "Partial lock on encrypted channels despite CAM CI + smartcard"
date: 2009-05-05
forum: Multimedia Software
---

### Post by lanthonyann on 2009-05-05
Hi,

I've decided to set up a mythbox based on DVB-C reception. I'm working on MythBuntu 9.04. I've got a FloppyDTV C/CI ([http://www.digital-everywhere.com/en/alcms/index.php?sid=1187727697](http://www.digital-everywhere.com/en/alcms/index.php?sid=1187727697)) that I finally got working by compiling a new kernel with the dedicated modules. I've correctly plugged the PowerCam HD with my smartcard inside.
Configuration is quite OK with MythTV : I was able to scan my channels and to watch the unencrypted ones.

But here is my problem : when I try to watch a encrypted channel, I only get a partial lock. I can see LSMc near the signal informations (it was LAMc some days ago, I don't really know why it has changed). I know that the c becomes a C after a few seconds when mythTV is able to decrypt the channel, but in my case, it's stuck on c.
The strange thing is that everything is working fine with Kaffeine. I can watch both encrypted and unencrypted channels. That makes me thing that this is not a driver issue.

I thought that it was a problem of communication between mythTV and my CAM module, but when I start mythbackend with the verbose on dvbcam :

```

nciut@nciut-desktop:/$ sudo mythbackend -v dvbcam
2009-05-05 09:20:34.635 Using runtime prefix = /usr
2009-05-05 09:20:34.636 Empty LocalHostName.
2009-05-05 09:20:34.636 Using localhost value of nciut-desktop
2009-05-05 09:20:34.640 New DB connection, total: 1
2009-05-05 09:20:34.642 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:20:34.642 Closing DB connection named 'DBManager0'
2009-05-05 09:20:34.643 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:20:34.643 New DB connection, total: 2
2009-05-05 09:20:34.643 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:20:34.644 Current Schema Version: 1214
Starting up as the master server.
[B]New High level CI handler
2009-05-05 09:20:34.693 DVB#0 CA: CI handler thread running
2009-05-05 09:20:34.693 DVB#0 CA: CI handler successfully initialized![/B]
Sending message=[9f 80 30 ]
2009-05-05 09:20:34.693 New DB connection, total: 3
2009-05-05 09:20:34.694 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:20:34.698 DVBChan(4:0) Warning: Unsupported fec_inner parameter.
Sending message=[9f 80 31 ]
Debug: 159 128 49 2 2 202 0 0 4 0 0 0 144 124 177 9 172 219 214 181 
2009-05-05 09:20:35.253 DVBChan(7:0) Warning: Unsupported fec_inner parameter.
2009-05-05 09:20:35.781 New DB scheduler connection
2009-05-05 09:20:35.781 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:20:36.988 Main::Registering HttpStatus Extension
2009-05-05 09:20:36.988 mythbackend version: 0.21.20080304-1 www.mythtv.org
2009-05-05 09:20:36.988 Enabled verbose msgs:  important general dvbcam
2009-05-05 09:20:36.988 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2009-05-05 09:20:38.783 Reschedule requested for id -1.
2009-05-05 09:20:38.790 Scheduled 0 items in 0.0 = 0.00 match + 0.01 place
2009-05-05 09:20:38.791 Seem to be woken up by USER

```These three lines seem to tell that my powercam is well recognized.

This is what I get when I try to watch an encrypted channel :
```

2009-05-05 09:25:35.225 TVRec(4): HW Tuner: 4->4
2009-05-05 09:25:36.147 DVBChan(4:0) Warning: Unsupported fec_inner parameter.
2009-05-05 09:25:37.684 Finished recording Unknown: channel 8501
2009-05-05 09:25:37.722 Using runtime prefix = /usr
2009-05-05 09:25:37.723 Empty LocalHostName.
2009-05-05 09:25:37.723 Using localhost value of nciut-desktop
2009-05-05 09:25:37.727 New DB connection, total: 1
2009-05-05 09:25:37.729 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:25:37.730 Closing DB connection named 'DBManager0'
2009-05-05 09:25:37.730 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:25:37.730 New DB connection, total: 2
2009-05-05 09:25:37.730 Connected to database 'mythconverg' at host: localhost
2009-05-05 09:25:37.731 Current Schema Version: 1214
2009-05-05 09:25:37.879 AFD: Opened codec 0xa22daf0, id(MPEG2VIDEO) type(Video)
2009-05-05 09:25:37.879 AFD: codec MP3 has 2 channels
2009-05-05 09:25:37.879 AFD: Opened codec 0xa22e0e0, id(MP3) type(Audio)
2009-05-05 09:25:37.879 AFD: codec MP3 has 2 channels
2009-05-05 09:25:37.879 AFD: Opened codec 0xa22e6d0, id(MP3) type(Audio)
2009-05-05 09:25:37.898 DVBSM(0), Warning: Can not count Uncorrected Blocks
            eno: Operation not supported (95)
2009-05-05 09:25:37.900 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15 min
2009-05-05 09:25:37.913 Preview: Grabbed preview '/var/lib/mythtv/recordings/8501_20090505092522.mpg' 720x576@64s
2009-05-05 09:25:38.781 DVB#0 CA: CiHandler needs CA_PMT
2009-05-05 09:25:38.781 DVB#0 CA: Creating CA_PMT, ServiceID = 9200
2009-05-05 09:25:38.781 Adding elementary stream: video-h264, pid(0x48)
2009-05-05 09:25:38.781 Adding elementary stream: audio-mp1-layer[1,2,3] (fre), pid(0x49)
2009-05-05 09:25:38.781 Adding elementary stream: audio-mp1-layer[1,2,3] (eng), pid(0x4a)
2009-05-05 09:25:38.781 Adding elementary stream: private-data, pid(0x69)
2009-05-05 09:25:38.781 Adding elementary stream: audio-ac3 (fre), pid(0x84)
2009-05-05 09:25:38.781 DVB#0 CA: Sending CA_PMT with CPLM_ONLY to CI slot #0
Setting CA PMT.
Sending message=[9f 80 32 ]
2009-05-05 09:25:39.293 DTVSM(0) Error: Wrong PMT; pmt->pn(9212) desired(9200)
2009-05-05 09:25:39.293 DTVSM(0) Error: Wrong PMT; pmt->pn(9203) desired(9200)
2009-05-05 09:25:39.294 DTVSM(0) Error: Wrong PMT; pmt->pn(9204) desired(9200)
2009-05-05 09:25:40.350 PID 0x48 status: Encrypted
2009-05-05 09:25:41.155 PID 0x84 status: Encrypted
2009-05-05 09:25:41.959 PID 0x49 status: Encrypted
2009-05-05 09:25:42.009 PID 0x4a status: Encrypted

```If you have any idea that could be helpful :)

Thank you.

---

### Post by StanleyKowalsky on 2009-06-18
Same Problem here.

Any Ideas?

---

### Post by JS36 on 2009-09-28
Any solutions to this problem yet? Having same problem too... :(

---

