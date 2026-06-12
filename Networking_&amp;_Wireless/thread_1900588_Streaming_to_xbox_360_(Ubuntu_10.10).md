---
title: "Streaming to xbox 360 (Ubuntu 10.10)"
date: 2011-12-26
forum: Networking &amp; Wireless
---

### Post by -RYknow on 2011-12-26
Hey guys. I was hoping I could setup my Linux box to stream to my 360. I was following [this]("http://ubuntuforums.org/showthread.php?t=1768917&highlight=stream+to+xbox") guide. After going through the instructions, I'm not seeing any of the shared content. 

Can anyone tell me what the best method is to stream music, tv, and movies to my 360 from my linux rig?

Thanks, 
-RYknow

---

### Post by inobe on 2011-12-26
i don't know about ushare, mediatomb streams to ps3, i think it will for xbox, or anything with UPNP capabilities.

just search youtube for mediatomb xbox360, lots of video howto's in there.

---

### Post by SirWeazel on 2011-12-26
mediatomb doesn't support xbox360 according to their site. My vote is for minidlna... Simple,light. Cinfigure it with simple text file.  Might seem complicated at first, but isn't too tough and is easy once you realize what your doing. It also supports multiple directories/mnt points too. I found some easy walkthrus but I'm out of town posting from my phone, otherwise I'd provide a link. But just google it and I'm sure you'll find it.

---

### Post by syerges on 2011-12-31
Microsoft Updated XBox to only allow sharing through Windows Media Player 11 which can only be installed on Windows and currently isn't working through Wine. So far Microsoft strkes again!

---

### Post by SirWeazel on 2012-01-01
> **syerges said:**
> Microsoft Updated XBox to only allow sharing through Windows Media Player 11 which can only be installed on Windows and currently isn't working through Wine. So far Microsoft strkes again!

Syerges, this is incorrect. My xbox is fully updated, and your post made me double check. So as of 01/01/2012 I am able to stream to my xbox360 using minidlna without a problem.

Microsoft did implement a non-standard/slightly different dlna/UPnP system, and from my understanding that is why mediatomb doesn't support the xbox. What makes the xbox different i'm not sure.

---

### Post by syerges on 2012-01-03
I stand corrected! Thank Goodness!

> **SirWeazel said:**
> Syerges, this is incorrect. My xbox is fully updated, and your post made me double check. So as of 01/01/2012 I am able to stream to my xbox360 using minidlna without a problem.

Microsoft did implement a non-standard/slightly different dlna/UPnP system, and from my understanding that is why mediatomb doesn't support the xbox. What makes the xbox different i'm not sure.

---

### Post by Fraoch on 2012-01-03
Sorry to differ with everybody but you may want to try [Serviio]("http://www.serviio.org/").  Honestly I'm not sure why Ubuntu users don't mention it more often - it doesn't need to be installed as it's a standalone Java app, administration can be performed on the host machine or any other on the network, but more importantly it supports transcoding.

Transcoding converts one media format to another, and it's done on-the-fly, so the client machine doesn't even know that the media is in a format it can't play and no duplicate files are required.

Serviio has customized profiles for a range of devices including the Xbox 360.  I also use it with my Samsung "C"-series TV as well as a WD TV Live.  Serviio uses a different profile for each, I don't have to do anything other than specify a profile for each device.  The profile definitions have the appropriate transcoding options specified for each device.

This means I can play flac files on my Xbox 360 because Serviio transcodes them to MP3.  This is all in the background, I don't have to do anything.  Just follow [this]("http://ubuntuforums.org/showthread.php?t=1117283") first.  Serviio will also transcode .mkv videos to a format the Xbox 360 can play, although I haven't verified this yet.

I guess Ubuntu users are wary of it because it's free but not "free" as in open-source.

---

### Post by skrite on 2012-01-21
THis looks cool, but how do you get the Xbox to see it?

---

### Post by Derek Karpinski on 2012-01-21
> **Fraoch said:**
> Sorry to differ with everybody but you may want to try [Serviio]("http://www.serviio.org/").  Honestly I'm not sure why Ubuntu users don't mention it more often - it doesn't need to be installed as it's a standalone Java app, administration can be performed on the host machine or any other on the network, but more importantly it supports transcoding.

Transcoding converts one media format to another, and it's done on-the-fly, so the client machine doesn't even know that the media is in a format it can't play and no duplicate files are required.

Serviio has customized profiles for a range of devices including the Xbox 360.  I also use it with my Samsung "C"-series TV as well as a WD TV Live.  Serviio uses a different profile for each, I don't have to do anything other than specify a profile for each device.  The profile definitions have the appropriate transcoding options specified for each device.

This means I can play flac files on my Xbox 360 because Serviio transcodes them to MP3.  This is all in the background, I don't have to do anything.  Just follow [this]("http://ubuntuforums.org/showthread.php?t=1117283") first.  Serviio will also transcode .mkv videos to a format the Xbox 360 can play, although I haven't verified this yet.

I guess Ubuntu users are wary of it because it's free but not "free" as in open-source.

Serviio is great, it's just way too heavy.  As are most java apps.  Unless I had a dedicated media server, I'd stay away.

All that being said, since the XBox360 update forced out by MS, I haven't been able to see my computer on the XBox.

Instead of Serviio, I'm using Logitech Media Server.  For one, because I have a squeezebox, but it will serve dlna to compatible devices.  My samsung TV sees my media folders perfectly.

---

### Post by syerges on 2012-05-06
I didn't mess with anything but ushare and ufw.
Mine only works on both XBox 360 and playstation 3 with the following settings exactly...if i change any of them, then it stops working.
USHARE_OVERRIDE_ICONV_ERR=yes
USHARE_ENABLE_WEB=yes
USHARE_ENABLE_TELNET=no
USHARE_ENABLE_XBOX=yes
USHARE_ENABLE_DLNA=no


The enable_dlna really messed me up because it says ps3 won't work without it, but it's wrong. also make sure to look up your xbox and ps3 ip addresses and open up the port to them from your pc.

My computer's IP address was found by right clicking on my internet connection and then clicking on "connection information" and it is 192.168.0.11

My Xbox and PS3's IP addresses were found by going to network settings, they are 192.168.0.10 and 192.168.0.13 so I had to use the following codes in terminal. sorry, don't know how to do that code thing here....

I used the same port as you so you shouldn't have to change that number.

sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.10 port 49153
sudo ufw allow proto tcp from 192.168.0.11 to 192.168.0.13 port 49153

---

### Post by bluedevil678 on 2013-01-21
I have used Ushare and it worked great and was easy to setup. Looking for an ARM Debian based Upnp server for my Raspberry Pi. Will try MediaTomb and get back with the results.):P

---

