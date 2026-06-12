---
title: "video playback on 10.4/0.23"
date: 2010-05-16
forum: Mythbuntu
---

### Post by kcaj on 2010-05-16
I'm using an LCD monitor with 1024x768 resolution. With 10.4 and 0.23 it wants to display everything full screen. Horrible display for HDTV.

I initially installed Mythbuntu 9.10 x86_64 with mythtv 0.22 from and iso and the video playback worked fine, it left black bars on the top & bottom but kept the video in the proper aspect.

Then I did the online upgrade which seemed to go well but...

With 10.4/0.23 it doesn't seem to matter which playback profile I use it wants to use full screen. (utilities->setup->tv settings->playback->3/8 playback profiles) 

ffplay will do the same thing unless I specify -x 1024 -y 756, then it will play normally.

I tried mplayer as well and I had to specify -vf scale=1024:576 to get the proper display.

Is this being caused by X or is it something in mythtv? Since 3 different programs want to do this I suspect X.

Thanks...

---

### Post by mike. on 2010-05-19
[COLOR=black][FONT=&quot]I have upgraded to the latest 10.04 LTS 32-bit release of MythBuntu by using a new (virgin out of the box) disk drive and noticed only one issue regarding recorded content’s aspect ratio.  [/FONT][/COLOR]
  
  [COLOR=black][FONT=&quot]The previous 9.10 release recorded the .mpg files at the native broadcaster resolution.  I see a mixture of different X and Y pixel counts in the files recorded in the /var/lib/mythtv/recordings directory.  Some of the popular recorded media sizes are 1920x1080, 548x480, 720x480, and several others.[/FONT][/COLOR]
  
  [COLOR=black][FONT=&quot]The 10.04 release seems to always record at 1920x1080 resolution independent of the broadcaster’s source format.  Old TV shows, like Hogan’s Heros, that are still being broadcasted at a very grainy 548x480 are small fields of video information with large black unused bands on top, bottom, left and right edges of the 1920x1080 *.mpg recorded file.  Consequently, during playback on a Samba mounted external video player or on the computer’s 1920x1080 flat screen monitor, I see all of the black field content rather than attempt to auto-resize the content to fit the playback screen.[/FONT][/COLOR]
  
  [COLOR=black][FONT=&quot]Another detriment of the 10.04 resolution issue is recorded file sizes.  Recording the same program on the 9.10 and 10.04 with the same quality setting (Normal) results in drastically different file sizes.  The older 9.10 release could record an old TV show at a data rate of 780 MByte/half hour.  The latest 10.04 release records the same show at a rate of 3.3 GByte/half hour (and a whole bunch of dark pixels surrounding the relatively small image in the middle).  I thought one of the attributes of the latest 10.04 release was the newest H.264 codecs that were both faster and more efficient at video compression.  My observations don’t align with these assumptions.[/FONT][/COLOR]
  
  [COLOR=black][FONT=&quot]Please help if you can…   Many thanks to all who try.[/FONT][/COLOR]
  



[B][U][COLOR=black][FONT=&quot]
[/FONT][/COLOR][/U][/B]
**_[COLOR=black][FONT=&quot]Software[/FONT][/COLOR]_**[COLOR=black][FONT=&quot]
**OS:** MythBuntu 10.04 LTS 32-bit installed on virgin HDD disk media[/FONT][/COLOR]
  **[COLOR=black][FONT=&quot]3rd Party Drivers:[/FONT][/COLOR]**[COLOR=black][FONT=&quot] downloaded and installed the Kernel Labs firmware support for Hauppauge Tuner[/FONT][/COLOR]
  **[COLOR=black][FONT=&quot]Misc:[/FONT][/COLOR]**[COLOR=black][FONT=&quot] Ran the Update Manager, all packages are at the current release revisions
 
 [/FONT][/COLOR]
  **_[COLOR=black][FONT=&quot]Hardware[/FONT][/COLOR]_**[COLOR=black][FONT=&quot]
**CPU:** Intel i7 860[/FONT][/COLOR]
  **[COLOR=black][FONT=&quot]Motherboard:[/FONT][/COLOR]**[COLOR=black][FONT=&quot] GA-P55A-UD4P LGA 1156 P55 ATX Motherboard
**RAM:** 4 GB DRAM
**Video Card:** ATI Diamond HD 4650 AGP 512MB DDR2
**HDD1:** 1.5 GB SATA 3Gb/s
**Tuners:** Hauppauge HVR-2250[/FONT][/COLOR]
  **[COLOR=black][FONT=&quot]External Media Player:[/FONT][/COLOR]**[COLOR=black][FONT=&quot] Western Digital Live TV connected to an old NTSC analog TV (4:3 aspect)[/FONT][/COLOR]

---

