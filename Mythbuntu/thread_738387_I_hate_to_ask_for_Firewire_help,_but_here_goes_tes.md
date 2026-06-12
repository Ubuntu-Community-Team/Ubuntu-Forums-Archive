---
title: "I hate to ask for Firewire help, but here goes: test-mpeg2 works, Myth does not!"
date: 2008-03-28
forum: Mythbuntu
---

### Post by grytpype on 2008-03-28
Any help with my Firewire problem would be greatly appreciated!  

I've exhausted all resources trying to solve the problem but I think I have it isolated.

Running Mythbuntu 8.04 beta, mythtv version 0.21.0-0ubuntu3

STB is a SA 4250HD (not HDC).  It was working fine with a .20 install (now long gone).  The STB identifies itself to Myth as "SA 4300 VL_SA_Jun062005 17:20:27"  

Plugreport, firewire_tester, and the p2p primer script work 100%.

test_mpeg2 works 100%, I've captured 30 sec. of HD and played it back.

Now for the problem:

Setting this up as a Firewire capture card, SA4250HDC, p2p,  at speed of 200 or 400, gives the following result:

I get a LAM lock just fine.  Then, about 2 seconds of video, then it freezes.

After that, plugreport doesn't show anything except the adapter, firewire_tester fails 100%.

If I remove all FW modules (raw1394 dv1394 ohci1394 ieee1394) and reinstall them, it gets me back to Square 1, with plugreport, firewire_tester, etc. working again.

I've tried configuring the card in myth-setup as SA4200HD and SA3250HD, and they are no better.

Relevant part of mythbackend.log:
2008-03-28 14:11:07.049 TVRec(5): Changing from None to WatchingLiveTV
2008-03-28 14:11:07.057 TVRec(5): HW Tuner: 5->5
2008-03-28 14:11:07.070 FireDev(001CEA0DC7A80000): The Scientific Atlanta 4250 HDC is not su
pported 
                        by any MythTV Firewire channel changer.At the moment you must use an
 IR blaster.
2008-03-28 14:11:07.084 SetLastChannel(11): cleared: yes
2008-03-28 14:11:08.164 AutoExpire: CalcParams(): Max required Free Space: 3.0 GB w/freq: 15
 min
libiec61883 warning: Overlayed connection on channel 1.
You may need to manually set the channel on the receiving node.
2008-03-28 14:11:08.194 LFireDev(001CEA0DC7A80000): Buffered packets 2000 (8000 KB)
2008-03-28 14:11:08.585 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/vid
eos:
2008-03-28 14:11:08.591 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-03-28 14:11:09.038 Finished recording Judge Mathis: channel 1011
2008-03-28 14:11:10.099 Finished recording Judge Mathis: channel 1011
2008-03-28 14:11:10.162 LFireDev(001CEA0DC7A80000): Buffered packets 2000 (8000 KB)
2008-03-28 14:11:10.183 LFireDev(001CEA0DC7A80000), Warning: No Input in 50 msec...
2008-03-28 14:11:10.437 Using runtime prefix = /usr, libdir = /usr/lib
2008-03-28 14:11:10.443 Empty LocalHostName.
2008-03-28 14:11:10.444 Using localhost value of eccles
2008-03-28 14:11:10.458 New DB connection, total: 1
2008-03-28 14:11:10.466 Connected to database 'mythconverg' at host: localhost
2008-03-28 14:11:10.468 Closing DB connection named 'DBManager0'
2008-03-28 14:11:10.469 Connected to database 'mythconverg' at host: localhost
2008-03-28 14:11:10.472 New DB connection, total: 2
2008-03-28 14:11:10.473 Connected to database 'mythconverg' at host: localhost
2008-03-28 14:11:10.476 Current Schema Version: 1214
2008-03-28 14:11:10.489 Preview Error: Previewer file '/media/storage01/1011_20080328141107.mpg' is not valid.
2008-03-28 14:11:10.491 Preview Error: Run() file not local: '/media/storage01/1011_20080328141107.mpg'
2008-03-28 14:11:10.515 Preview Error: Preview process not ok.
                        fileinfo(/media/storage01/1011_20080328141107.mpg.png) exists: 0 readable: 0 size: 0
