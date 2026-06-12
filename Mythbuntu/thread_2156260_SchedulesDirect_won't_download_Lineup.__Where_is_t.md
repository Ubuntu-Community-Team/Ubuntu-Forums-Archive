---
title: "SchedulesDirect won't download Lineup.  Where is the &quot;mythdownloadmanager.ccp&quot; file??"
date: 2013-06-21
forum: Mythbuntu
---

### Post by tegwilym on 2013-06-21
I have had a problem and it seems I'm not the only one with this issue.
Scehdulesdirect won't download the lineup data when run on a fresh mythbuntu install 12.x.  I now it does work, since on my current install of Mythbuntu 9.04 (?) it works just fine.  All the hardware is the same, but I installed the latest Mythbuntu 12.4 and I can't get past the lineup download. 
It seems a common fix is to edit the "mythdownloadmanager.cpp" file to give it a longer time out rather than 10 seconds.
I want to try this, but I can't find that thing anywhere!
Does anyone know where to find the mythdownloadmanger.cpp file?? I've looked all over and it doesn't seem to be on my computer.  
Where is this file? The path is shown below. 

mythtv/libs/libmythbase/mythdownloadmanager.cpp
Help!
Tom

---

### Post by tgm4883 on 2013-06-21
> **tegwilym said:**
> I have had a problem and it seems I'm not the only one with this issue.
Scehdulesdirect won't download the lineup data when run on a fresh mythbuntu install 12.x.  I now it does work, since on my current install of Mythbuntu 9.04 (?) it works just fine.  All the hardware is the same, but I installed the latest Mythbuntu 12.4 and I can't get past the lineup download. 
It seems a common fix is to edit the "mythdownloadmanager.cpp" file to give it a longer time out rather than 10 seconds.
I want to try this, but I can't find that thing anywhere!
Does anyone know where to find the mythdownloadmanger.cpp file?? I've looked all over and it doesn't seem to be on my computer.  
Where is this file? The path is shown below. 

mythtv/libs/libmythbase/mythdownloadmanager.cpp
Help!
Tom

That is a C++ file that you would use when compiling mythtv.  What version of mythtv are you on (full version)? Are you using the mythbuntu provided mythtv-updates repo? I thought that was already pushed out to 60 seconds

---

### Post by tgm4883 on 2013-06-21
So this looks to have been fixed in 0.26 6 months ago

[https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531](https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531)

---

### Post by tegwilym on 2013-06-21
> **tgm4883 said:**
> That is a C++ file that you would use when compiling mythtv.  What version of mythtv are you on (full version)? Are you using the mythbuntu provided mythtv-updates repo? I thought that was already pushed out to 60 seconds

Yes. I'm running the latest Mythbuntu version that has a fresh install and I'm going through the setup.  I did download all the updates and think I did the other autoupdate option in the Mythcontrol center updates also.  Still not working.  It seems to sit for about 10 seconds then the window goes away and there are no channel lineups downloaded.  It's worked fine on all the others that I've used over the last 4 years or so.  This is the first time I ran into problems.   
I did download the version a couple months ago.  I wonder if they have changed things since?  But the updates should have taken care of that.   

Where is the mythtv-updates repo?  Just to idiot check myself to see if I'm in the right place.  :-)

Thanks for the reply!

Tom

---

### Post by tegwilym on 2013-06-21
> **tgm4883 said:**
> So this looks to have been fixed in 0.26 6 months ago

[https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531](https://github.com/MythTV/mythtv/commit/bcc459fa2893f65c1debe9a7f976d3c23e865531)

Hmm.....was that possibly included in the .ISO or updated later?

---

### Post by tgm4883 on 2013-06-21
> **tegwilym said:**
> Hmm.....was that possibly included in the .ISO or updated later?

That would be updated later. What is the output of 

```
dpkg -l | grep mythtv
```

---

### Post by tegwilym on 2013-06-22
> **tgm4883 said:**
> That would be updated later. What is the output of 

```
dpkg -l | grep mythtv
```

Hey!  I got it working.  I went into SchedulesDirect and edited the lineup.  I removed the crap that I don't watch and that shortened the list down enough that it would download ok and not timeout.  
That seems to be the fix.  

Hopefully this info helps someone else. 

Tom

---

