---
title: "Subtitles (NOT Close Caption)"
date: 2009-08-05
forum: Mythbuntu
---

### Post by sydneysuder on 2009-08-05
Hi,

I got mythbuntu up and running on a test backend server. I am using the DVBT version of the HDHR tuners.  That all works fine.

One thing that I use all the time on my older PVR is the subtitle functions. Having young kids means sometimes I have to have the volume really low (so they can sleep) or I have to fight their giggles and screams while watching TV. For that the subtitles are wonderful.

Here in Australia we don't get CloseCaptioning we get Subtitles within the signal. 

In myth I can see the "This program has subtitles" icon on the recordings but I can't for the life of me make them come up.  If I press 'T' I get "Caption:On" but no actual subtitles. Probably because it is for close captioning not subtitles. 

I have scoured the pages in the wiki that list all the commands you can invoke when viewing LiveTV/recordings and see nothing on how to enable subtitles


Any help will be appreciated

---

### Post by Mister.Vash on 2009-08-07
First thing that pops into mind - are you transcoding the videos after recording them?  It is possible that that might be dropping the stream.  If the are being transcoded, try setting up a test recording that doesn't get transcoded to see if that makes any different.

If that doesn't seem to be the issue, take a look at the keybindings.  I usually do this from the mythweb as it seems to be the easiest place to do it.

Out of the box, I think you should be able to get to it directly by
[http://machine/mythweb/settings/mythtv/keys](http://machine/mythweb/settings/mythtv/keys) where machine is either the hostname or the ip address of the system you have mythtv install on

My guess is that right now, your T key is bound to:
TV Playback  	TOGGLECC  	Toggle any captions

Try binding T instead to:
TV Playback  	TOGGLESUBTITLE  	Toggle Subtitles

I'm not positive is that would cycle through all available, or just turn one on and off, so you might also look to bind the following to some other keys:
TV Playback  	PREVSUBTITLE  	Previous subtitle track  	
TV Playback 	NEXTSUBTITLE 	Next subtitle track
TV Playback  	SELECTSUBTITLE_1  	Display subtitle 2  	
TV Playback 	SELECTSUBTITLE_0 	Display subtitle 1


Changing the keybinding from mythweb will require a restart of the frontend


I think that's at least a starting point and hopefully one of those will work

---

### Post by sydneysuder on 2009-10-13
MrVash.
Thanks for the reply. I took some time off Mythbunty as I was using a pc from work to do a proof of concept. Once I gave that back I had to wait until last weekend when I finally reconfigured one of my own computers as a virtual server (Xen Server 5.5) and installed Mythbuntu as backend server.

I am still having the same problem: Can't see the subtitles
However I have narrowed it down to Live TV.  I can see the subtitles on recorded shows.

1. Start live TV, pick a channel that has subtitles (double check against the Topfield 5000 in the living room).
2. Press the M key to get the OSD. There is no option for subtitles(DVB CC). Only for closed captioning which do not show anything when selected/turned on.
3. Record the show (press R)
4. After the show is recorded go to View recordings. Select and start playing the program.
5. Press M. Now there is an option for the subtitle (right below the option for teletext.
6. Select the only subtitle available and boom you can now see it.

Some noteworthy items:
1. If the program has the "close caption" icon in "view recordings" there will be NO subtitles. I can't see subtitles OR Close captioning.
2. If the program does NOT have close caption or subtitle icons I can see the subtitles(DVB CC) on playback.
3. This is the same on the myth server or any of the frontend computers (3 macs running 10.5.8 and Mytfrontend from sniderpad dated October 5 2009)

Here is my setup:
Server
[INDENT]Mytbuntu 9.04[/INDENT]
[INDENT]Virtual Machine on a Citrix XenServer 5.5 with 512MB RAM Assigned (of 4GB available on server)[/INDENT]
[INDENT]HDD1  Virtual Disk 9.5GB on main HDD (320GB SATA Barracuda)of the virtual server[/INDENT]
[INDENT]HDD2  Virtual Disk with 495GB on second HDD(500GB PATA Barracuda) of the virtual server.  This is mounted under '/video' and all storage settings in myth are set to point there (or a subdirectory of) [/INDENT]
[INDENT]Tuner = 2* HDHOMERUN DVBT[/INDENT]

Frontends
MacMini 2GBRam Running Mythfrontend from sniderpad (dated Oct 5 2009)
Macbookpro 2GB Ram Running Mythfrontend from sniderpad (dated July 2009)
Macbookpro 4GB Ram Running Mythfrontend from sniderpad (dated July 2009)

[IMG]http://img410.imageshack.us/img410/4199/picture1ui.png[/IMG]
[IMG]http://img394.imageshack.us/img394/5066/picture2r.png[/IMG]
[IMG]http://img504.imageshack.us/img504/3756/picture3mj.png[/IMG]

---

