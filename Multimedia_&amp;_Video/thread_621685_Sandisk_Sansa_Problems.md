---
title: "Sandisk Sansa Problems"
date: 2007-11-23
forum: Multimedia &amp; Video
---

### Post by JParkus on 2007-11-23
I get the following error at the end of my readout of mtp-setect


libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   RIFF WAVE file
   Microsoft Windows Media Audio
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)


Can anyonetell me what this means and how to fix this
I will only randomly show up as a drive big problem if i want to add music

---

### Post by sirdilznik on 2007-11-24
> **JParkus said:**
> I get the following error at the end of my readout of mtp-setect


libmtp supported (playable) filetypes:
   ISO MPEG-1 Audio Layer 3
   RIFF WAVE file
   Microsoft Windows Media Audio
Unable to acquire device certificate, perhaps this device does not support this
Error 2: PTP Layer error 02ff: get_device_unicode_property(): failed to get unicode property.
Error 2: (Look this up in ptp.h for an explanation.)


Can anyonetell me what this means and how to fix this
I will only randomly show up as a drive big problem if i want to add music

Hmmm....  I have a Sansa e280 but I've never tried to connect it using MTP, I've always used MSC mode and just drag and dropped all my music into the player (even before when using the original firmware, these days I use Rockbox).  Have you tried in MSC mode?

---

### Post by Robertjm on 2007-11-24
Apparently, they have a "new" version of the Sansa e280 player, with is version 2 (says v3.xx on the device).

This took the USB Mode setting from the menu. Someone posted instructions on how to change the setting, but darn if I can get it to work.

Right now I connect mine up to Feisty Fawn, but no icon appears on the desktop. I will tell you though that the Sansa's screen keeps flashing about the database being updated, which makes no sense.

Apparently Sansa has fallen into the Windows trap and isn't allowing us to change from MTP to MSC? This blows big time!!

Robert

---

### Post by sirdilznik on 2007-11-24
Wow, that sucks.  I'm glad I have an "older" model.  I wonder if the change is in the hardware or in the firmware, because if it is a firmware change (most likely is) then you could just get an older version of the firmware,

---

### Post by Robertjm on 2007-11-24
Not sure. I just got off the phone with Sansa Tech. Support and he told me how to, supposedly, switch modes. 

