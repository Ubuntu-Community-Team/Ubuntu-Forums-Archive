---
title: "Good analog TV tuner for Mythbuntu"
date: 2013-07-07
forum: Mythbuntu
---

### Post by ogogon on 2013-07-07
Good day!

Colleagues, please tell me what a modern analog TV tuner will work with Mythbuntu without problems?

I have Hauppauge WinTV PVR-150, but it's a nightmare. Run it fails and the available tips do not help...

Ogogon.

---

### Post by tgm4883 on 2013-07-07
> **ogogon said:**
> Good day!

Colleagues, please tell me what a modern analog TV tuner will work with Mythbuntu without problems?

I have Hauppauge WinTV PVR-150, but it's a nightmare. Run it fails and the available tips do not help...

Ogogon.

Is it broken? The PVR-150 is the defacto standard analog tv tuner for linux

---

### Post by ogogon on 2013-07-07
> **tgm4883 said:**
> Is it broken? The PVR-150 is the defacto standard analog tv tuner for linux
While I have not described any tuner, Myth starts normally.
As soon as I ask this tuner, the backend does not start and in the mythbackend.log I see:
```
Jul  7 23:16:40 muthbuntu mythbackend[3827]: N CoreContext main_helpers.cpp:556 (run_backend) MythBackend: Starting up as the master server.
Jul  7 23:16:40 muthbuntu mythbackend[3827]: E CoreContext tv_rec.cpp:1715 (GetStartChannel) TVRec(2): Problem finding starting channel, setting to default of '3'.
Jul  7 23:16:40 muthbuntu mythbackend[3827]: E CoreContext channelbase.cpp:940 (InitializeInputs) InitializeInputs(): #012#011#011#011Could not get inputs for the capturecard.#012#011#011#011Perhaps you have forgotten to bind video#012#011#011#011sources to your card's inputs?
Jul  7 23:16:40 muthbuntu mythbackend[3827]: E CoreContext channelbase.cpp:1229 (CreateChannel) ChannelBase: CreateChannel() Error: Failed to open device /dev/video0
Jul  7 23:16:40 muthbuntu mythbackend[3827]: E CoreContext main_helpers.cpp:196 (setupTVs) Problem with capture cardsCard 2failed init
Jul  7 23:16:40 muthbuntu mythbackend[3827]: W CoreContext main_helpers.cpp:211 (setupTVs) MythBackend: No valid capture cards are defined in the database.
Jul  7 23:16:40 muthbuntu mythbackend[3827]: E CoreContext scheduler.cpp:218 (VerifyCards) Scheduler: No channel sources defined in the database

```

