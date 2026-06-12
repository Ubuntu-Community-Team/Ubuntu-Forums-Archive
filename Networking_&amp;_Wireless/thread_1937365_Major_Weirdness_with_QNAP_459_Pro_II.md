---
title: "Major Weirdness with QNAP 459 Pro II"
date: 2012-03-07
forum: Networking &amp; Wireless
---

### Post by ytene on 2012-03-07
I've just purchased a QNAP TS-459 Pro II NAS to replace an aging (and creaking) Apple Time Capsule. Unfortunately, my 64-Bit Oneiric build is prone to a complete kernel-panic system hang when using the NAS, something it never exhibited with the TC. 

My system comprises ubuntu 11:10 running on top of a Core i7 Quad system. I have added KDE to run as my GUI environment, on top of the default Window Manager. 

My system currently has a working Time Capsule connection. Here is my connection string for that:-

//192.168.1.40/Data /media/capsule cifs username=####,password=####,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

Since this worked, I thought it might be relatively straightforward to tweak the above to produce a new mount statement for the QNAP, so I produced one that looks like this:-

//192.168.1.41/Public /media/nas cifs username=####,password=####,rw,iocharset=utf8,file_mode=0777,dir_mode=0777

It worked, beautifully, and I was very smug for at least 20 minutes or so. At that point, my machine hung. We're talking a full system hang: screen, keyboard and mouse locking, and my Rhythmbox audio player catching a 1/5th snippet of a song in an endless loop. It took the hardware reset button to cure that problem. This has *NEVER* happened on ubuntu for me before...

Had a chat with the hard-core tekkies at work and they recommended that I replace the CIFS connection with something using NFS (which should be faster, more stable, etc). This took a little bit of tweaking, but at the second attempt I came to this:-

192.168.1.41:Public /media/nas                  nfs     defaults        0       2

which also connects just perfectly and appears to behave flawlessly. Obviously I had to add nfs-common and portmap to get that to work... Except it then exhibits the same problems as the CIFS connection, dropping dead after a short period of time. To give an indication of the "death time"... 

After getting the NFS mount to work, I flushed the original config of my Rhythmbox player [wiped /home/{me}/.local/share/Rhythmbox ] and re-launched, then directed the "folder import" across the NFS mount to my iTunes library now relocated to the QNAP... The player was able to scan 153 tracks before the interface hung and the system crashed. I can make it do this pretty consistently. 

One more point of note: when I use Rhythmbox now [selecting from the 150ish tracks] it seems to work fine... but a check in /var/log/syslog shows me this sort of thing:

Mar  7 21:27:13 voyager kernel: [ 3093.635159] r8169 0000:03:00.0: eth0: link up
Mar  7 21:27:22 voyager kernel: [ 3102.820707] r8169 0000:03:00.0: eth0: link up
Mar  7 21:27:26 voyager kernel: [ 3107.379628] r8169 0000:03:00.0: eth0: link up
Mar  7 21:27:56 voyager kernel: [ 3136.627584] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:15 voyager kernel: [ 3155.716853] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:21 voyager kernel: [ 3161.906999] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:26 voyager kernel: [ 3166.952556] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:37 voyager kernel: [ 3177.773495] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:48 voyager kernel: [ 3188.530705] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:53 voyager kernel: [ 3194.166439] r8169 0000:03:00.0: eth0: link up
Mar  7 21:28:58 voyager kernel: [ 3198.972636] r8169 0000:03:00.0: eth0: link up
Mar  7 21:29:04 voyager kernel: [ 3204.540730] r8169 0000:03:00.0: eth0: link up
Mar  7 21:29:28 voyager kernel: [ 3228.783041] r8169 0000:03:00.0: eth0: link up


I can't swear, but I'm pretty sure that I didn't get this to the Time Capsule! 

A couple more points. First, using *exactly the same hardware* and a different bootable OS drive [I use caddies] I can run up a copy of Windows 7 and it will connect to both the QNAP and the Time Capsule *flawlessly*. In other words, I am pretty sure I don't have a hardware, network, cable, or NAS problem. To verify, I also have 2 Mac Minis here, and both are quite comfortable working with the NAS and the TC. 

Every instinct leads me to suspect that I am just being a numpty and using a suspect connection profile for the CIFS or NFS links with Oneiric, but try as I might, I can't find it. 

I would be very happy to scrape logs, provide other config information, etc, to anyone willing to share their experience in the hope that we can fix this. Not sure if it's relevant, but on Saturday I also patched up the NAS to it's latest Firmware. I read the release notes, but I couldn't see anything that would suggest it fixes this problem... 

Any ideas please folks? [ Thanks in advance ... ]

---

### Post by ytene on 2012-03-08
I am not sure if this is going to help narrow down the problem, but today I dug out my Lucid Lynx build, applied all the latest patches, and installed nfs-common. 

I set up an entry in fstab, like this:-

192.168.1.41:Public /media/nas nfs ro,hard,intr 0 2

[ based on some advice from the tekkies at work ] and this seems to work just fine. Obviously I need to experiment a little with parameters [ I did try exactly the same settings under Oneiric and they did not work.

I am reasonably confident that there is something in the different between Lucid and Oneiric at a library level - or maybe even a kernel level - that must account for this. I will experiment a little further and see what else I can establish and report back.

If this update is read by any of the more experienced regulars, would one of you be kind enough to respond to this and let me know what I might need to provide in order to file a bug report?

Many thanks!

---

### Post by ytene on 2012-03-11
I've compeleted quite a bit more experimentation with this, trying various permutations to see what works. 

The short update is that I have been successful in getting an NFS mount from ubuntu 10.04 and now 12.04 (Precise Pangolin) Beta 1. 

The correct [slimmed down] connection string for the QNAP TS-459 Pro II [or, at least, a working one] seems to be:-

{QNAP IP Address}:public /media/{your mount point} nfs rw,hard 0 2

Note that you will need to have installed "nfs-common" in order to get the code that handles the NFS protocol over the network. 

I need to carefully qualify the level of success achieved here. Specifically, I have been successful in getting previously failing activities to work without difficulty. Those activities have included indexing my iTunes library after having relocated it from the Time Capsule to the QNAP, and the indexing means that I can now access it from Rhythmbox [which works beautifully]. 

This does not necessarily mean that all aspects of NFS performance and QNAP connectivity work successfully. Time permitting, I'd like to do some functionality and performance testing in the next week or so and will publish any results. 

For functionality I'd like to undertake testing of:-

Basic performance testing [QNAP vs Time Capsule / ubuntu vs Windows]
Audio and Video Streaming
File and Folder Security
File Locking from multiple clients
Folder synchronisation using eg rsync, Unison, etc

I can't promise to complete all [or any] of the above, but if anyone is interested in specific results, reply to this post and let me know what you're looking for and I'll try and oblige you.

---

