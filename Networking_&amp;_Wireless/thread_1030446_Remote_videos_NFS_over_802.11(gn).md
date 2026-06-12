---
title: "Remote videos NFS over 802.11(g/n)"
date: 2009-01-04
forum: Networking &amp; Wireless
---

### Post by jbernardo on 2009-01-04
Hi. I am going crazy with this. I have a mythbuntu setup, with a "silent" front-end (a advent DHE-500 pc) and a remote server. The server is sharing a movies directory, to which I ripped my children DVD, to try to make them last a little longer (ever seen a DVD on the hands of a 3yr old?).
The problem - either using 802.11g (ralink RT2500PCI adapter), connecting at 54Mbps or 802.11n (Marvell TopDog chipset linksys WUSB300N-EU) connecting at 144.5Mbps, I have video and audio problems. I have tried almost all NFS client parameters I could think of, using udp or tcp, increasing rsize to 65536 or decreasing it to 512, and the problem is always the same - either video hiccups, or audio sounding "metallic" and heavily distorted, when mplayer can't keep it synced.
I thought it might be a drive on my raid5 array giving problems, but it doesn't seem so:

```
$sudo hdparm -tT /dev/sda

/dev/sda:
 Timing cached reads:   1580 MB in  2.00 seconds = 790.35 MB/sec
 Timing buffered disk reads:  218 MB in  3.01 seconds =  72.49 MB/sec
$ sudo hdparm -tT /dev/sdb

/dev/sdb:
 Timing cached reads:   1304 MB in  2.00 seconds = 652.12 MB/sec
 Timing buffered disk reads:  186 MB in  3.02 seconds =  61.61 MB/sec
$ sudo hdparm -tT /dev/sdc

/dev/sdc:
 Timing cached reads:   938 MB in  1.99 seconds = 470.30 MB/sec
 Timing buffered disk reads:  232 MB in  3.00 seconds =  77.22 MB/sec
$ sudo hdparm -tT /dev/sdd

/dev/sdd:
 Timing cached reads:   1206 MB in  2.00 seconds = 603.04 MB/sec
 Timing buffered disk reads:  158 MB in  3.04 seconds =  51.89 MB/sec
$ sudo hdparm -tT /dev/md0

/dev/md0:
 Timing cached reads:   972 MB in  2.00 seconds = 486.18 MB/sec
 Timing buffered disk reads:  204 MB in  3.00 seconds =  67.95 MB/sec
```This should be enough for video streaming, right? Besides, when I connect a long ethernet cable between the machines, I have no video or audio problems, independent of the NFS mount settings, pointing the problem to some wifi related interaction.
Any idea?
Thanks!

---

### Post by oobe-feisty on 2009-02-22
forgive the late reply you may not be looking for help anymore the wusb300n is what i have attached to my backend the the remote frontend connects to a wireless-n router it works fine i tried wireless-n to wireless-n card and it would not work i think once 2 wifi devices connect to the lan it halfs the bandwidth

---

### Post by jbernardo on 2009-02-22
Thanks, but that isn't the problem. I have the backend connected to a netgear 802.11n router.
Bunto did help me work around it, setting up a mplayer cache, etc. But I still have to find why the NFS share over 802.11n is so slow and so affected by every little interference.

---

### Post by yeaitsdark on 2009-02-22
How is the server sharing media across the network? Samba?

Also I find different video clients are more "tolerant" of latency they'll buffer more data etc before even playing. Also, I notice that the file type and size has a lot to do with seamless video playing. One I like is VLC media player, it's really solid and supports .vob .mkv amongst other media types.

The read speeds you're getting from the array are more than sufficient for streaming video. As for the wireless my initial suggestion is to perhaps change the MTU or tweak some other options. Perhaps this article may assist you :[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9112462](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9112462)

---

### Post by jbernardo on 2009-02-22
The server is sharing over NFS... :)

I am running mythtv on the frontend, which uses both it's internal player and mplayer (can also configure other players).
The mplayer works well for most movies when I enable a large enough cache. For "high-def tv" quality movies made on my N96, it just hickups too much. The internal player, used for ISOs and such, is unusable.

I' ll check the link you posted and see if it helps.
Thanks!

---

### Post by oobe-feisty on 2009-03-07
see if this helped i recently switched to sshfs fuse and i found the results to be dramatic [http://ubuntuforums.org/showthread.php?t=1090085](http://ubuntuforums.org/showthread.php?t=1090085)

---

### Post by jbernardo on 2009-03-08
You're right, dramatic decrease in latency at least, and it appears also a huge speed increase. 
I just kicked NFS out, and put all my shared dirs with sshfs...

Thanks!

---

### Post by Yashiro on 2009-03-08
If sshfs-fuse is faster than NFS then something is badly broken.

---

### Post by jbernardo on 2009-03-08
It is... My guess is that it is a latency problem, and that NFS gets badly hit by it. I do now that if I connect the machines via ethernet, NFS is fast enough. And now I switched to sshfs, it also is fast enough over 802.11n, and visibly a lot faster than NFS over 802.11

---

### Post by jbernardo on 2009-03-22
Ok, now I took the time to benchmark everything, and even though sshfs is consistently faster reading, there is something very strange at play here.
The setup - a server pc connected via gigabyte ethernet to a netgear 802.11n router (I also tested with a linksys 802.11g router and the results were equal or worst). A media centre pc, connected via 802.11n, 10 meters away and with a brickwall between them. A laptop, 802.11g, just 4 meters away, and with the brickwall in between too.
A pc connected to the router via ethernet 100M.
Strangest of all - the discrepancies between write and read speed using wireless. The wired speeds are normal, the write speeds for 802.11n are the same as for ethernet, but the read speeds, are something else, up to ten times slower. 
Any idea on what is going on here?

A little extra info - the media centre pc or the laptop download from the internet at 7Mbit (my connection limit) without any problems. Ping with large packets also didn't show any problem.

---

