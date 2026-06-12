---
title: "HDHomerun Connect Dual Tuner problems"
date: 2015-05-17
forum: Mythbuntu
---

### Post by afremont on 2015-05-17
I downloaded the latest Mythbuntu, clean installed on new hardware, installed the updates and configured it.  By following the information from Silicondust and various wiki articles, I got it to see both tuners in my HDHomerun box.  I set one tuner so that the scheduler would never use it by making the priority 0.  I set up some sample recordings to test everything and I'm having a strange issue.  

I noticed that the HDHomerun is capable of streaming more than one sub-channel at a time using only one of the built in tuners.  That's pretty cool.  When I only had one tuner configured, the EPG would let me manually record one sub-channel and playback a different sub-channel.  I could see the EPG changed colors to show what I could pick from and using the up-arrow key I could run through the various sub-channels.  Now that I have both tuners configured, it still limits me the same way when something is recording, even though I can tell that MythTV is using the other tuner for the live TV.  IOW, even though it properly selects the other tuner, it will only allow me to choose sub-channels as if it is using a single tuner for both streams.

Any ideas?  I searched the forums a bit and couldn't find a solution. I'm trying to move away from WMC.  I ran MythTV about 10 years ago, looks like it's improved quite a bit.  I appreciate the work everyone has done with it.

It is set up as two Capture Cards:
   192.168.2.18-0
   192.168.2.18-1
One Video Source:
   Antenna
Two Input Connections:
   [HDHomerun: 192.168.2.18-0] (MPEG2TS) -> Antenna
   [HDHomerun: 192.168.2.18-1] (MPEG2TS) -> Antenna

I deleted the Capture Cards and set it all up again using the device id instead of the ip address.  That seems to have fixed the problem I was having.  I have 4 tuners now according the MythTV.  Does that sound right?  It seems strange to me, but maybe that's how it handles multiple sub-channel streams from one physical tuner?

Now it's jerking when I play Live TV.  It was working so beautifully before using Opengl High Quality, now it isn't looking so hot.  My network is Gigabit and I'm using an I3-4370 and an H97 chipset board.  I'm using the built in Intel graphics for now, but I will likely be getting an nVidia based card if it will solve all this deinterlace and decode performance issues.

UPDATE:  Possibly have my problem solved
I followed the advice of: [https://www.mythtv.org/wiki/VAAPI](https://www.mythtv.org/wiki/VAAPI)
**[COLOR=#0000ff]sudo apt-get install libva1 i965-va-driver libva-intel-vaapi-driver vainfo[/COLOR]**
and that seems to have lowered my CPU usage significantly.  I'm using OpenGL VAAPI.  I also changed the "painter" from Qt to Auto as the guide instructed.

---

