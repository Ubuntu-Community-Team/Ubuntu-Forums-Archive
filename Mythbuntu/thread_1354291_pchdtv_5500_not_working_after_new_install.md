---
title: "pchdtv 5500 not working after new install"
date: 2009-12-13
forum: Mythbuntu
---

### Post by itlarson on 2009-12-13
I just did a fresh install with 9.10.  I restored the database, but my tuner cards are not working.  When I rescan, I get "possible channels" instead of the call signs.  I assume this must be related.  I have re-done the input connections, but still the same result.

---

### Post by itlarson on 2009-12-13
Please help! Playback of recordings is working well, but when I try to play live TV I get the "playback starting" screen, then I am immediately kicked back to the frontend.  New recordings are just blank files.   Deleting  the cards and source, and recreating them gives the same result.  I am setting them up as dvb cards at /dev/dvb/adapter0/frontend0 and/dev/dvb/adapter1/frontend0.  They no longer show up as /dev/dvb0 and 1, which is my memory of where they used to show up.  This seems to be something with the input connections, as the scan turns up stations, but only can identify them as "possible" and "probable"

---

### Post by itlarson on 2009-12-14
Anyone?

---

### Post by jlagrone on 2009-12-15
I think it's just the way the new channel scan works.  Are you using an antenna or cable?  I use cable and don't get the call signs automatically because the cable company obfuscates them or just doesn't broadcast them, I haven't tried the new channel scan with an antenna so that may or may not be the same.  I get the same possible/probable channels.  I added them all and painstakingly went through all of them, so channels would lock but never get a picture, or exit, or crash the frontend.  It seems these are audio only channels or just blank channels (which I personally don't want anyway).

Here's the steps I took (It's much easier with mythweb if you're using it)

1.  Do channel scan

Add all the channels, on the channels that it says are unused or not broadcasting or anything like that, do not delete them.  Add them if you can, set them as invisible if you can't add them.

2.  Set all channels as visible (I think you can do this in the channel editor, I did it in mythweb) and note the default starting channel (let's say it is 4).

3.  Try to watch tv.  

If it doesn't work, as you're experiencing.  Change the default starting number.  If you're using mythweb, just delete channel 4.  Then rename another channel to 4.  Try again.  Repeat until a channel works.

If it does work, make a note of the channel number so you don't accidentally delete it.  Try the next channel.

4.  Delete all the unwanted/bad channels.  Try to rename the good ones appropriately, etc.

This is obviously pretty painstaking and if you are getting a lot of channels in your scan, I suggest looking at your lineup here [http://www.silicondust.com/hdhomerun/channels](http://www.silicondust.com/hdhomerun/channels).  That will give you a channel number for a channel you should have.  Start by just scanning one of those channels and maybe a few before and after it to see if it will work so you don't waste a lot of time.

Another thing to check if watching tv just crashes is that the default channel actually exists, mythtv-setup will warn you if it doesn't when you try to exit

---

### Post by tdcarlo on 2009-12-15
> **itlarson said:**
> Please help! Playback of recordings is working well, but when I try to play live TV I get the "playback starting" screen, then I am immediately kicked back to the frontend.  New recordings are just blank files.   Deleting  the cards and source, and recreating them gives the same result.  I am setting them up as dvb cards at /dev/dvb/adapter0/frontend0 and/dev/dvb/adapter1/frontend0.  They no longer show up as /dev/dvb0 and 1, which is my memory of where they used to show up.  This seems to be something with the input connections, as the scan turns up stations, but only can identify them as "possible" and "probable"


That's what I got with my 5500, "possible channels".  I inserted them, using the suggested numbers.  The channels looked fine.  I did have to manually put in the channel identification numbers to get the schedule direct listings to work.

---

### Post by Skybolt83JL on 2009-12-15
I found the easiest way to get the channels for cable is to use a TV with a QAM tuner. My Visio's channel scan finds everything that's unencrypted. I then preview the channels and write down the digital channel number and the call sign. Then for each digital channel I want, I let Myth scan only that channel. It shows an identifier in which the subchannel number is visible, so I manually enter the channel and subchannel number. (You have to ignore existing "off air" channels and carriers or it will delete the previous entries.) Then use the channel editor to add the callsign, cable channel, and schedule code number.

Not elegant, but it works...

---

### Post by itlarson on 2009-12-15
Thanks for the replies- I am confused as to where manually add channels.  In two previous installs I have never had to.  I am using the system for over-the-air not cable.  During the scan the signal strength never gets above zero.  Between this and the fact that the cards don't show up in the usual place in /dev, I am thinking something is wrong with how they are being recognized, and I don't know how to proceed.

---

### Post by itlarson on 2009-12-22
For other people's reference-  this was a file permission issue.  Because Mythtv always buffers live tv, the directories you set up as storage groups must be writable or live tv won't work.  Obviously recording won't work either if this is the case.  I was reusing one partition, and had created a new one on a new drive, but neither were writable by the back-end.  To me it seems myth setup should check for this when you add the directories as storage groups.

---

### Post by Meph1st0 on 2010-05-18
I get the feeling I'm experiencing the same problems that you were in this thread.  I too am using two of the pcHDTV 5500 cards and after upgrading to 9.10 they've stopped working properly.

Here's the thread that I've started:

[http://ubuntuforums.org/showthread.php?t=1486149](http://ubuntuforums.org/showthread.php?t=1486149)

Did you ever get this solved?

---

### Post by itlarson on 2010-05-20
All I did is set the permisions on the storage directory to writable by everyone.

---

