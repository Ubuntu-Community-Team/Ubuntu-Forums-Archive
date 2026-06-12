---
title: "rtorrent clogging network"
date: 2010-12-01
forum: Networking &amp; Wireless
---

### Post by shawn.abdushakur on 2010-12-01
Hi,

I'm in need of some help if someone has some time to spare. I've had this problem for some time and can't seem to shake it. I've been through various versions of Ubuntu and also Debian Lenny.

What's happening is that when I run rtorrent, my network connection seems to get 'clogged up' on my server (which is where rtorrent is running). If I try to SSH into the server while rtorrent is running, it takes forever to get in, like several minutes. Also, I mount some directories from the file server, via NFS, into XBMC so that I can watch videos and the same thing happens; the files are constantly buffering and sometimes just totally freezes XBMC. 

Simply stopping rtorrent doesn't solve the problem; I have to restart networking also. The computer that acts as the file server is a bit old if that offers any clues.

Any help would be appreciated. Please let me know what to do or where to start. I'm at a loss. Thanks.

Shawn

---

### Post by shawn.abdushakur on 2010-12-06
bump

---

### Post by inobe on 2010-12-06
a torrent box with ssh ?, come on man, that's not very wise, check your logs.

---

### Post by shawn.abdushakur on 2010-12-07
I know it's not the best thing to do, but until some money comes to buy a new box, that's what I have. I've checked /var/log/messages; should I be checking somewhere else? Nothing appears there when this event happens. Also, when this happens memory is fine and the swap file isn't being used. Thanks.

---

### Post by Boondoklife on 2010-12-07
Your issue is prolly related to network traffic not memory or proc usage. Try to tune the number of open connection down and limit the number of active torrents. You may want to check your router to see if there is a ceiling on the number of open connections (might be hard to find). As a simple rule, I set 30 peers per torrent and only run 5 at the max at a time.

The machine I am running it on is a WD mybook (100Mhz ARM, 32MB RAM), unless your shorter on resources than I am, I doubt it is hardware. I have my router tuned to allow 1280 connections at a time and it is just an old WRT-54g hacked with DD-WRT firmware.

As a side note, what is wrong with ssh on a torrent box? I would assume you have not DMZ'd the box so what's the big deal? I have it on mine and have never had an issue. Then again I don't give the world access to ssh on that box and only have 1 valid user that can login with a pretty good password.

---

### Post by shawn.abdushakur on 2010-12-07
So, just to clarify, the tuning of open connections is done on the router? And if I can't do it there, and I suspect I can't (for two reasons; first, I'm pretty familiar with the router software and can't recall a place to do that, and second, I can't install DD-WRT on my router unfortunately), can it be done elsewhere (i.e., on the server)? Thanks.

---

### Post by Boondoklife on 2010-12-07
The tuning of the peer per torrent and max peers would be done in the torrent application. If rtorrent does not have that ability then try transmission as I know it does. The tuning of the max open connections would be done on the router, if available.

You best bet is to tweek the peers settings, limit torrents to 4 at a time, and also looking into if your router can do QoS. QoS will help to make sure torrents only consume background bandwidth; it makes sure your connection stays snappy while downloading.

---

### Post by shawn.abdushakur on 2010-12-09
OK, so I thought we had this problem licked, but not so. I've got rtorrent limited to 30 peers and 4 torrents upload/download. I can't limit the number of connections on my router, but I have setup QoS. I set rtorrent to a priority of one on the ports I specified in rtorrent's config file on TCP. I also set UDP to a priority of 7 with the IP Address set to that of my file server and no port specified as I don't know what port it's sending the data out from. 

An example of what's happening now: I loaded XBMC and the NFS shares wouldn't mount, rtorrent running on the server, so I ssh into the server, not much of a lag, and just reboot the server. Mounted the shares and proceeded to watch a video. About 20 minutes into the video it starts to buffer 2%...after a few minutes 3%...now I'm writing this.

Thanks for trying though. Any other suggestions? Also, concerning the logs, where should I look?

---

### Post by Boondoklife on 2010-12-10
If you do not start rtorrent the system works fine correct? If that is the case try to use transmission and see if you get the same results. 

As to your QoS rules, I'm not sure what your priorities mean. I can tell you in my case I just flag torrents and apps like it to bulk (in my case the lowest priority) and let almost everything else be at the normal priority.

Try transmission and see if it fixes it and let us know.

---

### Post by shawn.abdushakur on 2010-12-12
I was using transmission prior to rtorrent and the same was happening. I thought it was transmission so I searched for less resource intensive client and found rtorrent.

I have some new information though. It doesn't appear to be an rtorrent problem. I was transferring an ISO from the file server to a remote host and the same thing happened. I had to restart networking about 3/4 through the transfer as it got stuck and wouldn't transfer anymore. I tried to SSH in and couldn't; connection timed out, so I went down to restart from the server itself. After that, the transfer resumed and completed fine so it looks like something to do with networking, but I'm no specialist in networking. 

Thanks for the help.

---

### Post by Boondoklife on 2010-12-12
Look into trying to install iperf and using it to test your network. It sounds like your router may be the issue, if you have two computers then try to connect them together with a crossover and transfer some files. If the issue persists it could be a software issue or a NIC issue, the latter is easily tested with a usb network adapter.

---

### Post by shawn.abdushakur on 2010-12-17
I haven't had time to connect the two computers together, but here are the results of an iperf test:


shawn@NX7400:~$ iperf -c 192.168.0.100 -i 2
------------------------------------------------------------
Client connecting to 192.168.0.100, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.101 port 53129 connected with 192.168.0.100 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0- 2.0 sec  22.0 MBytes  92.4 Mbits/sec
[  3]  2.0- 4.0 sec  22.4 MBytes  93.9 Mbits/sec
[  3]  4.0- 6.0 sec  22.3 MBytes  93.6 Mbits/sec
[  3]  6.0- 8.0 sec  22.4 MBytes  94.0 Mbits/sec
[  3]  8.0-10.0 sec  22.4 MBytes  93.8 Mbits/sec
[  3]  0.0-10.0 sec    112 MBytes  93.5 Mbits/sec

and with UDP...


shawn@NX7400:~$ iperf -c 10.1.1.1 -u -b 10m
------------------------------------------------------------
Client connecting to 10.1.1.1, UDP port 5001
Sending 1470 byte datagrams
UDP buffer size:   122 KByte (default)
------------------------------------------------------------
[  3] local 192.168.0.101 port 54897 connected with 10.1.1.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  11.9 MBytes  10.0 Mbits/sec
[  3] Sent 8505 datagrams
[  3] WARNING: did not receive ack of last datagram after 10 tries.

I'll try to connect the two computers this weekend. Thanks again.

---

### Post by shawn.abdushakur on 2010-12-19
Another update:

I connected the server and a notebook via crossover cable and transferred about 10 gigs worth of files over and it was perfect, no choking, speed was around 10.5-11 MBps. So I took up your suggestion that it might be the router and went and bought a new Linksys WRT160N, but unfortunately the same problem exists. I started up rtorrent about 3 hours ago and as of now I can't SSH in; I get connection timed out. 

Also, I neglected to mention in the previous post that those iperf tests were done while the problem was happening (i.e., a very slow SSH login).

Thanks again.

---

### Post by Boondoklife on 2010-12-19
Are you doing this via wifi or wired into the router? If via wifi then try wired and see what happens. If that works find then I would try to setup an ad-hoc network and see if that runs better.

This will at least tell us if it might be related to wifi. In your case it my just be a wifi issue, but let me know.

On a side note, if you keep the router and it is not ver. 2, you can install DD-WRT on it. WRT160N ver. 2.0 is not supported.

---

### Post by shawn.abdushakur on 2010-12-19
Wired.

Ya, I was thinking about keeping it, but it's kinda hard to justify right now, though DD-WRT is a tempting reason.

---

### Post by Boondoklife on 2010-12-19
> **shawn.abdushakur said:**
> Wired.

Ya, I was thinking about keeping it, but it's kinda hard to justify right now, though DD-WRT is a tempting reason.

So if you plug both devices into the router, and then try to transfer the ISO it still freezes? This is very odd as if they worked via crossover and you have a new router then I am at a loss.

---

### Post by amsterdamharu on 2010-12-19
Did you set max upload and max download throttle? Both transmission and rtorrent will take up too much bandwidth (or any other torrent app).

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)
Look under throttling I think it's zxc and shift zxc (maybe in combination with control but I don't think so)

