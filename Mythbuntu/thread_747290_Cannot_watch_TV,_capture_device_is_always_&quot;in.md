---
title: "Cannot watch TV, capture device is always &quot;in use&quot;"
date: 2008-04-06
forum: Mythbuntu
---

### Post by pagingmrherman on 2008-04-06
Hi, I've installed a PVR-250 in an IBM ThinkCenter and did a fresh mythbuntu install (7.10).  I cannot get mythtv (or tvtime for that matter) to watch TV.  No matter what I do, I always get an error message saying all the capture devices are in use. I can do a 'cat /dev/video0 >test.mpg' and I see video in test.mpg  w/ no problem.  I can also change the channels w/ no problem using the ivtv-tools.  What the heck is going on here????

Here's the output of dmesg | grep ivtv:

[   34.502870] ivtv:  ==================== START INIT IVTV ====================
[   34.502875] ivtv:  version 1.0.0 (2.6.22-14-generic SMP mod_unload 586 ) loading
[   34.908631] ivtv0: Autodetected Hauppauge card (cx23416 based)
[   34.910212] ivtv0: Unreasonably low latency timer, setting to 64 (was 32)
[   35.582859] ivtv0: loaded v4l-cx2341x-enc.fw firmware (3584711808 bytes)
[   35.797947] ivtv0: Encoder revision: 0x02050032
[   35.797951] ivtv0: Recommended firmware version is 0x02060039.
[   35.858741] ivtv0: Autodetected Hauppauge WinTV PVR-250
[   35.881209] tuner 0-0043: chip found @ 0x86 (ivtv i2c driver #0)
[   35.884433] tuner 0-0061: chip found @ 0xc2 (ivtv i2c driver #0)
[   35.939004] saa7115 0-0021: saa7115 found (1f7115d0e100000) @ 0x42 (ivtv i2c driver #0)
[   36.086668] msp3400 0-0040: MSP4448G-A2 found @ 0x80 (ivtv i2c driver #0)
[   36.365494] ivtv0: Registered device video0 for encoder MPEG (4 MB)
[   36.365836] ivtv0: Registered device video32 for encoder YUV (2 MB)
[   36.366151] ivtv0: Registered device vbi0 for encoder VBI (1 MB)
[   36.366361] ivtv0: Registered device video24 for encoder PCM audio (1 MB)
[   36.366693] ivtv0: Registered device radio0 for encoder radio
[   36.432879] ivtv0: Initialized Hauppauge WinTV PVR-250, card #0
[   36.432910] ivtv:  ====================  END INIT IVTV  ====================


Here's the output of lsmod | grep ivtv:

ivtv                  134928  0 
i2c_algo_bit            7428  1 ivtv
cx2341x                13316  1 ivtv
tveeprom               16784  1 ivtv
videodev               29312  1 ivtv
v4l2_common            18432  6 msp3400,saa7115,tuner,ivtv,cx2341x,videodev
v4l1_compat            15364  2 ivtv,videodev
i2c_core               26112  7 msp3400,saa7115,tuner,ivtv,i2c_algo_bit,nvidia,tveeprom

Any help would be greatly appreciated,

PW

---

### Post by volkswagner on 2008-04-06
What does information center say about the status for the tuner?

It may help if you post your backend log for the time when trying to watch live tv.

/var/log/mythtv/mythbackend.log

---

### Post by pagingmrherman on 2008-04-08
The information center says "tuner 1 is unavailable" on the Tuner Status.

Here's a copy of the /var/log/mythv/mythbackend.log:

2008-04-08 00:02:23.876 Using runtime prefix = /usr
2008-04-08 00:02:23.897 New DB connection, total: 1
2008-04-08 00:02:23.903 Connected to database 'mythconverg' at host: localhost
2008-04-08 00:02:23.907 Current Schema Version: 1160
Starting up as the master server.
2008-04-08 00:02:23.919 New DB connection, total: 2
2008-04-08 00:02:23.920 Connected to database 'mythconverg' at host: localhost
2008-04-08 00:02:23.923 EITHelper: localtime offset -4:00:00 
2008-04-08 00:02:23.928 TVRec(1) Error: Problem finding starting channel, setting to default of '3'.
2008-04-08 00:02:23.930 ChannelBase(1) Error: InitializeInputs(): 
                        Could not get inputs for the capturecard.
                        Perhaps you have forgotten to bind video
                        sources to your card's inputs?
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
2008-04-08 00:02:25.182 Main::Registering HttpStatus Extension
2008-04-08 00:02:25.183 mythbackend version: 0.20.20070821-1 [www.mythtv.org](www.mythtv.org)
2008-04-08 00:02:25.194 Enabled verbose msgs:  important general
2008-04-08 00:02:25.203 AutoExpire: Found 0 recorders w/max rate of 0 MiB/min
2008-04-08 00:02:25.212 AutoExpire: Required Free Space: 1.0 GB w/freq: 10 min
2008-04-08 00:03:32.170 MainServer::HandleAnnounce Monitor
2008-04-08 00:03:32.181 adding: ginger as a client (events: 0)
2008-04-08 00:03:32.183 MainServer::HandleAnnounce Monitor
2008-04-08 00:03:32.183 adding: ginger as a client (events: 1)
2008-04-08 00:05:53.604 MainServer: HandleRemoteEncoder(cmd GET_STATE) Unknown encoder: 1

---

### Post by volkswagner on 2008-04-08
When in mythtv backend setup, you must complete all steps for setting up a tuner.

[LIST=1]
[*]Capture Cards=Tuner-Create new tuner, select your device type, and default input.
[*]Video source-Create your lineup with schedules direct, enter your info here, Name your lineup with a unique name for you to recognize.
[*]Input connections-Select the input for the card, TV=Coax, or S-video, whichever you are connected to, Here you assign the created Video source (channel lineup) to the input on the card.  Fetch the channels from source (schedules direct)
[*]Channel editor can be used to tweak the lineup
[/LIST]

---

### Post by gazer22 on 2008-04-08
PW - 
I had the same issue (recent install w/ Hauppuge 350).

Deleting the card, the video source, and the input connections from the mythtv backend setup, and then re-doing the settings as volkswagner gave above worked for me.

---

### Post by pagingmrherman on 2008-04-10
Damn, it had been so long since I last set it up I didn't know you had to link the video source to the input.  This got broken somehow when I did 2 upgrades in a row to go from Edgy to Gutsy.  Also, I think my SQL database got screwed up in the process too since I have another front end.
Ugh, had to redo everything from scratch.

---