1 - Make sure player is on
2 - Make sure the Lock button is locked
3 - Press and hold the rewind button (the one at 9 0'Clock)
4 - Connect the USB Cable

At this point you will get a "connecting" msg and then it should change to "connected."

Unfortunately, mine just says "Connecting" and then "Refreshing Database" and repeats this every minute. It never connects. Wasn't worth busting the guy's chops since he did try to give me support even though it wasn't officially supported. 

I asked me about downgrading firmware, but he said it can't be done, and the last thing I want to do is brick it on my first day. :)

Will play more with it once I get home from the Sharks' hockey game.

Later,

Robert

---

### Post by sirdilznik on 2007-11-24
Maybe check around Rockbox.org a bit.  Even if you don't intend to use Rockbox (alternative firmware) like I do, I seem to remember (it was a long time ago) that the install process involved changing the original firmware over to MSC mode, so maybe there is some mention of this.  I'll check the site when I get a chance and post a link if I find anything.

Yeah I would definitely not do anything drastic since you just got the player until you find out more.

---

### Post by software pimp on 2007-12-22
I got to the build part of rockbox and then it all became "                           "
I know i can use msc mode but that takes away from the playlist that i luv so so much. 
thanks

---

### Post by Purplecatty on 2007-12-25
I have Sandisk Sansa View (newer version released in October 2007).  I got it reconized by Gusty Gibbon.  I followed the instruction what the guy on this post:

[B]Robertjm  	
Re: Sandisk Sansa Problems
Not sure. I just got off the phone with Sansa Tech. Support and he told me how to, supposedly, switch modes.

[U]1 - Make sure player is on
2 - Make sure the Lock button is locked
3 - Press and hold the rewind button (the one at 9 0'Clock)
4 - Connect the USB Cable[/U]

At this point you will get a "connecting" msg and then it should change to "connected."

Unfortunately, mine just says "Connecting" and then "Refreshing Database" and repeats this every minute. It never connects. Wasn't worth busting the guy's chops since he did try to give me support even though it wasn't officially supported.

I asked me about downgrading firmware, but he said it can't be done, and the last thing I want to do is brick it on my first day.

Will play more with it once I get home from the Sharks' hockey game.

Later,

Robert[/B]


**_ It works for me_**.  It did pop up window showing files! (Also I clicked "Places--Computer--SanDisk Sansa View :Sansa View folder).  So I haven't tried transferring music or video files yet cuz it's my daughter's new mp3 player for Christmas.  I'm am just learning tho.
Merry Christmas!:lolflag:


Thanks!
Catty

---

### Post by Robertjm on 2007-12-25
That's awesome!! There is hope out there for the new Sansa owners. However, I'm not one of them.

I ended up returning my Sansa e280 back to Costco and purchased a Sony NWZ-s618 at the San Francisco Sony-Style store.

When plugged in It popped up immediately. I did have to upgrade my libMTP, which in my case meant jumping up to Hardy Heron, but ever since upgrading it works fine with Amarok.

Truthfully there were two small niggling issues.
1 - Have to always press connect in Amarok, which then unmounts the device for the rest of the computer and I get the unsafe unmount error msg.
2 - When removing files off the device it leaves empty folders it created when I originally transfered stuff over.

Like I said, minor issues, but two that I hope can be rectifiied eventually. 

Merry Christmas to all!

Robert

---

### Post by Purplecatty on 2007-12-27
(off posting)

I am wondering are there MP3 music download for Linux.  I tried to run Best Buy Rhashody via Wine and it installs but won't run.  I have firefox (windows only) installed in Wine previously.  Am I missing anything in Wine to get Rhapshody working?  If not then what do you recommend MP3 software that would work for Linux or under Wine. I saw some are free legal mp3 download too.  If not any then I could run VirtualBox w/ XP installed then use it from there.

Does Linux have Video converter to convert it to MPEG-4 and 320X240 resolution.  I downloaded "Any-video-converter" software and installed it thru Wine and not working.  I would love to covert Youtube video into MP4 format.

Basically, I just want immerse in Linux and out of Windoz.  I know it's not 100% ready to be a desktop yet but gotten sick and tired of M$ux..   :lolflag:

Give me suggestions!!
Thanks
Happy New Year!
Catty

---

### Post by jElLyBeAnS1991 on 2007-12-29
> **Robertjm said:**
> 
When plugged in It popped up immediately. I did have to upgrade my libMTP, which in my case meant jumping up to Hardy Heron, but ever since upgrading it works fine with Amarok.

Truthfully there were two small niggling issues.
1 - Have to always press connect in Amarok, which then unmounts the device for the rest of the computer and I get the unsafe unmount error msg.
2 - When removing files off the device it leaves empty folders it created when I originally transfered stuff over.


Robert

I have a Sansa Sandisk e280 and I just can't figure out how to connect my player to Amarok. How do you mount it? 

Thanks!! :confused:

---

### Post by freddybob on 2007-12-30
I'm about to upgrade my wife's PC from WinXP to Ubuntu but she has a Sansa e280 and I cannot find a way to get Amarok to work with it.  This is a huge sticking point.  Please help!

---

### Post by Robertjm on 2007-12-30
***[COLOR="Red"]jEILyBeAnS 1991[/COLOR]***:
Is it the v2 or the older v1? If the former, you CANNOT currently get it to work with Amarok. That's why I ended up returning mine. They changed the firmware and perhaps even some hardware so it doesn't play nice with libMTP. They're working on it over in the libMTP group, but no go so far. At least none that's been said on the mailing list.

If you've got the latter, then there is a setting on one of the menu options where you can change USB mode from MTP to MSC. Look for "USB MODE" in one of the menus.This basically creates it as a mass storage device. While it works with linux, you loose all the any DRM'd music services you may be currently using. BEWARE!! THIS WILL WIPE ANY MUSIC OFF THE e280 THAT IS INSTALLED AT THIS POINT!!!!

You may need to upgrade to libMTP 0.24 for it to properly work in Amarok, which may require you to backport if you're not on Hardy Heron. As I didn't get mine working (v2) I don't know for sure.

If its in MSC mode there should be nothing to do special in Amarok. If Amarok is open when you plug the device in, it will detect the new device and give you options on how to use it (auto-connect, etc.)

***[COLOR="Red"]FREDDYBOB[/COLOR]***:
 If your wife's player is the v2 (probably is if you bought it in the last few months) than there is nothing that can currently be done. The best thing would be to subscribe to libMTP-discuss mailing list and keep an eye on the discussions that have Sansa or e200/e250/e260/e270/e280 in the subject line. 

[https://lists.sourceforge.net/lists/listinfo/libmtp-discuss]("https://lists.sourceforge.net/lists/listinfo/libmtp-discuss")

Hope that helps!

Robert

> **jElLyBeAnS1991 said:**
> I have a Sansa Sandisk e280 and I just can't figure out how to connect my player to Amarok. How do you mount it? 

Thanks!! :confused:

---

### Post by freddybob on 2007-12-30
Thanks Robert.  It's the older e280 she has (the one with the menu option to switch between MTP and MSC).

In MSC mode it appears on the desktop and so files can be dragged to it that way but it does not appear in Amarok.

In MTP mode it does not appear on the desktop and Amarok crashes whenever I ask it to connect.  Maybe I need to update my libMTP as you suggest,

---

