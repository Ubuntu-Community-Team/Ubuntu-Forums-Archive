---
title: "Capture Video in Kino"
date: 2006-11-26
forum: Multimedia &amp; Video
---

### Post by jmtjet on 2006-11-26
I'm trying to capture video from my Sony Handycam DCR HC21 camera to Kino. Ubuntu 6.06 sees my ieee 1394 (firewire) PCI card in the device manager but I'm not getting any video when I try to capture. My ieee card shows up as Texas Instruments TSB43AB23, Status: Status, Bus Type:PCI, Device Type: unknown, Capabilities: unknown. I haven't a clue were to look for the problem. Would someone know how to get this thing working? Thanks.

---

### Post by Unterseeboot_234 on 2006-12-07
Hello, I have spent some time with this. I can get Kino to work on a i686, but not the capture feature. I did however find a stand-alone program that is part of Kino called dvGrab. So, even that didn't work at first. I had to add raw1394. So, now I have a terminal based program to capture. I type 

dvgrab -- help
look at the options, type dvgrab -blahBlah -blahBlah
and it starts the camera and grabs video.

Now, to make raw1394 ... that took [http://www.linux1394.org]("http://www.linux1394.org")

Study up there. Make sure your camera and your 1394 chip are on the "success stories" chart. I had to download the c files ```
build-esential
``` from GNU to get ```
./configure
``` (there are installation instructions on the 1394org site).

So, I've got 2 pieces of software when I want one. It'd be nice if Kino would do it all. I think it can. I'm not smart enough to make the connection between dvgrab and the buttons in Kino. But, then again, I'm i686.

What I think is the TI chip on 1394 uses a different protocol -- lynx or something. ubuntu appears to be built for the more common chip architecture.

Where I'm hung up is there are 3 other modules to ./configure to make a complete device. raw1394 builds and complains but finishes. The other modules want options during the ./configure. The directions given are for SuSe and RedHat.

---

### Post by SBFC on 2006-12-12
My box had libraw1394-8 installed already (edgy). All I had to do to get capture with Kino working was add myself to the 'disk' group (sudo addgroup oblivion disk) as it was the owner of /dev/raw1394.

Can't remember what brand my firewire card is though. Purchased it too long ago.

---

