---
title: "Mythbuntu and Soundgraph iMon Pad (PLEASE READ!!)"
date: 2009-10-27
forum: Mythbuntu
---

### Post by rdhaines1966 on 2009-10-27
I just finished installing Mythbuntu and have several questions.  I'm a novice at best as far as experience with Linux and more specifically Ubuntu.
 
After I finished the install the first issue that I ran into was not being able to RIP DVDs.  I installed the 64 bit version of Mythbuntu and did the install while NOT connected to the Internet.  There were some missing packages that I was able to install once I got the machine online and ultimately was able to get DVD ripping to work.  I'm ripping to ISO.  I assume this is the best quality.
 
I wasn't able to plug in the IMDB number to automatically fill in the metadata for the movies that I ripped.  It wouldn't let me type in the field using the keyboard.  Weird!  Maybe it only allows you to type with a remote control?
 
Now my issue is getting the remote control to work that came with my Silverstone LC20M case.  It doesn't say anywhere what the model of the remote control is, but as near as I've been able to tell it's a Soundgraph iMon Pad remote control.
 
I've found some information about it's configuration but I don't know what I need to do to configure this thing.  Can someone point me to a step-by-step guide?  Preferable one that assumes that the person doing the setup knows nothing about Linux or Unbuntu.
 
Also, I have made some general observations about the user interface in Mythbuntu.  Overall, I think it's pretty user friendly, however, there are some features missing that I would have expected to be there.  For example, movie sub menus.
 
Movies --> genre(comedy, drama, action, etc...)
 
Same thing basically with music. 
 
Music --> genre(rock, country, classical, etc.)
 
Also, music play lists.  Maybe this feature does exist and I just don't know how to configure it yet.  I have an extensive MP3 collection.  Around 40,000 songs.
 
Sorry to make this so long, but I have lots of questions.  I would really like to get this working using Mythbuntu but may have to look at using a Windows product instead.  Media Portal looks like one that may be pretty full featured.
 
Also, I see that Mythbuntu 9.10 is set to be released in a few days.  Should I wait and install that version?  I believe it will have MythTV ver. 0.22
 
Any and all thoughts and suggestions will be warmly welcomed.

---

### Post by mitchell2345 on 2009-10-27
I wasn't able to plug in the IMDB number to automatically fill in the metadata for the movies that I ripped.  It wouldn't let me type in the field using the keyboard.  Weird!  Maybe it only allows you to type with a remote control?

IMDB support is going to be dropped in .22.  The grabber violates thier TOS.  So it may not be working anymore.  .22 pull from thetvdb.org.
 
[B]Now my issue is getting the remote control to work that came with my Silverstone LC20M case.  It doesn't say anywhere what the model of the remote control is, but as near as I've been able to tell it's a Soundgraph iMon Pad remote control.
 
I've found some information about it's configuration but I don't know what I need to do to configure this thing.  Can someone point me to a step-by-step guide?  Preferable one that assumes that the person doing the setup knows nothing about Linux or Unbuntu.[/B]

This guide may help: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=907256&page=2](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=907256&page=2)
 
[B]Also, I have made some general observations about the user interface in Mythbuntu.  Overall, I think it's pretty user friendly, however, there are some features missing that I would have expected to be there.  For example, movie sub menus.
 
Movies --> genre(comedy, drama, action, etc...)
 
Same thing basically with music. 
 
Music --> genre(rock, country, classical, etc.)
 
Also, music play lists.  Maybe this feature does exist and I just don't know how to configure it yet.  I have an extensive MP3 collection.  Around 40,000 songs.[/B]

Mythvideo has some extensive changes in .22 but alot of these features i dont believe are there.  The music player is also very lacking.  MythTV core is TV/DVR functionallity and that is where the devs put thier time and it shows.  Many users will add a custom button in Myth to launch XBMC as its video/music ability are far greater.
 
**Also, I see that Mythbuntu 9.10 is set to be released in a few days.  Should I wait and install that version?  I believe it will have MythTV ver. 0.22**
 
I would work on .21 now.  You can always upgrade.  Most new features are going to be VDPAU (video accel w/NVIDIA) and MythUI (new themes) core functionality are pretty much the same.  

Hope this helps.

~Mitchell

---

