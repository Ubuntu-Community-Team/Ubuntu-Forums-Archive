---
title: "Setting up mythbuntu for dish network only"
date: 2011-12-03
forum: Mythbuntu
---

### Post by dkag7 on 2011-12-03
Hi,
I was wondering if i can get some help on a few questions i have when setting up...
The system will be a asus pundit P1-PH1 Pentium 4 3GHz and a pvr-150 capture/tuner card.

1. I have no OTA TV streams, I will only be recording (and live tv) what my dish network receiver (VIP211) has (my paid subscription package). Is there anything special i should do during setup to tell mythbuntu not to look for any OTA antenna but only use the dish network receiver? As it looks now the receiver will connect to the pvr-150 by composite (possibly coax). 
2. in the second picture of the setup, here: [http://www.mythbuntu.org/wiki/input-connections](http://www.mythbuntu.org/wiki/input-connections) there is a box to check called 'use dishnet long term EIT data". Is this referring to Dish Network? If so, it it referring to Dish networks Program guide? So that i can use this program guide to schedule recordings..?
3. The system will have a small 500GB HDD internally. I was thinking of having this for the OS and recordings. Seeing that it is so small, I want to add 2, 2TB HDDs via USB or esata connections. The idea is to record a show to the internal, then have mythtv automatically move the recording to one of the externals after it has been recorded (therefor making room for the next recording on the internal). is this a wise way to do it?
The other idea is to just record directly to one of the externals.
If this is better, should i have the external hooked up prior to the install, or do it later?
Will mythbuntu auto format this external HDD to whatever format it needs during setup?
I think it is ext3 now... is this the correct format?
The other 2TB HDD is full of movies (ffmpeg/h264 etc..) that i will want mythtv to be able to play, but not record to at all. 

Thanks for any input
Kurt

---

### Post by nickrout on 2011-12-03
> **dkag7 said:**
> Hi,
I was wondering if i can get some help on a few questions i have when setting up...
The system will be a asus pundit P1-PH1 Pentium 4 3GHz and a pvr-150 capture/tuner card.

1. I have no OTA TV streams, I will only be recording (and live tv) what my dish network receiver (VIP211) has (my paid subscription package). Is there anything special i should do during setup to tell mythbuntu not to look for any OTA antenna but only use the dish network receiver? As it looks now the receiver will connect to the pvr-150 by composite (possibly coax). 
2. in the second picture of the setup, here: [http://www.mythbuntu.org/wiki/input-connections](http://www.mythbuntu.org/wiki/input-connections) there is a box to check called 'use dishnet long term EIT data". Is this referring to Dish Network? If so, it it referring to Dish networks Program guide? So that i can use this program guide to schedule recordings..? I don't think so, if you are in the US use schedules direct for your data> 
3. The system will have a small 500GB HDD internally. I was thinking of having this for the OS and recordings. Seeing that it is so small, I want to add 2, 2TB HDDs via USB or esata connections. The idea is to record a show to the internal, then have mythtv automatically move the recording to one of the externals after it has been recorded (therefor making room for the next recording on the internal). is this a wise way to do it?
The other idea is to just record directly to one of the externals.
If this is better, should i have the external hooked up prior to the install, or do it later?
Will mythbuntu auto format this external HDD to whatever format it needs during setup?
I think it is ext3 now... is this the correct format?
The other 2TB HDD is full of movies (ffmpeg/h264 etc..) that i will want mythtv to be able to play, but not record to at all. 

Thanks for any input
Kurt

you can record straight to the external, in fact you should use the external and some of the internal, as 500G for the OS will have a lot of room to spare.

Set the external up so it always mounts to the same point in your file system, eg /mnt/external

Then make a directory /mnt/external/recordings, make sure the mythtv user and group have permissions to read from  and write to the directory. Then add that directory as a recording directory in the storage groups part of mythtv-setup. 

If the external drive is missing or not mounted, the directory /mnt/external/recordings will be missing and mythtv will not write there.

the directory /var/lib/mythtv/recordings will be on your internal, and will also be in the storage group by default. Therefore you have achieved your goal of using both drives. If the external is unplugged/not mounted the system will record to only the internal.

---

### Post by dkag7 on 2011-12-03
actually i just found this , here: [http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)

**  Guide Data, EIT, Program Info, and Media Metadata **

 **  New Features **

 
[LIST]
[*] Add a "universal" method of handling video, music, and game metadata [[24960]]("http://code.mythtv.org/svnredirect/24960")
[*] Add support for "Studio" attribute (including "Browse By" and statetype support for themes) [[26136]]("http://code.mythtv.org/svnredirect/26136")
[*] Add EIT Fixups for Norwegian NRK DVB-T transmissions [[26355]]("http://code.mythtv.org/svnredirect/26355")
[*] _***Add Dish Network (DishNET) specific EIT enhancements and features***_
[/LIST]
So hopefully this means:
1. I can scan for stations into dish network (dish networks vip211 receivers composite out, will be plugged into pvr-150 in put)
2. Use the EIT provided by dishnetwork

what do you think?

I wonder also if i must connect dish network by the coax into the pvr-150 for this (rather than using composite)?

thanks
Kurt

---

### Post by dkag7 on 2011-12-03
I did find this as well, but it is 2 years old from mythbuntu 8.10
maybe i need to get schedules direct?
(red bold below)
**3. Video Sources**

 [LEFT]Next escape back to the main setup screen.   Select #3 Video Sources.  Here is where you tell mythtv the methods by  which you will feed your mythtv installation television. For example,     I have two sources.  First,  I get a few ATSC stations from over the  air using an outside antenna.    Second,  I have the s-video of the  HVR-1600 hooked up to the s-video output of my Dish Satellite Receiver  Box.   The first source I called  antenna and used the “scan for  channels”  to cause Mythbuntu’s backend program to scan all 83 channels  while adding the active channels to an internal table.  The second  source I labeled “dish” and was created by subscribing to[ Schedules Direct]("http://www.schedulesdirect.org/").[/LEFT]
 
Source (dish sat receiver)  connected to  HVR1600 Mpeg encoder 

 [LEFT]Note:  Don’t hit Scan for Channels here  where you are configuring the Capture Device /dev/Video0.  After all,   the hardware encoder can’t scan. It creates mpeg video with whatever  baseband video you have connected to the HVR s-video input.   [COLOR=Red]**The only  time Scan for channels should be clicked  is where the HVR is connected  to an outside antenna or a cable TV line.    So you would click Scan for  channels**[/COLOR], for example,  if you were configuring  Capture Device: DVB0:   [COLOR=Red]**In my case,  I ” Fetch channels from listing source”  when I want to  bring down a list of my dish network channels I subscribe to.  The list  is configured at the Schedules Direct Site(See screen shot below) This  was an endless source of confusion for me**[/COLOR].   Anyway if you want,  you  can escape out to the Main window (sprocket wheels) and look at what  channels you have configured by choosing  #5.  the Channel Editor.[/LEFT]

---

### Post by nickrout on 2011-12-03
> **dkag7 said:**
> actually i just found this , here: [http://www.mythtv.org/wiki/Release_Notes_-_0.24](http://www.mythtv.org/wiki/Release_Notes_-_0.24)

**  Guide Data, EIT, Program Info, and Media Metadata **

 **  New Features **

 
[LIST]
[*] Add a "universal" method of handling video, music, and game metadata [[24960]]("http://code.mythtv.org/svnredirect/24960")
[*] Add support for "Studio" attribute (including "Browse By" and statetype support for themes) [[26136]]("http://code.mythtv.org/svnredirect/26136")
[*] Add EIT Fixups for Norwegian NRK DVB-T transmissions [[26355]]("http://code.mythtv.org/svnredirect/26355")
[*] _***Add Dish Network (DishNET) specific EIT enhancements and features***_
[/LIST]
So hopefully this means:
1. I can scan for stations into dish network (dish networks vip211 receivers composite out, will be plugged into pvr-150 in put)
2. Use the EIT provided by dishnetwork

what do you think?

I wonder also if i must connect dish network by the coax into the pvr-150 for this (rather than using composite)?

thanks
Kurt

EIT is carried in the DVB signal, which never reaches mythtv.

Say again, use schedules direct.

---

