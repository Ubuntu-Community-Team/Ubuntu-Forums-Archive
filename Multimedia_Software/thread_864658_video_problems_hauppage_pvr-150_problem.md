---
title: "video problems hauppage pvr-150 problem"
date: 2008-07-19
forum: Multimedia Software
---

### Post by miguel20 on 2008-07-19
Hi,
I've read many threads here and on other linux forums which have helped me learn about the inner workings of video capture on ubuntu 8.0x but I still can't solve my own problem.

I have been trying to capture video from my hauppage pvr-150 using VLC and ivtv.

I've managed (I think) to make a little progress but still no luck.  I'm an amateur and I really have given it my best shot to work this through...

At this point using VLC in capture mode I see static on my video screen.
My video input is coming from a pal sky (uk satallite) box so there is no channel tuning on my pvr-150 (channel changes are done on the external sat box) as it is just a raw feed.  I don't quite understand what channel I should be on to just see this raw input? On a VCR you'd set the channel to AV but this isn't an option on my PVR-150.   So I'm confused?  

At one point I wondered if my probelm was not locking on to the correct input but I've fed in to coax, svideo and the red white and yellow.  Which changes nothing.  

Anyone who can offer me a point in the right direction for my SPECIFIC problem I'd be very happy!  Thanks

M

---

### Post by itsdaveperdue on 2008-07-21
> **miguel20 said:**
> 
My video input is coming from a pal sky (uk satallite) box so there is no channel tuning on my pvr-150 (channel changes are done on the external sat box) as it is just a raw feed. I don't quite understand what channel I should be on to just see this raw input? On a VCR you'd set the channel to AV but this isn't an option on my PVR-150. So I'm confused? 


So are you plugging into the PVR-150's S-Video, Composite, or Coax?  If you're using the svideo or composite then there isn't "tuning".  If you're running through coax you need to set the tuner to use channel 3 (set in input sources, option is Preset tuner to channel).  If you're running through svideo or composite you need to setup those inputs to use the video sources you've defined.

There's lots of documentation for these setups.  Google is your friend.  Also MythTV's webpage has info, and mythbuntu.org, and a whole bunch of other websites I've seen around.  Just do a search and you'll find a lot...

---

### Post by miguel20 on 2008-07-21
Hi itsdaveprdue
Thanks for the info...I've now managed to get a solution to my problem.  I really don't think I'd have got there on my own.
this is the solution that helped me with my problem for anyone else's reference.
[http://ubuntuforums.org/search.php?searchid=44941908](http://ubuntuforums.org/search.php?searchid=44941908)

thanks

M

> **itsdaveperdue said:**
> So are you plugging into the PVR-150's S-Video, Composite, or Coax?  If you're using the svideo or composite then there isn't "tuning".  If you're running through coax you need to set the tuner to use channel 3 (set in input sources, option is Preset tuner to channel).  If you're running through svideo or composite you need to setup those inputs to use the video sources you've defined.

There's lots of documentation for these setups.  Google is your friend.  Also MythTV's webpage has info, and mythbuntu.org, and a whole bunch of other websites I've seen around.  Just do a search and you'll find a lot...

---

### Post by itsdaveperdue on 2008-07-21
fyi: I think that link is incorrect.  I'm curious to see the posting, can you post another?

---

### Post by wolfen69 on 2008-07-21
i also would like to see your solution. the link you provided does not work.

---

### Post by miguel20 on 2008-07-21
apologies...

try this one...

[http://ubuntuforums.org/showthread.php?t=655523](http://ubuntuforums.org/showthread.php?t=655523)

post #9 on that thread helped me..
post #10 is me outlining what worked for my pvr-150 
My card is defintiely a PVr-150 but i think it's a UK version?
it has no DVB type connectors on it.... but it has UK RF.

M

> **itsdaveperdue said:**
> fyi: I think that link is incorrect.  I'm curious to see the posting, can you post another?

---

### Post by itsdaveperdue on 2008-07-21
It works, looks good.

For some reason I thought you were using mythtv, ha.

My PVR-150 has a little cable you plug into it that has inputs for svideo and composite, I think spdif and analog audio.  I'd have to look at it again to be sure...

Glad it works for you, though.

---

### Post by miguel20 on 2008-07-21
I'd quite like to use myth TV and did try but I was told later that  it is not so good (or doesn't work at all?) with the PVR-150.  
Do you have MythTV working with your PVR-150?

cheers

M
> **itsdaveperdue said:**
> It works, looks good.

For some reason I thought you were using mythtv, ha.

My PVR-150 has a little cable you plug into it that has inputs for svideo and composite, I think spdif and analog audio.  I'd have to look at it again to be sure...

Glad it works for you, though.

---

### Post by itsdaveperdue on 2008-07-21
> **miguel20 said:**
> Do you have MythTV working with your PVR-150

I do indeed.  I'm using Mythbuntu ([www.mythbuntu.org](www.mythbuntu.org)) and everything seems fine.  I have it controlling my cable box via the transmitter included with the PVR-150.  Right now I'm having a problem going past channel 99 while watching live TV (recording above 99 seems to work fine).  I think that problem has to do with a configuration I have somewhere and not the PVR-150; I'll be looking into that next.

I would not recommend installing MythTV on your machine if you're just going to watch TV with it or play video games (a bit of overkill if you ask me).  I have my (slightly underpowered) machine dedicated to being a mythtv backend.

---

