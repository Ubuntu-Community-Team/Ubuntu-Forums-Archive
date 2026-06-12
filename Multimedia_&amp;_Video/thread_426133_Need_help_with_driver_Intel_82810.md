---
title: "Need help with driver Intel 82810"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by ronnielsen1 on 2007-04-28
From what I've googled this video card seems to be linux capable (other than vesa) but I'm not sure what to do. Has anyone had success enabling 3d on this? I'm used to kde and I'm not sure what to do in xfce.


~$ lspci
00:00.0 Host bridge: Intel Corporation 82810 GMCH [Graphics Memory Controller Hub] (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810 CGC [Chipset Graphics Controller] (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801AA PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801AA ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801AA IDE (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801AA USB (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801AA AC'97 Audio (rev 02)
00:1f.6 Modem: Intel Corporation 82801AA AC'97 Modem (rev 02)
01:0e.0 Ethernet controller: ADMtek NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)

---

### Post by ronnielsen1 on 2007-04-28
I was one cup of ubuntu. How did I spill the beans? It changed again. Now I'm 5 cups of ubuntu?

---

### Post by AR_Kozz on 2007-04-28
For some moral support I'm having this same problem. I can't find anything on these boards about getting 3d going on the i810, either. And google just got me conflicting information, some sources said it worked fully, others said it lacked 3d support.

I'll be watching this thread to see if anyone comes up with the answer. 

One thing maybe: if you're using the native, disto-provided drivers these two files may be better. I don't remember where I got them, it was either a fedora repo or an intel site:

XFCom_i810-1.2-3.i386.rpm

and

I810Gtt-0.2-4.src.rpm

the first was the driver, the second something else needed to make it work. 


The native driver didn't work at all, now I can accelerate 2d at least.

If there's a way to get 3d working on the i810 someone plz spk up. I know it's an old chipset but the info needs to be out there.

btw ron if you dl those .rpm files use alien to convert them to .deb, so they'll install easily

the cups of ubuntu is just the site rank, it's totally random. Means nothing.You didn't spill the beans.

---

### Post by ronnielsen1 on 2007-04-28
Thank you for replying. Yes I used alien to turn the rpms to deb but they didn't seem to make a difference. Hopefully someone responds that knows an answer. I've also posted this on mepis (regular user on my box) and linux forums so hopefully we'll get an answer. I'll let you know if I get a response from one of the other two. I'm about ready to get a nvidia card. It's my sisters pc I'm trying to fix but it's frustrating when you get the conflicting info you mentioned.

---

### Post by TravMan63 on 2007-06-09
I'm looking for answers too....

-- my scenario - XP Pro with powerpoint on same box - installed xubuntu with impress 2.2
-- totem (not xine version) - with all codecs.... experiencing some jerky playback, some videos 
-- only play a few seconds and then stop... same machine played ok on XP/Powerpoint... 
----- (due to legal reasons XP/Powerpoint had to be removed...)

Have you found any info yet?

Here's stuff to research:

[http://www.intellinuxgraphics.org/download.html](http://www.intellinuxgraphics.org/download.html)
[http://support.intel.com/support/graphics/sb/CS-010512.htm](http://support.intel.com/support/graphics/sb/CS-010512.htm)

TM

---
update 2007-06-11
I have found that xine plays videos MUCH smoother than gstreamer
AND powerpoint player plays *.ppt files much smoother than Impress (transitions etc)

---

### Post by RiTarDid on 2008-01-25
also using an 810.  video plays back good with mplayer, but when i crank on compositing or try to use 3D effects I experience undesirable results.  I am checking out the source drivers from intel, and the files posted by AR_Kozz....was the second one a sound driver maybe?
Also, this is my second Xubuntu install on this machine, last time the sound worked, this time it doesn't.  Anyone else have to tweak their sound?

---

