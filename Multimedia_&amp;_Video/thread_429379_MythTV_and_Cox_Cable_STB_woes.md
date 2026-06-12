---
title: "MythTV and Cox Cable STB woes"
date: 2007-05-01
forum: Multimedia &amp; Video
---

### Post by craigsharp on 2007-05-01
Hi,  I just got through installing MythTV and I can't seem to get my Motorola 62something to work.  When I try and watch live tv, it says, MythTV is already using all available inputs for the channel you selected... and so on.  So, double checked my settings,  all was right according to the HowTO I found here.  I checked my Port and Node setting, all was right.  I even triple checked after no luck the second time.  I need help.  I didn't find any other posts that gave me any help.  

I'm not sure what model number it is,   62XX.  It's the one with DVI and NOT HDMI.
I know for a fact that my firewire is active on my STB.  I was able to record a show using my Apple Powerbook about 7 months ago.

Thanks
Craig

---

### Post by superm1 on 2007-05-01
In the recent past (1-2 weeks), some providers have been switching the status of firewire recordability for their STB's.  Go into the diagnostics menu and determine the status of 5C and CCI for the channel you are attempting to record.  If things are clear there, we need to bring major idiot (the author of the firewire howto) into this thread.

---

### Post by craigsharp on 2007-05-01
The only Diagnostics I was able to get into was a grey screen that had my Video Output, ie 4:3 and so on, and it also had options for Closed Captioning.
I looked on Cox's website for how to get into diagnostics with no luck.

---

### Post by craigsharp on 2007-05-01
I'm sorry, but the model number is 6412 and not a 62xx model.  Is there anyway to get this to work with mythtv?

I just realised that.

---

### Post by superm1 on 2007-05-01
This series box should still be fine (provided 5C/CCI are OK).  On my last firewire capable box (6200 series), i got into the diagnostics screen by pressing OK on the remote right after pressing power off on it.  I'm imagining it should be very similar (if not identical) on the 6400.

---

### Post by craigsharp on 2007-05-01
I found it, I checked around and I saw in one of the menus it said CCI 0x00 and when i went to the next page it showed it as 0x02.  I checked the 5c and it showed 0. Also this was odd, i saw that it said 1394 I/O Installed, But 0 active ports. I know that the ports are active because of my  plugreport showed host 0 node 1.  Then my p2p test failed with near flying colors so i tried broadcast and they passed 100 percent.  I'm not sure what else to try.

---

### Post by majoridiot on 2007-05-01
as superm1 pointed out, many cable companies have been doing questionable things with the EMI settings 
of their streams... notably turning on CCI 0x02, which effectively kills firewire output on "non-compliant" 
devices (read: *not* manufactured by one of the few companies that hold a monopoly on the 
hardware).

i'm fighting the exact same issue with my cable provider, insight, who turned off the firewire tap for **all**
digital and HD channels in at least 3 states last friday morning. (IL, IN and KY if you were wondering).

they are also *apparently* doing something strange with other EMI flags as well... as i noticed last night 
that the firewire connection to **anaolg** channels is now very, very flaky. i suspect they have done a 
firmware upgrade of these motorola boxes and/or are fiddling with the EMI bits to confuse the issue.

in any event, this is **against FCC regulations** as *all* channels on the "basic tier of service" are to be 
broadcast 0x00 (copy freely) to allow streaming to *all* 1394 devices, whether they are "compliant" or 
not.

i have the same series box you have and mine works best in broadcast mode, so you are on the right track.

feel free to pm me if you like- or check in at #ubuntu-mythtv on irc, as there are a few firewire guys that 
hang out there.

