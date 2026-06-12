---
title: "TV Card issues....Hardware Suggestions...."
date: 2014-08-22
forum: Mythbuntu
---

### Post by SolomonMan on 2014-08-22
All,
I am re-posting this in this forum as it may be more relevant here.....

 Recently been interested in setting up my Rig to be occasionally a DVR of sorts...Basically want to record a few shows that I am never home to see.

 My setup currently is running Trusty Tahr and has an Avermedia M791 Card which from what I can gather is a [SIZE=2]NTSC/ATSC TV tuner card with FM radio.
 The card appears not to be supported under Linux. The last dmesg says that the card is not recognized and suggested a series of many other cards. 
 After trying a few (modprobe commands)  I went searching online and from what I can gather it does not look promising.  If anyone knows otherwise please chime in and please let me know of the procedure... but it also does not appear to pick up a signal in Windows Media Center even though everything appears fine under Device Manager.

 Anyways, I am looking to record from a 40 foot Towered Antenna (Ohio,United States ) a few TV shows. [SIZE=2]The antenna works wonderful with my home office TV which is a digital flat panel Phillips TV. The antenna also works great for all the other TVs in my home. 

[/SIZE]With this situation going on I have basically began looking at new hardware to replace the non supported card/possibly not functioning card. 

 There are many different cards and a network device that I am considering.
 The network device is a SiliconDust HDHomeRun Dual HDHR4-2US HD Digital Network Attached TV Tuner Device.  The cards I am really open but they must be supported both under Linux and Windows preferably without much Linux configuration effort. The network device may be a better option as my home has multiple PCs.

 So I am looking for card suggestions based on my need and\or whether anyone has used such network devices in there Linux environment.  (Not really sure if the network device would really need anything driver wise but interested if anyone has used one and their thoughts.) Please note here I am a novice on the media center\TV realm of things so looking for suggestions on the best way to get this to work.

 Thanks,
 Chris [/SIZE]

---

### Post by topcat5 on 2014-08-22
The HDHomerun Dual, works flawlessly with MythTV.  I have two of them on my system.  (antennas pointed in different directions)  If it is on your local network when you configure MythTV, it will find them automatically.  You only have to do a channel scan and configure the channel settings that are found.   There is also a pretty nice android signal meter which if you have a smartphone, can be used as a handy antenna aiming tool.   

If you want a card, I also have a Hauppage (sp) HVR-2250 card in my backend. (connected to a 3rd antenna)  This card does require that you manually copy a firmware file as described in the MythTV wiki, but beyond that, it's completely supported under the present version of Ubuntu (14.xx).   Like above you just scan and configure channels.  

All 3 devices have been working in my system for 2+ years without issue.

---

### Post by SolomonMan on 2014-08-22
topcat5,
Thanks for the reply!...I have been considering card wise the Hauppage HVR-2250 or the Hauppage 1250...I am thinking though HDHomerun will be the first purchase though to cover more bases. Then the card route possibly later.

Thanks,
Chris

---