If I use ivtv utilities, the stations are found. (I have to explain that I live in a city that enjoys a large cable network. And frequencys of the channels in it are not chosen according to the standard.)
```
ogogon@muthbuntu:/var/log/mythtv$ scantv -c /dev/video0 -C /dev/vbi0

please select your TV norm
   0: NTSC
   1: NTSC-M
   2: NTSC-M-JP
   3: NTSC-M-KR
   4: NTSC-443
   5: PAL
   6: PAL-BG
   7: PAL-H
   8: PAL-I
   9: PAL-DK
  10: PAL-M
  11: PAL-N
  12: PAL-Nc
  13: PAL-60
  14: SECAM
  15: SECAM-B
  16: SECAM-G
  17: SECAM-H
  18: SECAM-DK
  19: SECAM-L
  20: SECAM-Lc
nr ? 14

please select a frequency table
   0: us-bcast
   1: us-cable
   2: us-cable-hrc
   3: japan-bcast
   4: japan-cable
   5: europe-west
   6: europe-east
   7: italy
   8: newzealand
   9: australia
  10: ireland
  11: france
  12: china-bcast
  13: southafrica
  14: argentina
  15: australia-optus
  16: russia
nr ? 16
[global]
freqtab = russia

[defaults]
input = Television
norm = SECAM

invalid value for input: Television
valid choices for "input": "Tuner 1", "S-Video 1", "Composite 1", "S-Video 2", "Composite 2"

scanning channel list russia...
R1   ( 49.75 MHz): no station
R2   ( 59.25 MHz): no station
R3   ( 77.25 MHz): no station
R4   ( 85.25 MHz): no station
R5   ( 93.25 MHz): ???
[unknown (R5)]
channel = R5

R6   (175.25 MHz): no station
R7   (183.25 MHz): no station
R8   (191.25 MHz): no station
R9   (199.25 MHz): no station
R10  (207.25 MHz): no station
R11  (215.25 MHz): no station
R12  (223.25 MHz): no station
SR1  (111.25 MHz): no station
SR2  (119.25 MHz): no station
SR3  (127.25 MHz): no station
SR4  (135.25 MHz): no station
SR5  (143.25 MHz): no station
SR6  (151.25 MHz): no station
SR7  (159.25 MHz): no station
SR8  (167.25 MHz): no station
SR11 (231.25 MHz): no station
SR12 (239.25 MHz): no station
SR13 (247.25 MHz): no station
SR14 (255.25 MHz): no station
SR15 (263.25 MHz): no station
SR16 (271.25 MHz): no station
SR17 (279.25 MHz): no station
SR18 (287.25 MHz): no station
S19  (295.25 MHz): no station
S20  (303.25 MHz): no station
S21  (311.25 MHz): no station
S22  (319.25 MHz): no station
S23  (327.25 MHz): ???
[unknown (S23)]
channel = S23

S24  (335.25 MHz): no station
S25  (343.25 MHz): no station
S26  (351.25 MHz): no station
S27  (359.25 MHz): no station
S28  (367.25 MHz): no station
S29  (375.25 MHz): no station
S30  (383.25 MHz): no station
S31  (391.25 MHz): no station
S32  (399.25 MHz): no station
S33  (407.25 MHz): no station
S34  (415.25 MHz): no station
S35  (423.25 MHz): no station
S36  (431.25 MHz): no station
S37  (439.25 MHz): no station
S38  (447.25 MHz): no station
S39  (455.25 MHz): no station
S40  (463.25 MHz): no station
21   (471.25 MHz): no station
22   (479.25 MHz): no station
23   (487.25 MHz): no station
24   (495.25 MHz): no station
25   (503.25 MHz): no station
26   (511.25 MHz): no station
27   (519.25 MHz): no station
28   (527.25 MHz): no station
29   (535.25 MHz): no station
30   (543.25 MHz): no station
31   (551.25 MHz): no station
32   (559.25 MHz): no station
33   (567.25 MHz): no station
34   (575.25 MHz): no station
35   (583.25 MHz): no station
36   (591.25 MHz): no station
37   (599.25 MHz): no station
38   (607.25 MHz): no station
39   (615.25 MHz): no station
40   (623.25 MHz): no station
41   (631.25 MHz): no station
42   (639.25 MHz): no station
43   (647.25 MHz): no station
44   (655.25 MHz): no station
45   (663.25 MHz): no station
46   (671.25 MHz): no station
47   (679.25 MHz): no station
48   (687.25 MHz): no station
49   (695.25 MHz): no station
50   (703.25 MHz): no station
51   (711.25 MHz): no station
52   (719.25 MHz): no station
53   (727.25 MHz): no station
54   (735.25 MHz): no station
55   (743.25 MHz): no station
56   (751.25 MHz): no station
57   (759.25 MHz): no station
58   (767.25 MHz): no station
59   (775.25 MHz): no station
60   (783.25 MHz): no station
61   (791.25 MHz): no station
62   (799.25 MHz): no station
63   (807.25 MHz): no station
64   (815.25 MHz): no station
65   (823.25 MHz): no station
66   (831.25 MHz): no station
67   (839.25 MHz): no station
68   (847.25 MHz): no station
69   (855.25 MHz): no station
ogogon@muthbuntu:/var/log/mythtv$
```

If you turn off the antenna, the station is no longer detected. I believe that my tuner is not broken.

I have the latest distribution Mythbuntu.
```
ogogon@muthbuntu:/var/log/mythtv$ uname -a
Linux muthbuntu 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
ogogon@muthbuntu:/var/log/mythtv$
```However, from the previous was the same.

Ogogon.

