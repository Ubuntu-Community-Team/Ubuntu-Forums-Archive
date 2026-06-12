---
title: "Newbie Questions Before I Buy a Tuner Card"
date: 2009-03-15
forum: Mythbuntu
---

### Post by arthritisankle on 2009-03-15
I want to install myth on an exisiting machine.  I don't have a video card for TVout so I just want to record stuff and stream it to one of my xbox360's.  I need the computer to do the typical computer stuff as well as recording programming.

Will myth record programming in the background while I use the computer to do other things (web surfing, ripping DVD's)?

Can I stream to two 360's at once?  

I have an IntelP4 2.8 GHz with 1GB of RAM.  Can I record and stream HD content?  Can I do better than the typical 7GB/hour if I don't want to output directly to a TV?  Can I transcode HD to a smaller container and still have "HD" quality (whatever that means)?  Am I right in thinking that streaming recorded HD to a 360 would be less taxing on the system than watching it live?

I am looking at getting a Hauppauge WINTVHVR1600 DUAL Tuner to record SD cable and HD over the air.  Am I overlooking something important? 

Are there any tutorials specifically for and setting up mythuntu on an existing PC?

You can probably tell by these questions that I really don't know what I'm getting myself into, so I appreciate your input/advice.  Ubuntu forums are the best.

---

### Post by arthritisankle on 2009-03-16
Any help?

---

### Post by Hackit on 2009-03-16
Hi,

I'm by no means a mythbuntu expert but let me shed some light on some of your questions.

A pentium 4 2.8 is a little old school for hd (i'm pretty sure)
I have an intel core 2 duo 2.2 and this is still not the best, I also have 4 gigs of ddr2 667 ram.

Whats the front side bus of the p4?
whats the l1, l2 and l3 if you have l3 cache?

As far as streaming, I would say if not wireless n (and I mean all computers are N) you would want to direct connect for streaming HD content to an xbox360. I would think you could try this now so long as the computer is connected to the same network as the xbox360. try and stream an avi and see what happens.

As far as the hauppauge card I also have a Hauppauge 1600 card and it was easy to setup (I'm so new that when I say easy it's easy). I have posted a guide if you search the forums.

As far as a specific guide, doubt you will find one, best bet is to find all the specs of your system, MB, Memory, Video, sound and see if you can find guides or steps to get it all working.

Maybe you can try the live cd first, or just install and see what does not work.

Hope this has helped.

kev

---

### Post by movieman on 2009-03-16
> **Hackit said:**
> A pentium 4 2.8 is a little old school for hd (i'm pretty sure)

Well, it will play 1080 HD compressed with MPEG-2 or Xvid, but not H.264. It should record and stream to another system OK though.

As for recording in the background while doing other things, yes, it will be fine for that so long as what you're doing isn't too CPU or disk intensive.

To be honest, you might be better to spend a couple of hundred dollars on an Athlon X2 and cheap motherboard; performance will be better and power consumption lower.

---

### Post by oobe-feisty on 2009-03-17
> Will myth record programming in the background while I use the computer to do other things (web surfing, ripping DVD's)? yes it will and to add this will not take up any system resources however commercial flagging and transcoding will.

> Can I stream to two 360's at once?  possibly the answer is dependent on your systems network upstream and the bitrate of the video content

> 
I have an IntelP4 2.8 GHz with 1GB of RAM. Can I record and stream HD content? Can I do better than the typical 7GB/hour if I don't want to output directly to a TV?
yes you can record HD content fine on that system 

> Can I transcode HD to a smaller container and still have "HD" quality (whatever that means)? yes however you will loose quality and it will be taxing on CPU 


as for your other questions you can look up [Hauppauge WINTVHVR1600 DUAL]("http://www.linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1600") or other devices on [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page) and other questions on [http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)

---

### Post by arthritisankle on 2009-03-17
Thanks for all your help.  I'm going to order the card and give it a go.   

Maybe I should upgrade the processor while I'm at it.  The mother board has 1MB L2 cache.  I would try to replace it as well, but I don't want to have to format and reinstall everything.

I'm currently streaming video (SD only) with ushare and music with twonky.  It will be nice to use myth for both.

---

### Post by theophile on 2009-03-17
If you're not going to be watching the recordings on the backend computer, those specs are perfectly fine. I'd invest in a larger hard drive, though, and don't worry about transcoding for short-term storage. You can compress files and keep HD quality using x264 but the encoding takes an extremely long time. On my P4 2.4, it takes about 12 hours to compress a 43-minute TV show.

But for a dedicated backend, that system should be plenty. Just get a big hard drive.

---

### Post by arthritisankle on 2009-03-17
> **theophile said:**
> If you're not going to be watching the recordings on the backend computer, those specs are perfectly fine. I'd invest in a larger hard drive, though, and don't worry about transcoding for short-term storage. You can compress files and keep HD quality using x264 but the encoding takes an extremely long time. On my P4 2.4, it takes about 12 hours to compress a 43-minute TV show.

But for a dedicated backend, that system should be plenty. Just get a big hard drive.

Am I correct in understanding that streaming HD from the mythtv upnp server is less resource intensive than playing it?  I should just get a big 1TB drive and not worry with transcoding or commercial flagging?  

If I'm going to get a massive drive, then there's really no reason to transcode the SD stuff either right?  (maybe commercial flagging though)  I've never streamed anything but SD .avi's with xvid codecs to my 360.

My new HD TV is coming saturday and I can't wait to get this rocking.  

Thanks to everyone for all the help. My research was just getting me more confused.  You guys are princes among men.

---

### Post by ashdavely on 2009-03-17
> **oobe-feisty said:**
> Hauppauge WINTVHVR1600 DUAL[/URL] or other devices on [http://www.linuxtv.org/wiki/index.php/Main_Page](http://www.linuxtv.org/wiki/index.php/Main_Page) and other questions on [http://www.mythtv.org/wiki/Main_Page](http://www.mythtv.org/wiki/Main_Page)

Is the HVR-1600 problematic to get working with both SD and OTA HD? I see a few posts here about it recently that look discouraging still. Does it work out of the box with Mytbuntu 8.10? I also see a problem with it and nvidia drivers.

---

### Post by theophile on 2009-03-17
> **arthritisankle said:**
> Am I correct in understanding that streaming HD from the mythtv upnp server is less resource intensive than playing it?
Definitely. Playing HD content is extremely CPU-intensive, unless you've got VDPAU going. Streaming over the network should not use much horsepower at all.

> I should just get a big 1TB drive and not worry with transcoding or commercial flagging?
That's what I'd do. Though I'd still commercial flag cause it's nice not to have to fast forward. I only transcode for long-term storage, like shows or movies I know I'll want to watch again.

> If I'm going to get a massive drive, then there's really no reason to transcode the SD stuff either right?  (maybe commercial flagging though)  I've never streamed anything but SD .avi's with xvid codecs to my 360.
Probably not. SD takes up far less room to begin with. On the flip side, it transcodes to xvid a heck of a lot faster than HD does to x264.

---

### Post by arthritisankle on 2009-03-17
Thanks again.  I like Hackit's idea of grabbing some HD content and trying it out before buying a tuner card.  I found some 1080p test patterns
[here]("http://www.w6rz.net"), but they all seem to have a .ts file extension and the 360 doesn't recognize them.

---

