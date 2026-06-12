---
title: "Question about encoding"
date: 2010-10-29
forum: Mythbuntu
---

### Post by intelquadcore on 2010-10-29
Hello,
After solving my issue about the blackmagic intensity shuttle not working with mythbuntu, I have decided to look at the blackmagic intensity pro card. I have read from blackmagic's site and other forums that this capture card records uncompressed HD content... Which leads to huge file sizes if recording for extended periods of time.

Well my question is that can the mythbuntu operating system compress/encode the recorded HD content on the fly? Or does it have to finish recording then encode the video?

Thanks

*Also I tried looking for some internal capture cards that have component input (besides the intensity pro) sources but could not find any. Do you guys know of any?

---

### Post by LowSky on 2010-10-29
I'm pretty sure you are still stumbling int a problem picking a blackmagic product. I can't find anything stating it will work with MythTV. Sure it has Linux drivers, but to what extent will this card work? HDCP isn't supported on Linux so forget running a cable box to the PC using this method. The only way to get HD video from a cable box to your PC is the Hauppauge HDPVR at the moment.

An OS does not do video encoding, decoding, or transcoding. Software does that that. You can easily set up mythtv to run encoding jobs, but if you plan on recording TV you will need a big hard drive anyway. Many users here have 500GB, some users like me are well over 2TB of recordable space. Uncompressed HD will generally be about 4-5Gb an hour of record time. 

Could you tell us exactly what you are looking to accomplish. You are spending a good time thinking over a capture card but not on the rest of your hardware you will need. Also may I suggest that if you wish to go the MythTV route you take a look at their wiki's especially supported hardware pages. [http://www.mythtv.org/wiki/Category:Hardware](http://www.mythtv.org/wiki/Category:Hardware)

I'm not trying to rain on your parade. On the contrary, I hope your user experience goes very well. Its hard for us to recommend hardware that has little to no documentation for being known to work. If you have the expertise or the free time and cash to test the product then by all means I hope to hear amazing results.

I get the feeling you are new to both PC building and open source software. I learned by jumping both feet in a few years ago. It was a very bad experience and I swore off Linux a few times. I gradually had to learn how to get things to work correctly and what not to fiddle with. In the early days instead of fixing a problem I would just reformat and try again if all hope seemed lost. Now I use use a form of Linux 95% of the time in my home.

I started playing with MythTV during Ubuntu 8.10. At the time my tuner card (HVR-2250) didn't work and I had to use Windows for a while. I used Windows for about a year. Even when support for my tuner card appeared I still didn't have a full grasp on using the system fully. It wasn't until 9.10 that I finally got things to working pretty well, and not until 10.04 that all my bugs got ironed out. My tuner card still only half works (no analog) but it does what I really intended it for.

---

### Post by rhpot1991 on 2010-10-29
I'll second that I've never heard of blackmagic, so getting up up and running may not go too smoothly.  Do your fair share of research before purchasing one.

I keep a page of my hardware so I can recommend things that I know works: [http://www.baablogic.net/drupal/node/13](http://www.baablogic.net/drupal/node/13)

We have this somewhat outdated page as well: [http://www.mythbuntu.org/developer-hardware](http://www.mythbuntu.org/developer-hardware)

I would say without a doubt the 2 most popular tuners are the HDHR and HDPVR.  You can't go wrong with these.

As far as encoding goes you can do that after something is recording, you will however need enough space to record the HD program and then enough free space to transcode it down to a smaller size before you can delete the original fullsized version.  This will also be a painfully slow process.  I would recommend just picking up a large hard drive, then transcoding programs you want to keep around after you watch them and allow the rest to delete when you run low on space.

---

### Post by tgm4883 on 2010-10-29
Get the HDPVR. I've looked at the black magic cards and you are gonig to run into multiple issues.

1) uncompressed video takes lots of space
2) uncompressed video takes lots of I/O
3) transcoding everything you record will take lots of time.

I don't recall if you are able to transcode it on the fly with MythTV. If you can, you aren't going to want to as your system surely isn't beefy enough to transcode uncompressed video on the fly.

---

### Post by intelquadcore on 2010-10-29
> **LowSky said:**
>  HDCP isn't supported on Linux so forget running a cable box to the PC using this method. The only way to get HD video from a cable box to your PC is the Hauppauge HDPVR at the moment.

Yea, that's true to an extent, but I did find a way  to bypass the HDCP. A product called HDFury2 converts your HDMI source to component, which drops the HDCP and Black Magic Intensity Pro has component input (breaker cable required). This will allow me to record at 720p without any protection.

> **LowSky said:**
> An OS does not do video encoding, decoding, or transcoding. Software does that that.

Lol I know, I was just curious as to whether or not the mythbuntu OS had bundled software to do the encoding. Because I know a lot of the tuner cards do the encoding themselves to relieve stress off the CPU. 


"mythTV can automatically transcode videos after recording them using  mythtranscode. It can only transcode to RTJPEG and MPEG4, however, which  may not be what your device requires." Just saw that after doing some more research.

  
> **LowSky said:**
> You can easily set up mythtv to run encoding jobs 

Thanks, just wanted to confirm that

> **LowSky said:**
> Could you tell us exactly what you are looking to accomplish. 

I am looking to record some HD shows over the air, and that requires an ATSC tuner, which I already found looking at myth's hardware page. WinTV-*HVR*-*5500*

I would also like to record shows off my satellite box which has an HDMI out, hence me needing a capture card that has a component in option to bypass the HDCP. 

> **LowSky said:**
> You are spending a good time thinking over a capture card but not on the rest of your hardware you will need.  

I have taken a look at the requirements and my computer spec's far exceed the minimum requirements, I am just having a really hard time choosing a tuner card lol. I want it to be an internal card that has the component in option. You have been helping since I began thinking about this project and I appreciate it Lowsky

> **rhpot1991 said:**
> I'll second that I've never heard of  blackmagic, so getting up up and running may not go too smoothly.  Do  your fair share of research before purchasing one. 

[http://ubuntuforums.org/showthread.php?t=1333927](http://ubuntuforums.org/showthread.php?t=1333927)

The above user at that link was able to get it running.

> **LowSky said:**
> I get the feeling you are new to both PC building and open source software.

As for my specs I guess I should of mentioned it earlier... It's a custom built pc that I put together my self
i7 930 OC'd to 3.4GHZ
GTX 470 fermi cards in SLI configuration
6 gigs of corsair dominator ram
EVGA SLI FTW 3 motherboard
2 80 gig hdd's in raid config ( but I will probably up it for storage...)
I am going to use this pc just as a frontend/backend
Windows 7 64bit atm, just waiting to put mythbuntu on once I decide on a capture card... Might just dual boot it or take out the fermi cards for another build

I am a sort of new to the open source software, been messing around with ubuntu which is noob friendly

---

### Post by nickrout on 2010-10-30
Short answer, use your hd fury and an hdpvr

---

### Post by rhpot1991 on 2010-10-30
> **intelquadcore said:**
> 
I am looking to record some HD shows over the air, and that requires an ATSC tuner, which I already found looking at myth's hardware page. WinTV-*HVR*-*5500*

I would also like to record shows off my satellite box which has an HDMI out, hence me needing a capture card that has a component in option to bypass the HDCP. 


You are missing the perfect combination of a HDHR and a HDPVR which will handle both of those for you and I'm pretty sure cost a lot less.

Edit: Sorry didn't realize you said HDMI, can it do component too, if so my statement still stands.

---

### Post by intelquadcore on 2010-11-12
Thanks for all the input guys, I decided on going with the HD-PVR! 
Can't wait till it comes in.

---

