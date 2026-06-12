---
title: "Streaming tv over mplayer in Jaunty"
date: 2009-04-25
forum: Multimedia Software
---

### Post by sofasurfer on 2009-04-25
In Hardy I could never accomplish tv streaming using the Hauppauge1600 PVR card because of all of the driver issues and such. Then when Intrepid came out my card was instantly recognized and issuing 'sudo apt-get install dvb-utils' and 'scan -U /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf.atsc' gave me tv with no effort.

Now with Jaunty I installed the dvb-utils package and then when I ran 'scan -U /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB > ~/.mplayer/channels.conf.atsc' to scan for channels I got this error...
```

scanning /usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB
using '/dev/dvb/adapter0/frontend0' and '/dev/dvb/adapter0/demux0'
ERROR: cannot open '/usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB': 2 No such file or directory
ERROR: initial tuning failed
dumping lists (0 services)
Done.

```

Any idea where I scewed up?

---

### Post by sofasurfer on 2009-04-25
I tried browsing to... /dev/dvb/adapter0/frontend0 and I got the following error...
```

Could not display "/dev/dvb/adapter0/frontend0". There is no application installed for this file type.

```

And the same result when I browsed to /dev/dvb/adapter0/demux0

I also tried browsing to '/usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB' but could only get as far as '/usr/share/doc/dvb-utils' and there is no '/examples' directory.

Another point is this. I am able to view analog tv with VLC.

---

### Post by sofasurfer on 2009-04-26
I made some progress. In my last post I said that I tried to browse to 
'/usr/share/doc/dvb-utils/examples/scan/atsc/us-ATSC-center-frequencies-8VSB' but there was no '/examples' directory. So I copied the 'examples' directory and it contents from my Intrepid system and pasted it into the proper location in the new Jaunty system.

Now when I scan for channels it works and the channel list is the same as in the Intrepid system.

But when I run 'mplayer dvb://' to try to view a channel I get the following message...
```

MPlayer 1.0rc2-4.3.3 (C) 2000-2007 MPlayer Team
CPU: AMD Sempron(tm) Processor LE-1250 (Family: 15, Model: 127, Stepping: 2)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 1 3DNow2: 1 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing dvb://.
UNKNOWN TUNER TYPE
DVB CONFIGURATION IS EMPTY, exit
Failed to open dvb://.


Exiting... (End of file)

```

Can any help with this?

---

### Post by thewolfman on 2009-04-26
Download and use kaffeine, yes it is a KDE app but works great, another option is me-tv which works equally well.

I have dvb-t and use both progs under Ubuntu.

---

### Post by sofasurfer on 2009-04-26
Goody. These are sure easier to use than mplayer was. Thanks. 
But 2 issues... How to change channels? In ME-TV auto scan works but how to change to a particular channel in ME-TV and Kaffeine eludes me. 

And in mplayer I always got channel 5.1, 5.2, 5.3. In Kaffeine I do not get any 5's. What process cause the signal to be detectable in mplayer but not Kaffeine? And how can I edit the Kaffeine channel list to include 5? I can get channel name and freqency from mplayers channel list but there are other specs that need to be added when editing Kaffeines channel list.

Thanks.

---

### Post by laceration on 2009-10-16
Better late than never!

I believe there was a MPlayer bug that caused your problems.

[https://bugs.launchpad.net/ubuntu/+s...er/+bug/369349](https://bugs.launchpad.net/ubuntu/+s...er/+bug/369349)

Even though your dvb card has a different Conexant chip than reported in the bug, this bug seems to affect more dvb devices than referred to in the bug report. The software defect in MPlayer is repaired in the version used in Karmic, so if you upgrade it should solve your problem.

---

