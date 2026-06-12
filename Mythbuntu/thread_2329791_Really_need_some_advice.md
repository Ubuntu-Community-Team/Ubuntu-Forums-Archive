---
title: "Really need some advice"
date: 2016-07-05
forum: Mythbuntu
---

### Post by Espryon on 2016-07-05
So... I finished a preliminary Mythbuntu test machine i.e. my old old laptop i.e. CrapTop from years ago. It was working fine up until I started running out of room on the small harddrive. I was wondering if I read correctly. The NAS and/or portable harddrive(s) need to have the ability to mount correct, same file structure as /var/lib/mythtv, and finally the directory above it owned by root and the directories on the drive owned by the mythtv group?

My second question was about lowering the quality of the recordings. The avg size of recordings being an 30 mins to 1 hour long is 26 GB and while I appreciate it actually working. It's frustrating to have to delete and/or backup the files to a portable harddrive.

My third question is, is there a guide for ordering, naming, and preparing recordings for viewing on laptops, phones, ipads, etc?

My fourth question is, how do I enable the auto removing of commercials from the recordings?

My fifth question is, is there a way to repair the video damage from the phasing on the antenna i.e. the blurriness once in a while?

My last question is, do you have to use SchedulesDirect or is there a way to configure the backend to receive the hdhomerun tv tuner(s) free tv guide?

Thanks,

Espryon

My setup is an old laptop I.e. The backend , 2 raspberry pi's I.e. The front end, and a silicon dust dual US tv tuner.

---

### Post by TheFu on 2016-07-05
What I think I know.

2) HDHR just stores the stream as sent by the broadcaster. Transcode to make it smaller.
3) Use handbrake. There are presets for those, but I found that Plex Media server handles it for most devices.
4) comskip. Don't know how to do that in Myth.
5) No. Usually digital signals don't have any ghosting. The protocol prevents that. If there are issues, it is because the HW is too slow to save the recordings - I've seen this with slow HDDs.
6) Schedule data is very regional. The solution for N. Europe is different from Mexico and still different from the USA. Not all models of HDHR-US tuners have access to their guide data.

