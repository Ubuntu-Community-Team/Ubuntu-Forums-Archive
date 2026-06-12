---
title: "Stuttering video in MythTV"
date: 2009-10-27
forum: Mythbuntu
---

### Post by Hoggle on 2009-10-27
I have an issue with stuttering video while viewing ClearQAM HD channels - its worse w/ NBC for some reason. It plays for about 2 seconds, stops for 1 second, plays for 2 sec. etc.... The digital channels are fine. 
 
here is my setup:
Tuner: HDHomerun
GBE network on C6 cable through a GBE Switch, all pc's 1000mb/s
Switch connected to a 10/100 W/L Router (POS Dlink)
 
Myth Backend/frontend:
Core2Quad 6600
4GB DDR2 800 RAM
GBE
3TB Raid 5 for movies/music/pics
500 GB for OS and trash files and recordings (prior to editing and putting "in production")
ATI 2400XT HD Video
Running MythBuntu 9.04
 
Frontend
ZOTAC IONITX-C-U Intel Atom N230 (the single core one)[http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028](http://www.newegg.com/Product/Product.aspx?Item=N82E16813500028)
The board has the NVIDIA GeForce 9400M graphics.  I'm using Nvidia supplied graphic drivers, 190.42.
1 GB DDR2 800 (can add 1 more GB if needed)
1 80GB SATAII HDD
Running Mythbuntu 9.04.  Also has XBMC alongside.  (I'm following this link:[http://electricshoes.tumblr.com/post/92305367/ubuntu-xbmc-aeon-stark-mythtv-good-times](http://electricshoes.tumblr.com/post/92305367/ubuntu-xbmc-aeon-stark-mythtv-good-times)
The HDHomerun is pulling 92% signal from the ClearQAM HD Channels.
Is this stuttering a result of the board? 
Is the processor handling the graphics?  If so, why isn't the Nvidia Graphics doing the work?
Is there something i need to do after i install the Graphics Drivers to get the video to work on it? I just ran the .sh and went with it. I didn't do any post install configuration. Do i need to?
Could it be my piece of 5*@# router? I thought if everything is in the switch, that it bypasses the router, only talking to it when it needs to go outside.
 
now, in reading the reviews and all the press, this board could do all that i wanted. It has 1080, the NVIDIA GeForce 9400M graphics, HDMI etc.... I'm not running Blueray or anything, just TV. Hell, even my Samsung LCD, with the built in tuner, can run ClearQAM HD Channels. Surely my tv isn't more powerful than the Nvidia 9400M or the Proc/Chipset on the board.
 
Will this help? i was planning on doing a minimal install of ubuntu, install what i need to get Myth and XMBC on, and their associated applications (xine, vlc, mplayer, codecs, whatever) and leave the gui off. Or maybe installing a small gui like Fluxbuntu.

Can somebody help me figure this out?  What's causing my stuttering?  What can i do to fix it!
 [U]

[/U][]("http://www.mythtvtalk.com/forum/editpost.php?do=editpost&p=48239")

---

### Post by SiHa on 2009-10-27
> Is there something i need to do after i install the Graphics Drivers to get the video to work on it?
I think you'll find you need to setup a VDPAU playback profile. I can't for the life of me think why such an important new feature that so many people are going to want to play with doesn't have a profile defined by default, but there y'go. It's free, so I'm not complaining.

In TV Settings -> Playback (I think) there's a screen with all the playback profiles (CPU--, CPU-, Slim, CPU+ etc.). Create a new profile called whatever you like, then add a new entry. I've used >0, 0 for the screen size so that it just uses VDPAU all the time.
For the deinterlacer on the next screen start with BOB (2x) and a fallback of Temporal (1x). Not sure quite what the 9400 is capable of, you might be able to use one of the advanced deinterlacers.

---

### Post by Hoggle on 2009-10-28
Siha,

Thanks for the tip.  I think that's the something i need.  I tried to make the changes you said, but I ran into a few things.  Mainly the Deinterlacer.  I used BOB (2x) in the first box, but i didn't have the Temporal option in the fallback.  There were alot of others; i tried to stay away from any that dealt with increased CPU  useage.  

It did make a difference, though, only in reverse.  It caused the HD channels to stop.  What i mean, it was like 1 FPM (frame per minute, not second!).  I played around with some different combinations, but honestly, i'm not sure WHAT i was changing and WHY i was changing it.  What is an "advanced deinterlacer" and what is it advanced against?  What is a non-advanced deinterlacer then?  

Also, I did make a new profile, after looking at the CPU-, CPU+, CPU++ whatever.  What are those choices, and how does it relate to the graphics issue?  What does the new entry, 0>0 do that the other options dont?

Thanks for the assist, again.  I've made progress, but just in the wrong direction.  I guess, in looking at it, you'll get to your destination, eventually, by only going in reverse.

---

### Post by SiHa on 2009-10-28
The different profiles basically dictate what hardware / software you want to use to do the video decoding, and for what resolutions. If you have dedicated decoding hardware (you do - the 9400), then you can use that, reducing the load on your CPU. Otherwise you have to do it in software, so you go from CPU--, through to CPU++.

The default CPU- profiles use the old nVidia API, XvMC, which was suited to the older chipsets, and didn't work terribly well (IMHO).

Now we have VDPAU which is nVidia's latest offering. It allows their newer chipsets to decode HD MPEG2 and H.264 streams. If you've created a new entry, and set the 'Decoder' box to "nVidia VDPAU acceleration", that should use the 9400 for your video decoding.

If you've done it right, the playback profile you've just created should have one line:

**if rez>0 -> vdpau & vdpau.**

That's all I had to do, and my CPU went from 166% to 18% when decoding BBC-HD (720p, I think).

If it's still not working, then I don't know, sorry. I'm far from an expert. Have a look for posts by 'jyavenard'. Seems to be the VDPAU guru around here!

---

### Post by Hoggle on 2009-10-28
SiHa,

Wonderful, thanks again.  
IIRC, i didn't see Nvidia VDPU option that you mentioned in my decoder box.  I may have missed it, but i'll check at lunch here in a few.

---

### Post by SiHa on 2009-10-28
*smacks head*:oops:
No, the VDPAU option is only there in 9.10. Sorry, I'm so caught up with trying to install this myself, I didn't notice you're on 9.04.

If you want VDPAU with 9.04 you'll have to use JY Avenard's backport. There's tons on here about it, [[COLOR="Blue"]_this_[/COLOR]](http://ubuntuforums.org/showthread.php?t=1063102) thread, being one of the hottest.

Then again, Karmic Koala (9.10) is out tomorrow....

---

### Post by Dewey_Oxberger on 2009-10-28
I did a clean install of 9.10RC and VDPAU has three profiles set up by default.  I don't recall the verbage but they are something like VDPAU High Quality, VDPAU Normal, and VDPAU Slim.

Good news...

Now if only the worked for me (I'll post that on a different thread).

---

### Post by SiHa on 2009-10-28
Ah, must've added those in since the beta.

---

### Post by Hoggle on 2009-10-28
> **SiHa said:**
> *smacks head*:oops:
No, the VDPAU option is only there in 9.10. Sorry, I'm so caught up with trying to install this myself, I didn't notice you're on 9.04.

If you want VDPAU with 9.04 you'll have to use JY Avenard's backport. There's tons on here about it, [[COLOR=Blue]_this_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1063102") thread, being one of the hottest.

Then again, Karmic Koala (9.10) is out tomorrow....

cool.  I'll wait til then.  Got KungFu anyway tonight, so won't be able to work on it anyway.

---

### Post by usmcstitch on 2009-11-02
OK, an update.

Its been awhile since my last post.  Basically, I "nuked it from orbit" and installed a clean install of 9.10 (btw, the new myth interface :()

It does indeed have 3 VDPAU settings, and Dewey was correct, VDPAU Slim, normal, HighQuality.  Using Slim, seems to work fine.  Using Normal causes slight hitching/stuttering.  Forget about HighQuality.  I also created a new profile as mentioned by SiHa earlier.  It seems to work fine. 

My question(s) are,
 what is the difference between these settings (slim, norm, hq, and SiHa's custom)?  What do the >, =, < mean in this context?
 And is there any way to tweak the settings to get a better/image or more power or whatever?

My TV is a 32" 720 HDTV LCD. 

Still, though, i would think the 9400 would be a little more powerful, being the bee's knees and all.

EDIT:  after looking at it again, SiHa's config is the same as the VDPAU HighQuality, but it works better.  WTH?

---

### Post by nickrout on 2009-11-02
perhaps reading the documentatin would work for you?

[http://www.mythtv.org/wiki/Playback_profiles](http://www.mythtv.org/wiki/Playback_profiles)

[http://www.mythtv.org/wiki/Vdpau](http://www.mythtv.org/wiki/Vdpau)

Or following the mailing list, etc.

The < and > are standard mathematical signs, like for example IF the resolution is GREATER THAN 640x480 AND LESS THAN 720x400 use THIS DECODER.

---

### Post by SiHa on 2009-11-02
> **usmcstitch said:**
> 
My question(s) are,
 what is the difference between these settings (slim, norm, hq, and SiHa's custom)?  What do the >, =, < mean in this context?
 And is there any way to tweak the settings to get a better/image or more power or whatever?

My TV is a 32" 720 HDTV LCD. 

Still, though, i would think the 9400 would be a little more powerful, being the bee's knees and all.

EDIT:  after looking at it again, SiHa's config is the same as the VDPAU HighQuality, but it works better.  WTH?

The only difference, is that my profile doesn't use any custom filters, cos I don't know what they do!

---

### Post by kja999 on 2009-11-02
Simple I know, but have you checked for any messages logged when running mythfrontend from a console ?
I have seen similar issues as this due to audio buffer errors ... the client will pause vid while waiting for the sound to catch up.

---

