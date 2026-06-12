---
title: "Hauppauge 1250 + cable box + MythTV; anyone get this to work. Firewire card?"
date: 2011-11-04
forum: Multimedia Software
---

### Post by Ohmn on 2011-11-04
Okay thanks to a kick butt howto 

[http://ubuntuforums.org/showthread.php?t=1648472](http://ubuntuforums.org/showthread.php?t=1648472)

I have the 1250 installed and recognized by MythTV. The thing is, all I want to do is take the feed from the cable box through the coaxil cable and be able to record whatever channel the cable box is set on. I did this in vista, I only get one channel when the cable box is on and I scan. It is channel 3 and it says it is analogue. I don't really care because channel 3 is whatever channel the cable box is tuned to.  This is all I want, so if I need to record something, all I have to do is set the cable box to the channel and set the windows software for the 1250 to tape channel 3 for the time the show is on. 

In Ubuntu 11.10, when the cable box is on, I don't get any channels in MythTV, not my beloved channel 3 that is whatever the cable box is set to. So has anyone done this, is it possible? Currently I am dual booting with Ubuntu and vista so I know all the hardware works. 

Thanks

Oh, I read that sometimes you can record with a firewire card. My cable box has a firewire port and I have an older firewire card, so if someone has done the above with that would love to hear before I embark on a fruitless adventure.

---

### Post by poe503 on 2011-11-06
You're welcome regarding the howto. :)

The analogue function in the 1250 card is not supported in linux, just digital and QAM.  See this webpage: [http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250]("http://linuxtv.org/wiki/index.php/Hauppauge_WinTV-HVR-1250"); it says so right at the beginning.  

There are plenty of Hauppauge analogue cards that are supported by linux and you can pick them up for a song since most folks now have to tune for digital (ATSC) and not analogue (NTSC). 

I read that some cable companies retained the NTSC standard when the US changed the broadcast standard so that their customers didn't have to change their equipment.

---

