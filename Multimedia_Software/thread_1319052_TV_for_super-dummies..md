---
title: "TV for super-dummies."
date: 2009-11-08
forum: Multimedia Software
---

### Post by 1clue on 2009-11-08
Hi,

I'm a TV/webcam novice, to the point I haven't even started to read about it until recently.

I got a web cam, and an HDHomeRun.  I dove into the HOWTO here.

I got the webcam working except that the part which automatically tracks me with the camera doesn't work.  I'm fine with that, unless somebody knows the problem.  That's not what I'm emailing about.

I want to watch TV.  I would like to do so in 2 modes:  First, as full screen, as though it were a real TV.  Second, I want to get a signal in a window that I can watch while doing something else.

MythTV is probably wonderful for those of you who want 14 different tuners in your house and you want precise control over which ones get what channels, and other options I have never imagined before.  I've messed with this damn thing for hours now and I can't get the @#$%@#^ TV to work.

I'm willing to work through documentation if I know it's going to get me where I want to go.  MythTV looks like it wants to be an entertainment center and nothing else, meaning I can't work while watching TV.  It looks to want extreme control over everything.  I don't, I just want the TV to work.  I want to be able to press up/down arrows to cycle channels, or type in a channel, and MAYBE record.

Is it true that you have to record something before you can watch it?  There are settings which seem to talk about "live TV" but no matter what, I try to watch TV and it complains that there are no recordings.

I'm totally lost.  Please help.

Thank you.

---

### Post by marc.verwerft on 2009-11-08
> **1clue said:**
> Hi,

I'm a TV/webcam novice, to the point I haven't even started to read about it until recently.
...
 I want to be able to press up/down arrows to cycle channels, or type in a channel, and MAYBE record.
...
I'm totally lost.  Please help.

Thank you.

I think you want something like tvtime before you switch to mythtv.

---

### Post by xc3RnbFO8P on 2009-11-08
You can use VLC.

---

### Post by 1clue on 2009-11-08
I'll look closer at these.  I tried VLC, but didn't figure out how to hook it to the hdhomerun server yet.

Haven't heard about this other one yet.

I don't mean to disrespect mythtv, there is definitely a place for it.  It's just not what I want.

Thanks.

---

### Post by zenkaon on 2009-11-08
I highly recommend tvtime. It's very very good. 

I've played with most tv apps for linux and some for windows and I have to say that if you just want to watch tv or play a Wii then it's great.

Are you sure you have you TV card setup correctly?? open a terminal and type:
```

dmesg | less     (this pipes the output into less - a useful tool for looking at files)
/bttv     (this searches less for bttv)

```

scroll through (Page Down or down arrow) and look for bttv, does it give any errors? 

Could you copy and paste the output surrounding bttv. q will exit less

---

### Post by MountainX on 2009-11-08
I've been messing with TV lately. The easiest solution I found was to install openSUSE 11.2 KDE. Kaffeine comes with it and I was watching TV in no time.

The next easiest solution I have used is SageTV for Linux. It costs $79, but it includes a free US/Canadian program guide. The same thing for MythTV costs $20/year, so after a while the cost is probably about the same.

I have both Kaffeine and SageTV working right now. 

I just watched the season-ending MotoGP race on my TV using a MediaMVP frontend and SageTV running on a Ubuntu server in my garage. It worked great. I can watch SageTV recordings on any TV anywhere in my house, or I can watch on the computer (and my wife can watch on her Windows computer).

I've also been trying to install Mythbuntu, but I can't get it working. The other two choices are much easier. MythTV is probably the most powerful, but SageTV does a lot of the same things with a lot less setup skill. One of these days I hope to get MythTV working just because I like a challenge.

---

### Post by 1clue on 2009-11-08
> **zenkaon said:**
> I highly recommend tvtime. It's very very good. 

I've played with most tv apps for linux and some for windows and I have to say that if you just want to watch tv or play a Wii then it's great.

