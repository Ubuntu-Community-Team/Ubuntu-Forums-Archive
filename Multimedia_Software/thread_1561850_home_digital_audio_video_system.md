---
title: "home digital audio video system"
date: 2010-08-26
forum: Multimedia Software
---

### Post by cnbiz850 on 2010-08-26
This was a follow up to [this]("http://ubuntuforums.org/showthread.php?t=1552695") thread, since the topic deviates somewhat from that, so I would like to start a new one.

===============
Here I'd like to describe my system in some more detail, just to share knowledge and more importantly seek suggestions and critics.

I have a 4-year old Dell Inspiron 6400 laptop with Core 2 Due and 1GB RAM running Ubuntu 10.04. I tried using a good USB sound card connecting through the RCA connectors to the hifi amplifier and the sound quality was great except for the AC noise, which is not acceptable. The amplifier is branded Rogers and the stereo speakers are Sonus Farber by the way and I don't have home theater surround sound system. Someone said connecting via optical would remove the noise. The USB card has an optical outlet but unfortunately my hifi amplifier doesn't, so I haven't tried that. The laptop doesn't have HDMI, so I tried to connect via VGA cable to my HDTV, which is a Hitachi plasma 1080i TV. And as expected, the video is totally not acceptable. The TV, amplifier and speakers are all located together in the living room downstairs.

So then I found this 10moons DMP581 media player [(thread)]("http://ubuntuforums.org/showthread.php?t=1533563") running a Linux distro called Venus (somewhere after telnet saying BusyBox). It has HDMI, USB, RCA, optical, Ethernet outlets. It's pretty neat with a size of about 10cm by 10cm and 4cm in thickness. So I connect HDMI to the TV, RCA to the amplifier and Ethernet to a Netgear wireless router (serving as an access point). You control it with a supplied remote and have choices of playing music, pictures, movie, net radio, or browsing online. You also have a choice of your media source as from internal disk (which is not included but you can install one yourself - which I have not), USB, or network. On network, it can access Samba shared media. It accepts a wide variety of media formats. On the quality of the playout, it's totally over my expectation. Flac files coming out of the stereo are superb - no more need for a high quality CD player. Playing 1080p video files just tells me that I had been wasting my TV for the last couple of years playing SDTV via settop boxes and DVD players.

With that, then I moved the laptop to my office upstairs and connected it by wire to the main wireless router (a same Netgear model) which connects to the broadband. So I use it as a server, connected via USB to a 1TB disk, which I share via Samba.

Now the server and the media player are both connected by wire to two separate routers, which are then connected by wireless. Playing audio files and STD video files are OK. I did notice problems playing HD video across the network. So when playing HD video, I generally use a USB disk to move the media.

Two shortcomings I found:

1) the media player basically has no playlist feature. It just plays files in a directory one by one until the end, then either stops or repeats from the beginning if set so. So to play more music, you have to go select another directory (with the remote) manually when the previous finished.

2) the media player only accepts mms streams for net radio, NO http. So many good radios on shoutcast for instance can not be listened there.

---

### Post by charcaroth on 2010-08-27
>>
>>What would you say about the advantages/disadvantages of it over disks USB'ed to a server?
>>

My QNAP TS-239 is very responsive over the network, but has a slight lag when devices are connected via USB to the device compared to the internal RAID-1 array due to speed limitations of the USB 2.0 bus vs. the SATA one.  I'd feel comfortable expanding my media server/NAS in this way if I needed to add more volumes, especially temporarily.  I guess the issue you'll be facing when connecting is how well the "server" deals with the USB drives.  In effect, is the server close to fast enough over USB instead of an internal disk drive or array of drives?  I would bet the answer is "no" but that's really a question only you can answer.  The speed decrease in accessing media might just be worth not having to re-install the setup on another box, especially if you don't have one available.  I'd also be concerned about the amount of RAM on the server.  1 gb is probably enough (it's double what my NAS has), but if other processes are running on the machine (I'd try shutting down as many functions as possible) it could slow down the server access time as well.  Another possibility is that you could get a device that would let you connect your 1 TB USB hard drive to the network as a NAS, which could potentially have faster response than connecting to the USB port, but a quick review of those devices seem to indicate re-formats of the storage  drive (and to FAT32 which eliminates file storage over 4 gb) and connectivity issues when the drive goes into a power down state.  

In any case, I foresee latency issues across the wireless bridge that'll be hard to overcome, especially when streaming video.  Even standard definition streams lag in my experience. I just haven't seen wireless video streaming work well using any equipment.  Maybe with the coming of 60 ghz Wi-Gig networking it would be better, but even that's line of sight and wouldn't help in your situation.  I'd run a long CAT6A cable into the attic and snake it into the wall if it all possible.

---