the upshot is that the conglomerates are absolutely gutting the spirit of "fair use" in the quest of maintaining
their *hardware* monopoly. :(

folks think this is a DRM and copyright protection issue and it isn't- the hardware manufacturers are as 
complicit as the MPAA, et. al.

---

### Post by craigsharp on 2007-05-01
Thanks for the help.  I'm about 99.9%positive that the channel I have it starting on is non encrypted.  When I'm MythTV Backend Setup and I go to Channel Editor and then down to channel scanner it shows "failed to open the card" and if i try and change any of the settings, it says Programmer Error, See Console.  I checked my Log file  and all it says ```
2007-05-01 05:24:48.460 FireChan, Error: Unable to get handle for port: 0
ERROR: no valid capture cards are defined in the database.
Perhaps you should read the installation instructions?
```

I've double checked everything and all should be right for my setup.

Is there anything I can do to get my firewire ports active?  Like call COX and get them to send a new box or upload it with a different firmware?  I know that per FCC it is illegal not to have a firewire port active, Is that something I can bring up with them?

If you have anything more, PLEASE let me know.  I appreciate all help

---

### Post by craigsharp on 2007-05-01
Is there a PVR Card that has CableCARD that works with MythTV?  I don't want to lose my movie channels if at all possible.  I guess I could put my DVR in my bedroom for my movies, but that would defeat the purpose of setting up mythTV.

---

### Post by craigsharp on 2007-05-01
anybody?

---

### Post by majoridiot on 2007-05-01
first, you are better off NOT calling your cable co.  that just seems to add to woes. :(

from the errors, it looks like something got corrupted on the firewire setup.  try deleting it, exiting mythtv-setup
and then running setup again to confingure a new firewire connection.

---

### Post by superm1 on 2007-05-01
At that note, make sure that your cable box still has the same port and node assignments.  Across a reboot, if they changed for whatever reason - MythTV won't know, and there will be troubles if it is indeed accessing the wrong port.

---

### Post by craigsharp on 2007-05-02
I tried that and it didn't seem to help.  I might try installing a spare firewire card I have laying around and retry it then. It'll be a while till I can. I just got off work and I'm gonna sleep for 6 or so hours. and then i'll try it.  Also, while Im still up, I also have a 2524 in my room so my wife and I can watch tv and movies.  I've read where I could plug that into a pvr and use a serial cable and changer commands to use it.  I know I wont get a true digital feed, but I don't have a HDTV (yet).  Will that work? once again thanks.
Craig

---

### Post by majoridiot on 2007-05-02
i'm not sure about that model specifically, but the info on serial changers is here:

[https://help.ubuntu.com/community/MythTV_External_Channel_Changer#head-ba90074522cba8ce07b138da78e92567b8e1e56c](https://help.ubuntu.com/community/MythTV_External_Channel_Changer#head-ba90074522cba8ce07b138da78e92567b8e1e56c)

it *should* work ok to run the output of that stb into a capture card.  just make sure to set the card's start 
channel to the output channel of the stb- likely 3 or 4.

as to your firewire problem, is it giving you the same error after deleting and re-adding the firewire tuner?  if so,
you might try installing phpmyadmin and tring to repair the database.  you can find phpmyadmin instructions here:

[https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty](https://help.ubuntu.com/community/MythTV/Install/WhatNext/Feisty)

if that is the only error, it is not specific to firewire itself, but the configuration.  if you pm me here, i would be happy
to schedule a troubleshooting session with you in irc.

---

### Post by craigsharp on 2007-05-02
Thanks for the help so far.  I'm not going to be able to work on it until tomorrow.  I will try and repair the database and i'll try and remove it and add it again, I've been having small problems with my motherboard, I think i'll try and put a firewire card in a try it out, just to make sure it's not my mobo.
I'll get back to ya tomorrow and If it doesnt work, I'll get in touch with ya for TS session in irc.

Thanks

---

### Post by craigsharp on 2007-05-05
Sorry for the long wait,  but I still have been unable to get my stb to work with firewire,  oh well.  ::( 
I did, however, purchase a pvr150 AND!!! a pvr 500.  With my dvr stb I can record 4 shows and still be able to watch 1.  I'll be needing a lot of :popcorn: now.   I want to thank all of you for trying to help with my problem, even though my stb is crapped out when it comes to firewire.

Thanks
Craig

---