Are you sure you have you TV card setup correctly?? open a terminal and type:
```

dmesg | less     (this pipes the output into less - a useful tool for looking at files)
/bttv     (this searches less for bttv)

```

scroll through (Page Down or down arrow) and look for bttv, does it give any errors? 

Could you copy and paste the output surrounding bttv. q will exit less

hdhomerun is an external network-based dual TV tuner.  You hook it up to cable and then (somehow) log in to it from any computer on the network.  So I don't think there's a local device, unless I were to configure one somehow.

Maybe that's what is missing?

---

### Post by MountainX on 2009-11-08
> **1clue said:**
> hdhomerun is an external network-based dual TV tuner.  You hook it up to cable and then (somehow) log in to it from any computer on the network.  So I don't think there's a local device, unless I were to configure one somehow.

Maybe that's what is missing?

I didn't read the part about you having an hdhomerun. That is a cool device!

It should work with SageTV. Check this:
[http://www.silicondust.com/hdhomerun/instructions/sagetv](http://www.silicondust.com/hdhomerun/instructions/sagetv)
Even though the instructions are for Windows, SageTV runs on Linux. The Linux client is the Placeshifter, so it is different from the Win client. But SageTV might work for you. Only problem is that there is not a trial...

I read through the hdhomerun setup instructions for SageTV and I have all those options available to me with my setup which is SageTV server running on Linux. I use a MediaMVP frontend connected to my TV. I don't use Windows. So maybe SageTV will work for you. Ask on their forums (sage.tv).

The other thing you might want to look into is using just the MythTV frontend... that might be a lot simpler (but I can't say for sure because I've never done it).

Bottom line: you need a compatible software application. Looks like this is the list:
[http://www.silicondust.com/hdhomerun/instructions](http://www.silicondust.com/hdhomerun/instructions)

---

### Post by 1clue on 2009-11-09
Darn it.

It's 32-bit only.  I'm runnig 64-bit.

BTW, I evidently missed a couple posts in there.

I also have no problems paying for commercial software, but I would rather buy the license outright than deal with a monthly fee.  My income is based off of copyright law, so I'm generally pretty fussy about following those rules.  :)

If nothing else, I have a couple more things to try out.

I wonder, do you need to create a sort of localized network device for the HDHomeRun?  Am I missing things here?  The company web site linked to by the device is a bit scattered, they seem to make assumptions about my video knowledge which I have no idea about.

Thanks.

---

### Post by MountainX on 2009-11-09
> **1clue said:**
> Darn it.

It's 32-bit only.  I'm runnig 64-bit.


Yes, I prefer 64bit, but for TV stuff, 32 bit is fine. I switched to 32-bit Linux on the computer running the SageTV server. It's no big deal. It works fine.

---

### Post by 1clue on 2009-11-09
Maybe I'll install a VMware with 32-bit or something.

There's no way I'm going back to a 32-bit OS.  FWIW, I don't think I could even access all my RAM.

---

### Post by seeker5528 on 2009-11-09
> **1clue said:**
> 
I wonder, do you need to create a sort of localized network device for the HDHomeRun?  Am I missing things here?  The company web site linked to by the device is a bit scattered, they seem to make assumptions about my video knowledge which I have no idea about.

Myth TV has the support built in to recoginze and control the HDHomerun. 

If you don't use Myth TV, then you need the config utilities and a player that can connect to the UDP stream, the instructions are here:

[http://www.silicondust.com/forum/viewtopic.php?t=1924](http://www.silicondust.com/forum/viewtopic.php?t=1924)

: there is a config package installable from the Ubuntu repositories, but to get the GUI stuff, it looks like you have to download the stuff from Silicondust and compile it.

Later, Seeker

---

### Post by 1clue on 2009-11-09
I already have the GUI config compiled from silicondust.  I used Xnest to make mythtv in a small window, but there the problem is you can't resize it.

If I could get VLC going that would be awesome.  That's about what I was thinking in terms of an app interface, I just can't seem to get it to connect on any port that's open on the homerun.

---

### Post by seeker5528 on 2009-11-11
I haven't tried connecting that way with VLC myself, but if the config utility is connecting and the lights on the HDHomerun indicate a tuner is active, then the list of things they give you to check are pretty short:

- Check that VLC is running and is using "udp://@" or "udp://@:1234".
- Check the IP address of the machine VLC is running on.
- Check that the port is not blocked by a firewall. 

The Myth TV frontend has an option to run windowed instead of fullscreen, but I can't say off the top of my head if that window is re-sizable or if you are limited to the size you have selected in the Mythfrontend, I'm kinda thinkin' it's the latter. I only run MythTV windowed to make it easier to switch between applications and desktops, at that was mostly because of inconsistencies between different desktops and window managers about what key combinations you can use and when you can use them to switch to another desktop.

Later, Seeker

---

### Post by 1clue on 2009-11-11
vlc udp://192.168.1.100
VLC media player 1.0.2 Goldeneye
[0x853c28] main interface error: no interface module matched "globalhotkeys,none"
[0x853c28] main interface error: no suitable interface module
[0x757888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x757888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x86c6e8] main stream error: cannot pre fill buffer


Pretty much shows up like that no matter what port I hook it to.

---

### Post by seeker5528 on 2009-11-12
I downloaded the config gui and installed on my Debian installation.

The way it works for me is......

Do a scan.
Find a channel with something on it.
Click the view button
VLC opens automatically and says it is connected to:

udp://127.0.0.1:5000

I think that is the only way it will work using the GUI.

If you look at the instructions for doing it all from the command line, you have to use the config utility to set the HDHomerun to the channel and multiplex on the tuner you want to use view, then start VLC, then use the config utility to tell the HDHomerun where to send the video stream from that tuner.

In the GUI utility there is no way to tell the HDHomerun where to send the video, it automatically starts VLC and tells the HDHomerun where to send the stream when you click on view.

Later, Seeker

---

### Post by 1clue on 2009-11-12
Interesting.

I put in 65, and US-cable.  I happen to be watching that on Comcast.

The view button is disabled.  I don't know what that means, but it probably means I'm not configured correctly or that I have a missing component.

---

### Post by xc3RnbFO8P on 2009-11-12
[http://www.silicondust.com/hdhomerun/hdhomerun_tech.pdf]("http://www.silicondust.com/hdhomerun/hdhomerun_tech.pdf")

> VideoLAN VLC:
VideoLAN VLC is a 3rd party client suitable for playing multicast video from the HDHomeRun TECH.
      Run VLC and select Media, Open Network.
   &#8226;
      Set the protocol to RTP.
   &#8226;
      Set the address to 239.255.1.1 and the port to 59001.
   &#8226;
      Click play.
   &#8226;

Maybe you have to change this:
tools> perferences> input & codecs:  use rtp over rtsp (tcp)

---

### Post by seeker5528 on 2009-11-12
The channels on the tuner do not have any relationship to the channels on the TV or cable box, each channel can have a dozen streams, possibly more depending on the content, any stream on any channel can be mapped to any number channel on the cable box.

In the earlier part of the FAQ they give you instruction for setting the channel map and then dumping a list of channels.

I think the command line utility also an option to download a list of channels for your area from a server at Silicondust to match up to the channels that are detected in the scan and I think this is optionally updated in the HDHomerun.

Not sure what the GUI does, I do have a number of things that show up with text that matches up to the station ID of the local affiliate for the major networks and network id of other stations, mostly the same as the IDs you see if you go online to view the TV listings at Comcast or Zap2it, but there are also channels that do not have that information. In my case this information could be there from using the utilities provided in Windows. Some of the stations, at least in my area, are radio stations.

Later, Seeker

---

