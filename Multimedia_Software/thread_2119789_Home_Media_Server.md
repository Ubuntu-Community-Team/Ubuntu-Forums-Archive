---
title: "Home Media Server"
date: 2013-02-24
forum: Multimedia Software
---

### Post by chrisguk on 2013-02-24
Hi,

Firstly I am not sure if this is the right area to post this question so I apologise in advance.

For the past two weeks I have been pulling my hair out trying to setup my own media server.  The hardware side is no issue, thats all setup and working fine.

My issue is software.  I have tried the following:

Ubuntu Server with the following:
Ushare - UPnP
Mediatomb - UPnP/DNLA
XBMC
Plex

FreeNAS with DNLA and UPnP and Mediatomb

The problem I am having is the playing of different movie formats.  For example I have some that are *.avi and some that are *.mp4.  I have tried transcoding with scripts etc and nothing seems to work.

Does anyone out there have good experience in this area and a system that works full proof for them.  Unfortunately I have no friends that have any experience in this area.

Oh by the way I want to play the movies from my wireless Media center a Pinnacle Show Center 250HD and a D-Link DSM-320.

---

### Post by chrisguk on 2013-02-26
Anyone?  Bump ;)

---

### Post by tgalati4 on 2013-02-26
Please post a detailed set of experiences that you have with each solution:  Ubuntu server with media services and Freenas with media services.

I have both set up, but other than the bandwidth limit of wireless routers, they both seem to work fine.  You can't expect High Definition through Wireless-G networks, nor can you get more than one video stream through the network when someone else is using netflicks, hulu, or other streaming service.  The bandwidth just isn't there.

avi and mp4 may have some some encryption issues depending on where they originated from and where you are trying to play them.  Try playing one problematic file locally (not through the network) using VLC and open the message/information console and post some of the video codec information or error messages.  There are lots of debugging tools for video streaming, but you have to provide us with some information.

---

### Post by chrisguk on 2013-02-26
Hi there,

Thank you for your reply.

Okay this is my setup:

First of all nothing is wireless, everything is on a wired connection.

SETUP:

NAS - Running FreeNAS - Supermicro Workstation 2 x Dual Core Opteron CPU 8GB RAM 2 xNICs

DNS/Gateway Server - Running Ubuntu Server 12.04 HP Proliant DL365 2 x 2.4 Ghz Dual Core CPU 4GB RAM

24 Port Cisco Switch (All Gigabit LAN)

Pinnacle Media Player - Wired connection.

Prior to the setup above my first approach was to Install Ubuntu server on the NAS machine and attempt to run the following:

PLEX - kept hanging up and support could not solve the issue.

MEDIATOMB - Im still trying to stick with this one because its the only software that has nearly got me near to my goal.

SERVIIO - codec issues and kept freezing on the media player.

USHARE - standard Upnp not adequate for my setup.

Here is the media info form VLC Media player as requested.

--no Errors--
Stream 0

Type Video
Codec: H264 - MPEG-4 AVC (part 10) (avc1)
Resolution: 1280x720
Frame rate: 23.976023
Decoded format: Planar 4:2:0 YUV

Stream 1

Type: Audio
Codec: MPEG AAC Audio (mp4a)
Language: English
Channels: Stereo
Sample rate: 48000 Hz

So my question is, VLC on the PC plays this file with no issues, why cant I do the same in Mediatomb.  If you need anymore then feel free to reply or add me to skype.

---

### Post by tgalati4 on 2013-02-26
Try streaming with VLC:

[https://www.socallinuxexpo.org/scale11x/presentations/videolan-vlc-overview](https://www.socallinuxexpo.org/scale11x/presentations/videolan-vlc-overview)

It's the most robust codec handler.  I use mediatomb for music only.  There are mediatomb forums, so I would do some searching there for codec/video streaming issues.

---

### Post by chrisguk on 2013-02-27
> **tgalati4 said:**
> Try streaming with VLC:

[https://www.socallinuxexpo.org/scale11x/presentations/videolan-vlc-overview](https://www.socallinuxexpo.org/scale11x/presentations/videolan-vlc-overview)

It's the most robust codec handler.  I use mediatomb for music only.  There are mediatomb forums, so I would do some searching there for codec/video streaming issues.

Just out of interest what do you use for Video media?

---

### Post by tgalati4 on 2013-02-27
I don't stream video at home, since my network is now saturated with netflicks, wireless phones, laptops, desktops, etc.  So, now I just use my freenas server with dedicated (fstab-mounted) shares on my devices and I copy video for local video.  There's just too many network variables that disrupt video on my home network, without using Quality-of-Service (QoS).  Setting up QoS requires replacing some of my existing routers and using open source firmware replacements and configuring QoS.  That will probably happen next year.  So for now, I just use dedicated mounts and move/copy videos over that I want to watch on local devices.

VLC provides a robust video streaming solution, but you must set up the streams remotely or write some scripts to do it.

There have been significant improvements in mythTV and linHES and LinuxMCE.  I have not used these in the past 2 years, but it's tempting to set up a system and try all of the new features.

Some links:

[http://linhes.org/](http://linhes.org/)

[http://linuxmce.com/](http://linuxmce.com/)

---

### Post by chrisguk on 2013-02-27
I just took a look at those distros.  The look interesting.

Its funny but I just finished putting VLC together to work with Mediatomb.  Seems to work pretty nice and it transcodes on the as it supposed to.  Something I did notice though is a slight degradation of the quality.  Not sure how to change this setting.  And at the start of any give movie the screen kind of stutters.  

I wrote the necessary script to go with it and that seems to operate as I expected.

On a side note, I probably have enough hardware and a network setup that would suite a medium size business.  People say why the hell do you have all that.  My answer - I just love technology and this is my big toy ;)

---

### Post by tgalati4 on 2013-03-02
There are a lot of ways to set up multimedia under linux.  None of them are easy, nor is the quality great, but with some work, you can find a workable solution.  Transcoding will always cause degradation of image quality.  You may not notice it on a 10" tablet, but you will notice it on an 8-foot projection screen.  The screen stuttering can sometimes be reduced by increasing the buffer size in both mediatomb and vlc.  You will have to do some digging to find the settings.  You will have a greater start up delay, but hopefully less stuttering.  Again, it's not perfect, but workable.

As far as overall video quality, there are endless discussions on the merits of each type of video codec.  If you are ripping DVD movies, then each movie will have optimum settings:  Black-and-White (Das Boot), action, drama, etc.  You will have to experiment or read the Home Theater/AV forums where this stuff is dicussed endlessly.

---

### Post by chrisguk on 2013-03-02
So that brings me to a new question then.

Do I go for a Windows installation instead?

---

### Post by tgalati4 on 2013-03-02
I haven't used Windows since Win98.  So I don't know what is available for streaming under Windows.  But let us know what works for you.

---

### Post by chrisguk on 2013-03-03
You have the same issue as me, I'm not a windows user either ;)

---

