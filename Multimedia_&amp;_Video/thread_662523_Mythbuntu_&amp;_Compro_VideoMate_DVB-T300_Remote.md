---
title: "Mythbuntu &amp; Compro VideoMate DVB-T300 Remote"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by angelman99 on 2008-01-09
Mythbuntu is great, I especially like the Mythbuntu Control Centre, it has a very polished feel and is easy to use for newbies to Linux such as myself.

My problem is that my standard remote that comes with the Compro VideoMate DVB-T300 is not an option in the list of remote controls.

Has someone gotten this remote to work with Mythbuntu?
(If you have can you please post your lirc.conf??? file and where to put it. The where to put it is especially import to us newbie users :-) ) (and I'm only guessing that Mythbuntu uses lirc to talk to the remote control :confused: )

Is this card/remote sold under another name in other countries?
I've tried the one listed for card=70 (Prolink Pixelview PV-BT878P+) which didn't work.
(I've randomly tried a few of the others - no result ](*,) ).
I connected my old hard drive and checked that the remote was working (in Windows :-( ) and yes it's working fine there.

This is the last step I need to do before my Mythbuntu PC makes its grand entrance into my lounge room \\:D/

---

### Post by simgrant on 2008-07-19
How did you get it to work at all? I couldn't.

---

### Post by angelman99 on 2008-07-19
Hers's what I did. I haven't tried it with the latest distro though. Been busy.

[http://ubuntuforums.org/showthread.php?t=402783&highlight=compro](http://ubuntuforums.org/showthread.php?t=402783&highlight=compro)

---

### Post by simgrant on 2008-07-19
Thanks for replying. I found this thread already in the meantime but can't make it happen. I have gotten as far as getting it to channel scan but it won't lock on to any channels. Seems to be a common problem. I tried updating the firmware to no avail. I haven't yet tried updating the V4L drivers.

  What was the final detail that fixed it for you  in the end?

I want to get this working because Mythbuntu seems to fix issues I used to have with Linux and component TV out. I tried some DVD's before with VLC and the picture quality is streets ahead of tv out in windows and even better than my DVD player. Just got to get the soundcard working also but one step at a time.

Regards.

---

### Post by simgrant on 2008-07-19
Addendum: Managed to get Kaffeine to scan in just enough channels to watch all the major networks. Still doesn't work on MythTV though.

---

### Post by angelman99 on 2008-07-19
Well done :)

Sorry for beeing such a newbie myself, but I'm pretty sure if you "find" the Kaffine channel file ie the file it creates where it stores those channels it's found, you can then manually or place that channel information into the right file for MythTV. I can't remember if it needed to be converted first (look up scan and DVB-tools). Oh you need to make the channel scan delay in MythTV longer ie how much time it spends waiting for lock before moving to the next channel, I think it's set to 5,000ms you need to up it to like 50,000ms, the setting is accessable from the GUI MythTV setup screens.
But hey at least you know now that the card will actually work with your equipment, I spent months chasing my tail with a motherboard/chipset/tuner card combination that was never going to work (ie as soon as I stuck the card into another PC fired it up and the Ubuntu even autodected the card correctly!!!). I've shelved the media PC for the past couple of months (using a boring PVR), I currently putting away funds to buy a new dual HD tuner card with onboard mpeg4 (and stupid me it looks like it's going to be the Compro card :confused: ) I should know better shouldn't I. But I can see this new card being VERY popular and hence will get support.

---

### Post by simgrant on 2008-07-19
Thanks angelman99, will try that. If I can get this to work and MythTV is as pleasant to use as they say then I will build my Dad HTPC.

  He has bought two supposedly good PVR's, both turning out to be disastrously buggy and user-unfriendly. He is a big fan of Linux so would be delighted to use MythTV if it can be made to work.

  Of course if I build him a HTPC I will definitely make sure to use hardware proven to work. However I am using hardware I already have first to make sure I can configure it to be user friendly and remote controllable.

  Hopefully I can sort this, then figure out getting sound card to work and output 5.1 analogue, then finally seamlessly replace MythTV internal DVD play with VLC (IMO the best DVD player for home theatre). Then I think it will definitely have to replace XP for watching movies through my TV.

Regards.

---

