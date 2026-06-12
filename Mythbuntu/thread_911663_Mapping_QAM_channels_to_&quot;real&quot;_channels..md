---
title: "Mapping QAM channels to &quot;real&quot; channels...?"
date: 2008-09-05
forum: Mythbuntu
---

### Post by slickware on 2008-09-05
So, sorry if this is an idiot question.

I finally broke down and bought an HDHomeRun box. I first set it up on the alpha release of Mythbuntu (ibis), and it locked onto and added around 100 channels.(DIGITAL CABLE) However, when I went to "watch TV", most of them would time out, and they were all out of order and none of them were named anything even remotely like channels I know.

So, I went back to the stable version of mythbuntu. Same install, made sure the firmware was updated, same setup for the HDhomerun. This time the channel scan showed timeouts on EVERY channel (full signal,) (but somehow when it finished, they had all been added anyway). Going to "watch TV" results in a still picture of the first channel every 20-30 seconds (super choppy). 

So, I'm assuming the IBIS release is the way to go.
**What I want to know, for real, is -**how do I map these random QAM channel frequency numbers (71.3, 71.4, 71.6...etc) to my regular channels, which are like channels 2,3,4,5,15,25, etc?

---

### Post by newlinux on 2008-09-05
Once you know what they are, you can do it three ways - You can modify the channel information using mythweb (my prefered method), Using the channel editor in mythtv-setup, or using the frontend channel editor (I think you press "E" while viewing a channel in livetv. If the channel number you map exists in your schedules direct source once you have the right channel numbers you can use mythfilldatabase to update the rest of the channel information. I usually just input the XMLTVIDs and of the channels I want, delete the channels I don't want, and let mythfilldatabase take care of the rest...

---

### Post by slickware on 2008-09-05
That is my problem though -
I have nearly 100 channel, and only 7 of them were "found" with names (WGBH, WHDH, etc). 6 of those are showing up as "OFF AIR", whatever that means. 
How am I supposed to figure out what the other channels are, especially if every time I try and live-tv-watch them I get a "problem with the display" error?
Do I literally have to type in the callsigns for 100 different channels?

---

### Post by slickware on 2008-09-05
Is there a help file somewhere for this mapping/matching stage of the process? I've never done this before and feel like I am missing some key points.

---

### Post by newlinux on 2008-09-06
> **slickware said:**
> That is my problem though -
I have nearly 100 channel, and only 7 of them were "found" with names (WGBH, WHDH, etc). 6 of those are showing up as "OFF AIR", whatever that means. 
How am I supposed to figure out what the other channels are, especially if every time I try and live-tv-watch them I get a "problem with the display" error?
Do I literally have to type in the callsigns for 100 different channels?

No, you can just type in the XMLTVID or channel number, but you will have to do this for every channel that doesn't already have them. But you only have to do it once, unless your cable company moves the channels. Just because it scanned in doesn't mean it is displayable - the signal could still be very weak. Or your playback profile could be causing problems with display of some stations. Yes, you have to go through all of them to figure them out. Blame your cable company for not putting PSIP information with all your channels. Or you could find someone in your area that has already mapped the QAM stations - My local cable provider thread in avsforum.com keeps a file up to date.

---

