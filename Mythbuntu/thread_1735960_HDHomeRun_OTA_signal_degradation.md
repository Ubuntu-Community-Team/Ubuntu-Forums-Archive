---
title: "HDHomeRun OTA signal degradation"
date: 2011-04-22
forum: Mythbuntu
---

### Post by davidstoll on 2011-04-22
Recently I've noticed _**every single**_ OTA channel has garble/blocks/corruption (seemingly low signal), but the actual signal levels range from 80-100%.  The corruption is exactly like if you had low signal.

I have the latest firmware on the Silicon Dust HDHomeRun.  I can tune to the channels and they are perfect when the antenna line is connected directly to my TV.

I have a TV tower with a tower mounted amp and a rotary. My analog cable comes in just fine.  I've tried both inputs on my HDHomeRun for OTA.  I have also played with the rotary and am not able to fix the issue.

I have also re-scanned and rebooted the unit.  I've been running with this setup for quite some time (from 8.04 to 10.10 32bit).

I'm using 0.24 but just recently upgraded from 0.23 (in the last couple of days), but the problem occurred before that for several weeks.

I also can use the HDHomeRun config utility on another machine (windows) and can tune to the channels and they look absolutely beautiful.  Not a glitch or hiccup.

If anyone else has ideas, I sure would appreciate it.

---

### Post by winsecure on 2011-04-22
Possibly network saturation?  I'm a complete newb, but I believe that Homerun transmits the data via UDP rather than TCP.  Wondering if you have network errors and/or saturation thats causing some UDP packets to not arrive at the Backend.

---

### Post by davidstoll on 2011-04-22
Well, that is unlikely because there is not much of anything going on between those two connections.  They are on their own sub switch.  Everything in the network including the backend are gigabit.  Only the HDHomeRun is 100Mb I believe.

---

### Post by LowSky on 2011-04-22
Try playing an HD video file in MythTV. I'm thinking it could actually be the video card failing at high temperatures. If you can take one of these files and try to play them on another PC or media device to check the quality.

It could also be a failure of the Ethernet cable to your Mythtv backend. Ports can die. It happened to me on my last Motherboard. Try testing it by trying to play something off hulu or youtube and see if you get constant drops or loading screens while playing HD content.

If you connections speed is too slow for that kind of test, just set up a ping test from the terminal with a command like so

```
ping -c 50 www.google.com
```

the number can be anything you like

---

### Post by davidstoll on 2011-04-23
Excellent idea to play a recorded file directly on another computer.  When I played the files, the digital artifacts (garble) matched exactly.  That tells me they were recorded that way, so it's not a playback issue.  I'm glad you mentioned that.

What was interesting though was that some of the files did not play back.  I opened VLC on a Windows machine.  Some played ok, but others opened a black screen (of appropriate size..720, 1080, 480, etc), but didn't actually play anything.  The time stamp was frozen at 00:00/00:00.  In fact, only one particular channel's recordings would actually play back.  I couldn't get any of the other channel's recordings to play back on another machine directly.  I even tried to advance the timeline. By the way the particular channel's recordings that did play happened to be 1080p.

MediaInfo shows that all files have info that I would expect.  Nothing out of the ordinary.

I have a 10Mb/s connection and I just tested it from 3 different websites, one of which was from my ISP.  All looks good.

64 bytes from 74.125.225.17: icmp_req=1 ttl=54 time=15.1 ms
64 bytes from 74.125.225.17: icmp_req=2 ttl=54 time=15.2 ms
64 bytes from 74.125.225.17: icmp_req=3 ttl=54 time=14.6 ms
64 bytes from 74.125.225.17: icmp_req=4 ttl=54 time=12.8 ms
64 bytes from 74.125.225.17: icmp_req=5 ttl=54 time=11.9 ms
64 bytes from 74.125.225.17: icmp_req=6 ttl=54 time=12.1 ms
64 bytes from 74.125.225.17: icmp_req=7 ttl=54 time=12.3 ms
64 bytes from 74.125.225.17: icmp_req=8 ttl=54 time=15.6 ms
64 bytes from 74.125.225.17: icmp_req=9 ttl=54 time=15.0 ms
^C64 bytes from 74.125.225.17: icmp_req=10 ttl=54 time=13.8 ms

I am going to reboot the switch they are both connected to and replace the ethernet cables.


> **LowSky said:**
> Try playing an HD video file in MythTV. I'm thinking it could actually be the video card failing at high temperatures. If you can take one of these files and try to play them on another PC or media device to check the quality.

It could also be a failure of the Ethernet cable to your Mythtv backend. Ports can die. It happened to me on my last Motherboard. Try testing it by trying to play something off hulu or youtube and see if you get constant drops or loading screens while playing HD content.

If you connections speed is too slow for that kind of test, just set up a ping test from the terminal with a command like so

```
ping -c 50 www.google.com
```

the number can be anything you like

---