I use multiple HDHR3-US to record OTA ATSC broadcasts, but do not use MythTV. I think only the newer HDHR tuners with DLNA servers built-in support their guide data (I don't have one).

I record on 1 system, locate commercials, remove those, then transcode. Most recordings are about 11G/hr for HiDef, but become about 2G/hr after transcoding and commercial removal with ZERO loss of quality seen.  Comskip isn't perfect and is wrong often enough to require manual fixing before removing the commercials.  For SD video, sizes are much smaller - 2G/hr and less than 1G after removal of commercials and transcoding. h.264 doesn't compress SD as well as HD videos.

---

### Post by khPWXxF on 2016-07-05
[COLOR=#000000]Your first question:
"The NAS and/or portable harddrive(s) need to have the ability to mount correct, same file structure as /var/lib/mythtv, and finally the directory above it owned by root and the directories on the drive owned by the mythtv group?"
That sounds about right - I split my system at that point, but with internal disks.
You will need to edit /etc/fstab to tell ubuntu that it should look to your new drive to find /var/lib/mythtv.
Phil


[/COLOR]

---

### Post by Espryon on 2016-07-05
I lowered the quality and its still having issues weirdly enough with the ghosting. I'm wondering if its a network related thing i.e. having to go through multiple switches and maybe an ad-hoc situation and/or plugging it into a bridge mode router and/or its own switch would be better served for it. Not the antenna or laptop. I also found the model of my old laptop: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834246328](http://www.newegg.com/Product/Product.aspx?Item=N82E16834246328) It did reduce the space though i.e. 26 GB to 2 GB on avg per recording.

We have at my house like 4 switches, 3 routers, and hundreds of feet of cat5e inbetween the frontend and the backend and aforementioned equipment.

---

### Post by TheFu on 2016-07-05
On the raspberry pis ... did you purchase and install the mpeg2 codecs?  At hidef resolutions, the CPU can't handle mpeg2, but can easily handle h.264 (transcoded) media.

I have cheap switches, all GigE, through my home too. Has never been an issue for any networking. All my systems are GigE ethernet connected, except a Raspberry Pi v2 and the HDHR2 tuners. With a non-GigE "server", if the streams are h.264, even a solid 100 base-TX network should be fine for playback. But if recording 2 Hidef streams AND trying to play 1 as mpeg2, that would probably be more than the HDD could handle. With hiDef and mpeg2, it becomes more of a challenge, but honestly, I'm mostly worried about the laptop HDD - those tend to be slow.  Mine recording VM can record 1 hidef stream and 2 low-def streams without issues, but not 2 hidef streams.  When ATSCv3 becomes the standard, the required bitrates for recording will drop greatly - alas, that is 3+ yrs away and my HDHR tuners (and all existing TV tuners) will be useless then.

If there is an wifi, all this data can be thrown out.  Wifi can be great, but that seems to be the exception, not the rule.  For example, I just reworked my wifi-G network into a wifi-N (300Mpbs) network ... and all my N devices can only connect at 65Mbps regardless of the distance.  10- inches or 25 ft line-of-sight ... 65Mbps is the fastest connection possible which means more like 30Mbps real-world throughput.  Did a wifi deployment project for over 1200 location a few years ago. What that taught me was ... avoid wifi, always, unless there isn't **any** other possible solution.  Wifi might appear stable to humans, but the computers see the wildly varied bandwidth as interference and atmospheric conditions change. It is crazy how much it fluctuates.  Heck, even bad powerline is more stable than wifi - though powerline bandwidth marketing is even more full of lies than wifi marketing.  I have "600 Mbps" powerline which achieves only 60Mbps.  10% of the advertised bandwidth.  Even in the same room, I never saw more than 220Mbps with these 600Mbps devices. Makes politicians seem like truthful people in comparison. ;(

You can use iperf to see a best-case throughput between devices, but don't believe those results - always test by pushing real data between the 1 points on the network.

---

### Post by Espryon on 2016-07-05
Yes I did but, I ran into this [https://discourse.osmc.tv/t/livetv-mpeg2-from-over-the-air-ota-audio-stutter/8545](https://discourse.osmc.tv/t/livetv-mpeg2-from-over-the-air-ota-audio-stutter/8545) . The Dev(s) suggestions fixed the problem with the hdhomerun addon but, not with the live tv PVR recordings and/or live tv. I thought it was ^ with the aforementioned different modes but, the recordings on the server have the stutter too, its leading me to believe that it has something to do with network lag i.e. between the wireless router, silicondust hdhomerun receiver, backend, raspberry pi, switches, and router(s).

It wouldn't be surprising considering I couldn't get the NIC on the laptop to work i.e. its using the 802.11G/N wifi card in the laptop to communicate over the network.

---

### Post by TheFu on 2016-07-05
So your "server" is using wifi?  I cannot help you.

---

### Post by Espryon on 2016-07-05
I might be able to get the NIC to work. I downloaded drivers and installed them. I'm updating it now and I'm going to reboot in a bit and see if the drivers work.

(Edit) Got the NIC to work following this guide as I can't remember how to do this for some reason: [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

Looked up the NIC from the aforementioned link to where I purchased the laptop. It will be entertaining if this actually works while I build a real server. In the other post I made, I eventually came to the conclusion that the motherboard was defunct i.e. it turned on but, not much else worked. I will report back if it fixes stuttering issues.

Thanks </Insert name(s) here/> Mythbuntu people,

Espryon

picard@Stargazer:~/Desktop$ ifconfig
eth1      Link encap:Ethernet  HWaddr a1:b2:c3:d4:e5:f6  
          inet addr:192.168.2.61  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f2de:f1ff:fee4:8f48/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13760 errors:0 dropped:0 overruns:0 frame:0
          TX packets:416 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18506464 (18.5 MB)  TX bytes:49396 (49.3 KB)
          Interrupt:43 Base address:0x2000 

^ Woo!

---

### Post by Espryon on 2016-07-05
Was able to use my 2 TB drive by doing this.

I set . and .. to chown root:root 

I set the subdirectories also to chown mythtv:mythtv

I set all the subdirectories of mythtv to chmod 2775

Woo! 2TB of video recording. Now I just need to fix the web streaming service of mythtv.

---

