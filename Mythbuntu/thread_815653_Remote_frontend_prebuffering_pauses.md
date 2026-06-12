---
title: "Remote frontend prebuffering pauses"
date: 2008-06-01
forum: Mythbuntu
---

### Post by zoiks on 2008-06-01
I've just set up a mythfrontend on the laptop to connect to the existing HTPC frontend/backend combo.

It works great so far, with one exception: watching recordings has nasty prebuffering pauses

```
2008-06-01 17:54:59.385 Connected to database 'mythconverg' at host: coral
2008-06-01 17:54:59.540 Video timing method: USleep with busy wait
2008-06-01 17:55:01.099 NVP: prebuffering pause
2008-06-01 17:55:02.341 NVP: prebuffering pause
2008-06-01 17:55:03.493 NVP: prebuffering pause
2008-06-01 17:55:04.823 NVP: Prebuffer wait timed out 10 times.
2008-06-01 17:55:05.501 NVP: prebuffering pause
[...etc...]

```

Whereas Live TV does not:

```
2008-06-01 17:55:58.395 Video timing method: USleep with busy wait
2008-06-01 17:55:59.701 VideoOutputXv: XVideo Adaptor Name: 'NV17 Video Texture'
2008-06-01 17:55:59.836 AFD: Opened codec 0x7f719407ad60, id(MPEG2VIDEO) type(Vi
deo)
2008-06-01 17:55:59.836 AFD: codec AC3 has 2 channels
2008-06-01 17:55:59.836 AFD: Opened codec 0x7f719407a380, id(AC3) type(Audio)
2008-06-01 17:55:59.836 AFD: codec AC3 has 2 channels
2008-06-01 17:55:59.837 AFD: Opened codec 0x7f7194079340, id(AC3) type(Audio)
2008-06-01 17:56:00.065 Opening audio device 'default'. ch 2(2) sr 48000
2008-06-01 17:56:00.065 Opening ALSA audio device 'default'.
2008-06-01 17:56:00.180 AudioOutput Warning: Mixer attach error -2: No such file
 or directory
                        Check Mixer Name in Setup: '/dev/mixer'
2008-06-01 17:56:00.201 NVP: Enabling Audio
2008-06-01 17:56:00.439 NVP: Prebuffer wait timed out 10 times.

```

So, I don't get the reason why I'd get PBP's during recording playback but not Live TV. This is only on the remote frontend running on the laptop. The local frontend in the entertainment center has no pauses at all.

Any clues? Thanks in advance!

---

### Post by zoiks on 2008-06-03
Aw, crud. I found out whyfore the prebuffering pauses. My 802.11g network's too slow. I get (net, after overhead) 16Mb/s between the mythbox and my router, and 16Mb/s between the router and my laptop. Being a half-duplex connection at the router, the net bandwidth between the mythbox and the laptop is only 8Mb/s. Apparently, the 8Mb/s isn't quite enough for the higher bitrate videos in myth.

Bummer. Not sure there's much I can do about it. Transcoding will only work for recordings (not live TV) and then only after they've finished transcoding. 802.11n, AFAIK, isn't supported in Linux yet, and would require lots of new hardware.

---

### Post by volkswagner on 2008-06-03
Your first post suggests live TV is working OK on the laptop.  How did you determine network bandwidth?  I thought you and I had the same problem, although I have the symptoms with both LAN and WLAN.

---

### Post by zoiks on 2008-06-03
I determined the bandwidths by transferring large files using sftp and dividing bits by number of seconds. My server is connected via cable to the router itself, so there's effectively no delay there. Here's my data:

Transfer mythbox to laptop: 213MB in 191s, 8.92Mb/s
Transfer mythbox to server: 557MB in 273s, 16.32Mb/s
Transfer server to laptop: 270MB in 128s, 16.88Mb/s

In each case I just started transferring a very large file and stopped it when I felt there was plenty of data for the measurement.