### Post by davidstoll on 2011-04-23
:(

Cable changes didn't help.

---

### Post by LowSky on 2011-04-23
[http://www.silicondust.com/support/hdhomerun/downloads/linux/](http://www.silicondust.com/support/hdhomerun/downloads/linux/)

maybe install the drivers a from source?

---

### Post by Dewey_Oxberger on 2011-04-23
How old is your HDHomeRun?

Two/three years ago they had a batch with bad power supplies.  As the supply aged its noise increased and it produced symptoms similar to what you are seeing.  It's a long shot.

Also, I've had a bad network switch that caused the same trouble.  The only symptom of the bad switch was I couldn't watch OTA with the HDHR.  Replaced the switch and it has worked for years.

---

### Post by davidstoll on 2011-04-24
> **Dewey_Oxberger said:**
> How old is your HDHomeRun?

Two/three years ago they had a batch with bad power supplies.  As the supply aged its noise increased and it produced symptoms similar to what you are seeing.  It's a long shot.

Also, I've had a bad network switch that caused the same trouble.  The only symptom of the bad switch was I couldn't watch OTA with the HDHR.  Replaced the switch and it has worked for years.

I changed out the switch to eliminate that...no joy though.

I'm not sure about the power supply.  I'll try to contact silicon dust, but, you are right, it's probably a long shot.

Not sure what else to do.

---

### Post by davidstoll on 2011-04-24
Thanks for the suggestion.

I tried it, but it didn't make a difference.

But it was working before, so I'm not sure what would have changed.



> **LowSky said:**
> [http://www.silicondust.com/support/hdhomerun/downloads/linux/](http://www.silicondust.com/support/hdhomerun/downloads/linux/)

maybe install the drivers a from source?

---

### Post by r50880 on 2011-04-26
I'd try replacing the power supply for the HDHomeRun.  They are notorious for failing.  I just had mine fail on me today.  Actually, this is my second power supply.  The first was voluntarily recalled and replaced by SiliconDust.  It was the replacement that failed.  It failed slowly.  Initially, I just had trouble tuning a single channel.  It had exactly the low signal symptoms you describe, despite having 100% signal strength.  Then the rest of the channels followed.  Then finally it wouldn't tune anything at all.  Luckily I still had my old power supply laying around, so I swapped it out and now it works perfectly.

---

### Post by davidstoll on 2011-04-26
Here is silicon dust's response...

```
The symptoms aren't consistent with a power supply issue. The logs showed over 60000 network packets lost in the first hour. This level of packet loss on a wired ethernet network is almost always some sort of hardware failure: bad cable (ruled out), network not connected at full speed (PC reporting 1000, HDHomeRun reporting 100, this is exactly what it should be, so ruled out), bad switch port (ruled out), bad switch (next to test), or a bad NIC.
```


> **r50880 said:**
> I'd try replacing the power supply for the HDHomeRun.  They are notorious for failing.  I just had mine fail on me today.  Actually, this is my second power supply.  The first was voluntarily recalled and replaced by SiliconDust.  It was the replacement that failed.  It failed slowly.  Initially, I just had trouble tuning a single channel.  It had exactly the low signal symptoms you describe, despite having 100% signal strength.  Then the rest of the channels followed.  Then finally it wouldn't tune anything at all.  Luckily I still had my old power supply laying around, so I swapped it out and now it works perfectly.

---

### Post by BrandonXavier on 2011-04-27
I wouldn't rule out the possibility of network issues yet.  Here's a few more suggestions of things to check out:

[LIST=1] 
[*] If possible check port stats on your switch. You may be getting errors on one or more ports that aren't easy to see from the computer side (see below). Note: most consumer/SOHO switches won't have this capability, so don't spend a great deal of time looking for it if it isn't readily available.
[*] When doing your ping tests try varying the packet sizes with the "-s" option.  Good values to try are 512 and 1500.  Also, ping a device on your LAN - preferably the HomeRun device.  Pinging an internet address isn't really the best way to find errors on the LAN side. 
[*] If your NIC is doing onboard checksumming you probably won't be seeing the errors from your computer even though they're still occurring. If you suspect this is the case, try disabling it thru some modprobe options (varies by NIC/driver).
[/LIST]

Hope this helps.

BX

---

### Post by davidstoll on 2011-04-29
I did more random fiddling with the switch...changing cables, ports, rebooting the switch...and then it seemed fine for about 1 day, but returned to it's bad behavior.  I only see issues with the HDHomeRun.  There are probably other issues, but normal pc use doesn't show them.

So, I replaced the router last night, and once again, everything seemed fine.  I basically had two of the same switch.  One was in a different part of the house.  So, I just swapped them.  I'll see how it goes.  If the switch has minor issues, but doesn't affect the devices it's plugged into, I might be able to run that way for a while, but it's looking like it will need to be replaced.

I guess time will tell.

I'll try to report back if I come to a definitive answer so the thread has a resolution, but thank you everyone for your kind help and suggestions!




> **BrandonXavier said:**
> I wouldn't rule out the possibility of network issues yet.  Here's a few more suggestions of things to check out:

[LIST=1] 
[*] If possible check port stats on your switch. You may be getting errors on one or more ports that aren't easy to see from the computer side (see below). Note: most consumer/SOHO switches won't have this capability, so don't spend a great deal of time looking for it if it isn't readily available.
[*] When doing your ping tests try varying the packet sizes with the "-s" option.  Good values to try are 512 and 1500.  Also, ping a device on your LAN - preferably the HomeRun device.  Pinging an internet address isn't really the best way to find errors on the LAN side. 
[*] If your NIC is doing onboard checksumming you probably won't be seeing the errors from your computer even though they're still occurring. If you suspect this is the case, try disabling it thru some modprobe options (varies by NIC/driver).
[/LIST]

Hope this helps.

BX

---

### Post by davidstoll on 2011-05-04
The problem switch was RMA'ed.

The lost packets were not obvious when I moved it to an area in my network with computers that did basic web browsing or Internet file serving.  I guess because the internet connection is so much slower so retrys are (relatively) fast enough to keep up.

It was only apparent with time sensitive transmissions...i.e. Live OTA TV (Hauppauge HDHomeRun), VoIP, etc.

:/

---

