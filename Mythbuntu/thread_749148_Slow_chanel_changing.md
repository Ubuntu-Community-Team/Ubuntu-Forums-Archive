---
title: "Slow chanel changing"
date: 2008-04-08
forum: Mythbuntu
---

### Post by extasy on 2008-04-08
I have read around the net about the livetv beeing slow chaning chanel. For me it takes about 5 sec to just change chanel. Compairing to a Dreambox it seems forever.

Anyone knows if they are planing on working to reduce the chanel chaning time in mythtv? I use this system mainly as a HTPC with live tv about 90%. The rest is pvr and music. So for me it's a big issue.

Henrik

---

### Post by viciouslime on 2008-04-08
I believe the delay is associated with the fact mythtv is constantly recording the live stream to allow you to pause live tv. When you change channel, it needs to start a new recording. It might be possible to speed this up by looking at differnt filesystems, though I shouldn't expect a massive difference in performance.

Also, your TV card might well take a while to switch channels. There has been lots of work done in the past to speed up this process, but there are limits to how fast this can be done, most of them arising from your hardware. It takes a lot less than 5 seconds for mine to switch, but then it's a decent TV card plugged into a fast computer.

YOu might like to consider alternatives to mythtv if you're watching live tv 90% of the time...

---

### Post by nasha on 2008-04-08
[rant]I'd just like to point out that the Dreambox's version of linux is specifically designed for the hardware that it runs on... 
MythTV however is designed for maximum hardware flexibility, and sure there still some glitches, afterall, its still in pre-release stages (0.21).
I think MythTV has done amazingly well to be as advanced as it is in early stages of development.

My channel change takes about 2-4sec depending on what the backend is doing at the time. There is some initial pause built in to allow input of numbers greater than a single digit. I wouldn't consider this much of a delay anyway, even at 5sec... You going to miss 5sec of a program?
[/rant]

The above poster is correct, its due to the HDD bufferering. Your not actually watching LiveTV, ur watching a slightly delayed recording off the HDD, not the direct stream.

Just my two cents,
Nasha

---

### Post by agent5150 on 2008-04-08
I had this problem with IDE drive.  Switched to SATA drive recently (board support sata 150 only though the drive is sata 300/II) my channel change rtime on external satellite receiver is now 3 secs.  

Check if your HD dma settings are correct.

---

### Post by Nikas on 2008-04-08
My channel change takes about 10 sec. :(


I have IDE-drives, new ones with DMA activated.


/dev/hdc:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
 **using_dma     =  1 (on)**
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0


/dev/hda:
 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 unmaskirq     =  1 (on)
** using_dma     =  1 (on)**
 keepsettings  =  0 (off)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 30401/255/63, sectors = 488397168, start = 0

---

### Post by agent5150 on 2008-04-08
How's your mysql performance.  This could be a performance issue.  in my my.cnf I have the following under the [mysqld] section:

key_buffer = 16M
table_cache = 128
sort_buffer_size = 2M
myisam_sort_buffer_size = 8M
query_cache_size = 16M 

It improves overall performance.

---

### Post by extasy on 2008-04-08
I'm on a Intel P4 2,66 Ghz system with a 500GiB Hdd with 8MiB cache 1GiB, I use the newest v4l drivers for the Hauppauge WinTV-NOVA-T-500 card. Front and Backend in one system.

If the speed problem is with the Hauppauge card witch one could I change to in order to get a quicker dvb-t channel changing? And is it possible to remove the buffering time of mythtv. I would prefer to have instant change to the desired channel and then start to record from there.

Is there any guide of how to trim the channel chaning of mythtv?

---

### Post by Mrbbad on 2008-04-10
Interestingly, I don't have channel changing problems.  I have laggy PROGRAM GUIDE problems.  Sometimes I can push up/down in the program guide and count to 10 before it acts.  Also, when watching videos/show I'm playing back it can lag when I hit pause/FF/RW quite significantly.

I don't know if these issues are correlated or not, but know any little trimming/tweaking in general even just for channel changing might help or...

who knows...

---

### Post by ReddogOne on 2008-09-15
Haven't coded (or seen the code for MythTV) but have worked on software for some major broadcasters in the past.

As I understand it (in MythTV as stated above) everything is recorded and then played from the disk. Never done this for a commercial STB but it sounds like a troublesome way of doing it (in regards to speed).

It takes up to a second (depending on the i-Frame rate) to get enough information to be able to start showing video. But as this is being copied to disk you probably have to wait for a bit to be written to the disk (more than a second) then read a lump off the disk before you start decoding and then as its done is SW maybe 1/2 second to get the first frame.

So changing channel goes from 0.5 (ish) to > 2.5 (allowing for my guess working). This doesn't include other lags in the system.

If it then waits for extra numbers to be entered rather than starting the tune straight away and re-starting if a another number is entered... it all adds up.

Alternate way is to push the feed to the frontend and disk at the same time and only switch to the recording if the user tries to pause or rewind live TV.

---

### Post by DutchLoki on 2008-09-15
It's been a while since I read an discussion about channel switching, must be at least a few days... 

PLEASE READ THIS:

[http://www.gossamer-threads.com/lists/mythtv/users/346910](http://www.gossamer-threads.com/lists/mythtv/users/346910)


In short: mythTV is not designed for fast channelswitching... differently said: its designed wrong and none of the developers dislikes it enough to fixe it (its a lot of work).

So if anyone has some sparetime: go for it... its opensource and good developers are always welcome and appreciated.

---

### Post by Antharian on 2009-05-17
> **DutchLoki said:**
> It's been a while since I read an discussion about channel switching, must be at least a few days... 

PLEASE READ THIS:

[http://www.gossamer-threads.com/lists/mythtv/users/346910](http://www.gossamer-threads.com/lists/mythtv/users/346910)


In short: mythTV is not designed for fast channelswitching... differently said: its designed wrong and none of the developers dislikes it enough to fixe it (its a lot of work).

So if anyone has some sparetime: go for it... its opensource and good developers are always welcome and appreciated.


This has been the least flame intense discussion of the channel change issues around mythtv.

With that said, are there any ideas for how the channel change should have been implemented?  From what I read, it seems that the LiveTV is just a frontend to the recording section: ie scheduling and playing a recording right now.



Regards

---