2008-03-28 14:11:10.605 LFireDev(001CEA0DC7A80000), Warning: No Input in 100 msec...
2008-03-28 14:11:10.661 LFireDev(001CEA0DC7A80000), Warning: No Input in 150 msec...
2008-03-28 14:11:10.712 LFireDev(001CEA0DC7A80000), Warning: No Input in 200 msec...
2008-03-28 14:11:10.764 LFireDev(001CEA0DC7A80000), Warning: No Input in 250 msec...
......etc......

Mythfrontend.log:
2008-03-28 14:04:53.335 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-03-28 14:04:53.423 OSD Theme Dimensions W: 640 H: 480
2008-03-28 14:04:53.921 TV: Changing from None to WatchingLiveTV
2008-03-28 14:04:53.928 Realtime priority would require SUID as root.
Initialize Yadif Deinterlacer. In-Pixformat = 1 Out-Pixformat=1
yadifdeint: size changed from 0 x 0 -> 720 x 576
2008-03-28 14:04:54.029 OpenGLVideoSync()
2008-03-28 14:04:54.102 Video timing method: SGI OpenGL
2008-03-28 14:04:58.959 [mpeg2video @ 0x7f63e173c990]skipped MB in I frame at 6 8
2008-03-28 14:04:58.963 [mpeg2video @ 0x7f63e173c990]Warning MVs not available
2008-03-28 14:04:58.994 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
yadifdeint: size changed from 720 x 576 -> 704 x 480
2008-03-28 14:04:59.720 AFD: Opened codec 0x7f63cc1c75e0, id(MPEG2VIDEO) type(Video)
2008-03-28 14:04:59.720 AFD: codec AC3 has 2 channels
2008-03-28 14:04:59.721 AFD: Opened codec 0x7f63cc1ce100, id(AC3) type(Audio)
2008-03-28 14:04:59.857 Opening audio device 'default'. ch 2(2) sr 48000
2008-03-28 14:04:59.857 Opening ALSA audio device 'default'.
2008-03-28 14:04:59.980 mixer unable to find control Master 1
2008-03-28 14:04:59.982 NVP: Enabling Audio
2008-03-28 14:05:00.037 [mpeg2video @ 0x7f63e173c990]skipped MB in I frame at 6 8
2008-03-28 14:05:00.041 [mpeg2video @ 0x7f63e173c990]Warning MVs not available
2008-03-28 14:05:02.245 NVP: prebuffering pause
2008-03-28 14:05:02.246 WriteAudio: buffer underrun
2008-03-28 14:05:03.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:05.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:06.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:08.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:09.207 RingBuf(/media/storage01/1011_20080328140455.mpg): Waited 8.0 seconds for data to become available...
2008-03-28 14:05:09.207 Checking to see if there's a new livetv program to switch to..
2008-03-28 14:05:09.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:11.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:12.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:14.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:15.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:17.209 RingBuf(/media/storage01/1011_20080328140455.mpg) Error: Waited 16 seconds for data, aborting.
2008-03-28 14:05:17.218 NVP: Prebuffer wait timed out 10 times.

2008-03-28 14:05:14.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:15.718 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:17.209 RingBuf(/media/storage01/1011_20080328140455.mpg) Error: Waited 16 s
econds for data, aborting.
2008-03-28 14:05:17.218 NVP: Prebuffer wait timed out 10 times.
2008-03-28 14:05:17.845 [mpeg2video @ 0x7f63e173c990]ac-tex damaged at 14 20
2008-03-28 14:05:18.718 NVP: Prebuffer wait timed out 10 times.
......etc.....

---

### Post by 4dognight on 2008-03-28
This looks familiar, when I upgraded to .21
I think I resolved it by unchecking that new check box related to firewire. I cant recall exactly the title of the check box. It had something to do with firewire and the bus reset.

---

### Post by grytpype on 2008-03-28
> **4dognight said:**
> This looks familiar, when I upgraded to .21
I think I resolved it by unchecking that new check box related to firewire. I cant recall exactly the title of the check box. It had something to do with firewire and the bus reset.

Thanks for that suggestion, but I just tried it and I still have the problem (no matter how the checkbox is set).  Thanks again!

Anyone have any other hints???

---

### Post by grytpype on 2008-03-29
I'm starting to think it's my VIA chipset.  This is a new mobo, and it has a VIA instead of an NVIDIA chipset, which may be a mistake.  

It turns out my PVR-250 card isn't working either, two seconds of video and then it freezes with a DMA TIMEOUT error in syslog.  VIA is rumored to have DMA problems, it may be affecting both PCI cards (the PVR and Firewire).  It's relatively cheap to get a new mobo so I am going to do that.

---