It makes perfect sense since the radio on the WRT54G is half-duplex: it can only transmit or receive at any given instant, not both.

My mythbox has a dual-tuner PVR-500 and an HDHomeRun. I've successfully correlated my problem with the bandwidth of the video I was watching at the time. The lower bandwidth video files play just fine.

---

### Post by volkswagner on 2008-06-03
I am still curious about live HD performance.  Why would it play better?  Does live TV stream by default?  
Please correct me if I'm wrong.  I believe my HD recordings rarely get over 8gig/hr.  That would require < 3Mbs.  No?

---

### Post by zoiks on 2008-06-03
8gig/hr would be about 18Mb/s. Hence no-go on my system.

---

### Post by volkswagner on 2008-06-03
OK, thanks.  I guess I need to bone up on my bits and bytes.  Are you able to watch live HD?

---

### Post by zoiks on 2008-09-03
If anyone is interested, I managed to get this working quite well.

To refresh, the objective was to get good performance streaming video (hopefully including Live TV) from my wifi-connected myth backend to my laptop. This is with HDHomeRun-captured hi-def as well as video captured by the Hauppauge PVR-500.

I toyed around with solving the problem through transcoding and accepting that it would only work with recorded/transcoded video. But I managed a better solution.

The keys are:
[LIST]
[*]using two WRT54G APs in parallel (only one is an actual router/gateway) (a separate WRT54G is used in bridge mode to connect the mythbox to the wireless network)
[*]setting different values for the channel (and ssid) for the two APs (I used channels 1 and 11 for good separation/less interference)
[*]using better firmware (I was using OpenWRT White Russian and DD-WRT before, now I've switched to Tomato v1.21 and am very glad I did.)
[*]upping the TX power on all APs (to 80mW in my case)
[*]using Afterburner between the two WRT54G's that link to each other over wireless
[*]using Frame Bursting between the main router WRT54G and the laptop client
[*]keeping some distance (> 5 ft.) between the two ethernet-linked WRT54G's, as they will RF-jam each other if too close
[/LIST]

So, I get the benefits of effectively having full-duplex wifi connections, as well as the additional performance gained by using a better firmware (Tomato).

Here is a block diagram:

```

                            ______
 __________________  Ether |      |
|                  |=======| HDHR |
| WRT54GS (Bridge) |       |______|
| + Afterburner    |        _________
| SSID 1 Ch. 1     | Ether |         |
|__________________|=======| Mythbox |
         ~                 |_________|
         ~  Wifi
         ~  (~30 ft.)
 __________________          _____________________
|                  |        |                     |
| WRT54G (AP only) | Ether  | WRT54GL (AP/Router) |
| + Afterburner    |========| + Frame Burst       |
| SSID 1 Ch. 1     | ~7 ft. | SSID 2 Ch. 11       |
|__________________|        |_____________________|
                                    ~
                                    ~  Wifi
                                    ~  (~10-50 ft.)
                            ____________________
All WRT's:                 |                    |
  Tomato 1.21              | Laptop Myth Client |
  WPA TKIP                 | Intel 4965         |
  TX Power = 80mW          | SSID 2 Ch. 11      |
                           |____________________|

```

The Linksys WRT54G, GS, and GL are routers I'd had around that previously were put to other uses. The GL is the main router and wifi access point for my home network.

With this arrangement, each of the wireless legs is giving me ~2700KB/s average net throughput, as seen by ifstat during an sftp file transfer. The connection between the mythbox and the laptop is ~2600KB/s on average, sustained over 2500KB/s, even when the mythbox is sharing the WRT54GS with the HDHomeRun for watching Live TV.

These rates equate to 20mbps or higher net throughput, so there's about a 10% margin for viewing 1080i over the network. The only buffering pauses I get are when watching 1080i Live TV on the client laptop, and even then they are rare (maybe 3-4 times per hour).

So my performance now vs. before is like night and day. The Tomato firmware is awesome in usability and performance (though not fully GPL, AFAIK).

---