---

### Post by tgm4883 on 2013-07-07
When you set the card up in mythtv-setup. What type of did you set the tuner as?

---

### Post by ogogon on 2013-07-07
> **tgm4883 said:**
> When you set the card up in mythtv-setup. What type of did you set the tuner as?
```
Tuner set as "MPEG-2 encoder card"
Video device - "/dev/video0"
Probed info - "Hauppauge Win-TV PVR-150 [ivtv]"
Tuning timeout (ms) - 12000
```
Still, just in case
```
ogogon@muthbuntu:/dev$ ls -alg video*
crw-rw----+ 1 video 81, 0 &#1080;&#1102;&#1083;&#1103;   8 00:12 video0
crw-rw----+ 1 video 81, 5 &#1080;&#1102;&#1083;&#1103;   8 00:12 video1
crw-rw----+ 1 video 81, 3 &#1080;&#1102;&#1083;&#1103;   8 00:12 video24
crw-rw----+ 1 video 81, 1 &#1080;&#1102;&#1083;&#1103;   8 00:12 video32
ogogon@muthbuntu:/dev$
```

Ogogon.

---

### Post by tgm4883 on 2013-07-07
Looking back at your logs. I wonder if it's bombing out because you didn't go though all the steps in mythtv-setup (eg. creating a video source and attaching it to a tuner)

---

### Post by ogogon on 2013-07-07
> **tgm4883 said:**
> Looking back at your logs. I wonder if it's bombing out because you didn't go though all the steps in mythtv-setup (eg. creating a video source and attaching it to a tuner)
I'm sorry, I think that my English is not very good.

So I do not quite understand who and what bombed. And what I have to do...

Ogogon.

---

### Post by tgm4883 on 2013-07-08
> **ogogon said:**
> I'm sorry, I think that my English is not very good.

So I do not quite understand who and what bombed. And what I have to do...

Ogogon.

You need to go though all the steps in mythtv-setup, meaning you need to setup a tuner AND a video source and then connect them. Here is a guide that might help [http://goo.gl/S54zL](http://goo.gl/S54zL)

---

### Post by ogogon on 2013-07-08
I guess I'm starting to understand what the problem is.

I need to compile and load the descriptor frequency channels in our cable network. They are not standard. This handle should be available in the "Video Sources".
Then I need to refer to this descriptor in "Input connections". This will bring up a list of channels with the desired frequency,
(That is, if I understand correctly architecture)

How do I create and upload a handle channels with non-standard frequencies?

Ogogon.

---

### Post by tgm4883 on 2013-07-08
> **ogogon said:**
> I guess I'm starting to understand what the problem is.

I need to compile and load the descriptor frequency channels in our cable network. They are not standard. This handle should be available in the "Video Sources".
Then I need to refer to this descriptor in "Input connections". This will bring up a list of channels with the desired frequency,
(That is, if I understand correctly architecture)

How do I create and upload a handle channels with non-standard frequencies?

Ogogon.

Not exactly. Section 4, "Video Sources" is where you get guide data. If you aren't getting guide data from anywhere, you still need to create something here (there is a setting for no grabber). Then in Section 5 "Input Connections", you need to connect the video source from step 4 to the tv tuner you set up in step 2.

---

### Post by grunge09 on 2013-07-12
I use the PVR-500, they are fairly cheap on eBay, and have dual analog tuners.  I have 3 in my back end server so I can record 6 streams at once.  Linux mythtv loves these cards.  They have dual onboard mpeg encoders so it takes a load off the CPU.   you only need one USB remote receiver and a remove control for the front end box.  Or just use a wireless keyboard.

---

### Post by tgm4883 on 2013-07-12
> **grunge09 said:**
> I use the PVR-500, they are fairly cheap on eBay, and have dual analog tuners.  I have 3 in my back end server so I can record 6 streams at once.  Linux mythtv loves these cards.  They have dual onboard mpeg encoders so it takes a load off the CPU.   you only need one USB remote receiver and a remove control for the front end box.  Or just use a wireless keyboard.

Just a quick note. The PVR-500 is literally 2 PVR-150's on the same board.

---

