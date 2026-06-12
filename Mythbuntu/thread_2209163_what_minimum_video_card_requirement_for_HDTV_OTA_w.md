---
title: "what minimum video card requirement for HDTV OTA with mythtv?"
date: 2014-03-04
forum: Mythbuntu
---

### Post by sdowney717 on 2014-03-04
gpu model numbers for 

Amd?
Nvidia?

I have several older PC's I can turn into mythtv PC.
For example, one has an AMD HD 2600 pro. This card has trouble playing 1080p internet flash in ubuntu due to no driver support from AMD.
The HD 2600 pro  plays flawlessly perfect in windows7 for 1080p flash online.

So for AMD seems for video, unless you get a modern system with an advanced card,  mythtv not be as good as an nvidia card with nvidia drivers?

What is the least nvidia card usable.
6200 GS, 6600 GT,  7600 GS? , etc...?How low can you go and get the HDTV working ok, and say be able to watch h264 video files locally?

I know those nvidia cards cannot play 1080p online flash video in windows7.

The geforce 6200 can play 1080i wtv files in WMC very well.
I have a 6200 nvidia card and did some tests. 
In ubuntu 14.04 with VLC, the card can play 1080i wtv WMC recorded tv files fine, IF you leave deinterlacing off. You will see interlace artifacts!
If you turn deinterlace on, then the video slows down.
In WMC, WMC is able to deinterlace on that card fine with no video slowdown.

---

### Post by SeijiSensei on 2014-03-04
On NVIDIA hardware, you need to use a player that can make use of its proprietary "VDPAU" code built into the graphics processor.  With VDPAU, the video decoding for highly-compressed codecs like H.264 is handled in the adapter leaving the CPU free to do its usual tasks.  VDPAU support first appeared in the 8xxx line of NVIDIA adapters and has been available ever since. 

The bigger problem might be finding a card with the proper connector.  Some older machines do not have a PCI-Express slot, though there are a [couple of PCI cards]("http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=100007709%20600007313%20600007853&IsNodeId=1&name=PCI") in the 8400 series.  Finding cards for machines with AGP slots is pretty difficult these days, and none of the ones at Newegg support VDPAU.

---

### Post by sdowney717 on 2014-03-04
AGP is harder to find even used for a decent price. I did buy one off ebay for $26 an agp ATI HD 2600 pro, but was very dissappointed at its performance in Ubuntu.
In windows it is perfect, AMD still has a driver for it for windows.

Still would like to know for nvidia the minimum gpu that can handle mythtv. Since Nvidia still provides a driver for older GPU, I assume it is better than ATI for what I want to do.

In Ubuntu, an Nvidia 6200 can play 1080i recorded TV file from WMC well, except for if deinterlacing is enabled. smplayer or vlc makes no diff.

---

### Post by SeijiSensei on 2014-03-04
You probably have a decently powerful CPU.  I once had a Pentium III box with a 6150 that could not play 720p H.264 content.  It might have worked on a faster machine.  This was when H.264 content first started appearing on the Internet.  For a while I converted everything with XviD in the AVI container to get around this problem.  Then I got a 9500GT which eliminated the problem entirely.

---

