---
title: "Unable to get program listings or watch TV on Mythbuntu 10.04"
date: 2010-05-02
forum: Mythbuntu
---

### Post by SquareRootofBlue on 2010-05-02
When I select the watch TV option I get the following error:

Error: Mythtv is using all inputs, but there are no active recordings?

It also failed when I tried to do the channel scan during setup. I've tried plugging the aeriel into both ports on my Hauppage DVB TV card-it made no difference. The specific model is: Hauppauge WinTV Nova-TD 500 Dual digital DVB-T PCI TV Tuner card.

This is a clean install (front and backend) on a new machine and I've never tried setting up Mythbuntu before and as there are quite a lot of technical settings I may well have overlooked something but don't know what. Any advice would be appreciated.

---

### Post by LowSky on 2010-05-02
i'm having the same issues.I don't think its the card, its the MythTV version included with 10.04. I hade to enter the channel data by hand, its the only way to get it to work with mythconverg. Thank goodness Schedules Direct lets you see the channel ID's.
I have the Hauppauge WinTV HVR-2250 Tuner, which is seeing the same issues but worked fine last release. My recommendation is to go back to Mythbuntu 9.10 as 10.04 uses a devepment version of MythTV and not a stable version according to the MythTV developers.

---

### Post by tgm4883 on 2010-05-02
Make sure you went though each setting in mythtv-setup.

---

### Post by Zilax on 2010-05-04
I also have this problem with the HVR-1600 and a fresh install. Like the original poster, this is my first attempt with Mythbuntu or even MythTV. It must be some newbie mistake, as going back to 9.10, as you suggested, did not change the symptoms at all. 

If I ever puzzle it out, I'll post back.

---

### Post by kasulstyls on 2010-05-04
I have this same problem. only thing i can see is the video source losing the schedule direct listing on the backend. For me to get it working, I will do a:
1. reboot --  for some reason you just cant do steps 2-5. 
2. after reboot exit mythfrontend, 
3. start the mythbackend setting and go to #3 ( video source ). 
4. scroll down to retrieve lineups from schedule direct then finish.
5. exit the backend and start mythfrontend. 
You should now have TV... until you reboot again. 


I have noticed that once you leave the backend the schedule direct location information is gone again. 

This is not a real fix but just what i found for me to get it working. I am hoping that when myth is fully release, it will be fixed for me. 

mypost
[http://ubuntuforums.org/showthread.php?t=1467656](http://ubuntuforums.org/showthread.php?t=1467656)

Kas....

---

### Post by Zilax on 2010-05-05
My issue turned out to be not properly connecting the Video Source to the Tuner input. There were only two options in the list and the second option (the correct one) lined up perfectly with a line of text in the background. (I was using the mouse) On my screen the drop box outline is quite faint and my eyes did not register the presence of the second option. Had I been using the remote, I probably would have seen the option.

I also selected the wrong type of card for my Hauppauge. 

The next thing for me is to improve my reception, but that's another story.

---

### Post by chipppy on 2010-05-07
Good Morning

I have recently run into this problem on my 9.10 box.  
Out of interest 9.10 uses 0.22 which is also a d evelopment build of MythTV, that is why there are a few issue with vob files.
I havent been able to fix this up yet but I think it has something to do with the way I have my schedule setup as when I run my program guide via a www import it kills my TV and brings up the 
Error: Mythtv is using all inputs, but there are no active recordings
but if I get my program guide via transmitted then it works fine.

hope this helps someone work out the error.

cheers
chipppy

---

### Post by SquareRootofBlue on 2010-05-08
I did a clean install of 9.10 and the channel scan completed, and I can now watch TV-although everything's in black and white-the only colour I've seen is the red in the American Megatrends BIOS logo. This was the same on 10.04. And it still timesout when trying to play DVDs but the title problem seems to be solved.

---

### Post by tgm4883 on 2010-05-08
> **SquareRootofBlue said:**
> I did a clean install of 9.10 and the channel scan completed, and I can now watch TV-although everything's in black and white-the only colour I've seen is the red in the American Megatrends BIOS logo. This was the same on 10.04. And it still timesout when trying to play DVDs but the title problem seems to be solved.

Sounds like you might have a PAL/NTSC issue (wrong one selected)

---

### Post by SquareRootofBlue on 2010-05-09
Thanks tgm4883, I suspected this myself and had already changed it from NTSC-M to PAL-I but it didn't make any difference. Checking the xorg.conf file, however, had the old entry in it, either the settings hadn't been asved after I made the chagne or it didn't update the xorg.conf file. Changing it manually worked. I still have some other unrelated issues but I'll deal with those in other threads.

---

### Post by JamesNorris on 2010-05-09
> **SquareRootofBlue said:**
> When I select the watch TV option I get the following error:

Error: Mythtv is using all inputs, but there are no active recordings?

It also failed when I tried to do the channel scan during setup. I've tried plugging the aeriel into both ports on my Hauppage DVB TV card


I've upgraded from 9.10 and after having to change my MySQL port numbers in the backend setup (which seemed to change itself during the upgrade) I, too, am having this problem. 

I have a Hauppauge Nova-T set up as a "DVB DTV capture card (v3.x)" 
It has sucessfully managed to pull the channel list, but won't fetch the listing data and I have the "Mythtv is using all inputs, but there are no active recordings?" error as well. 

I've pasted console output of what I believe is the error below...


```
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2010-05-09 18:35:54.120 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.121 MythSocket(1dfe200:9): Protocol error: '>' is not a valid size prefix. 89 bytes pending.
2010-05-09 18:35:54.121 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.121 Error rescheduling id -1 in ScheduledRecording::signalChange
2010-05-09 18:35:54.122 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.122 MythSocket(1dfc5b0:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.122 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.
2010-05-09 18:35:54.123 MythContext: Connecting to backend server: 127.0.0.1:3306 (try 1 of 1)
2010-05-09 18:35:54.123 MythSocket(1e01d70:9): Protocol error: '>' is not a valid size prefix. 58 bytes pending.
2010-05-09 18:35:54.123 Protocol version check failure.
			The response to MYTH_PROTO_VERSION was empty.
			This happens when the backend is too busy to respond,
			or has deadlocked in due to bugs or hardware failure.

```

Edit: I'm using .23-fixes from the Avenard repos.

---

### Post by thor999 on 2010-05-16
I just recently installed this on a test machine w/ a SSD, and am having the same problem, along w/ the same log entries as the post above. This machine has ran many forms of MythTV and Linux w/ no problems, and am using a pcHDTV5500 tuner card.

---