---

### Post by Boondoklife on 2010-12-19
> **amsterdamharu said:**
> Did you set max upload and max download throttle? Both transmission and rtorrent will take up too much bandwidth (or any other torrent app).

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)
Look under throttling I think it's zxc and shift zxc (maybe in combination with control but I don't think so)

This has ceased to be a torrent issue as he said the same thing happen without it running and just transfering an ISO file.

---

### Post by amsterdamharu on 2010-12-19
> This has ceased to be a torrent issue

How is that? I share a router with 3 room mates and am unable to load an internet page if their (uploads) are not limited.

> he said the same thing happen without it running and just transfering an ISO file

Ok, you got a point there but I still would say it doesn't hurt to squeeze some off the upload depending on your bandwidth I guess. For home users usually a 3M line means only a couple of K upload.

---

### Post by Boondoklife on 2010-12-19
Well since the problem is even internal traffic grinding to a halt, I would think limiting the WAN access would be mute.

---

### Post by shawn.abdushakur on 2010-12-19
> So if you plug both devices into the router, and then try to transfer the ISO it still freezes? This is very odd as if they worked via crossover and you have a new router then I am at a loss.

I kinda figured you would say that :). Hopefully somebody else can weigh in cause I'm at a loss too. Thanks for the help.

---

### Post by shawn.abdushakur on 2010-12-19
> **amsterdamharu said:**
> Did you set max upload and max download throttle? Both transmission and rtorrent will take up too much bandwidth (or any other torrent app).

[http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide](http://libtorrent.rakshasa.no/wiki/RTorrentUserGuide)
Look under throttling I think it's zxc and shift zxc (maybe in combination with control but I don't think so)
I have throttled both the download and upload.

---

### Post by Boondoklife on 2010-12-19
Just as a shot in the dark, have you tried different cables? you do get the same results via wifi correct?

I can not think of anything else to try other than booting a live CD on each computer and trying it that way. This would make sure it is not an OS/Software setting that is sabotaging you.

---

### Post by shawn.abdushakur on 2010-12-19
> **Boondoklife said:**
> Just as a shot in the dark, have you tried different cables? you do get the same results via wifi correct?

I can not think of anything else to try other than booting a live CD on each computer and trying it that way. This would make sure it is not an OS/Software setting that is sabotaging you.
Ya, I originally had a crossover cable connecting the server to the router so I just changed that yesterday. 

Live CD's would be too much trouble the way I'm thinking, but maybe I'm not thinking right. Briefly, how would suggest going about that?

---

### Post by shawn.abdushakur on 2010-12-19
Let's put this on hold til tomorrow. I tried to SSH earlier and got connection timed out so I restarted networking and stopped rtorrent which would normally solve the problem, at least temporarily, but I just tried to SSH in again and got the same; furthermore, I can't mount my NFS drives so I'm thinking something else is going on right now. It's late now, so I'm gonna continue tomorrow. Thanks again for the help. I'll let you know what happens tomorrow.

---

