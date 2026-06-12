---
title: "Myth .21 digital channel problems"
date: 2010-04-04
forum: Mythbuntu
---

### Post by oldtincup on 2010-04-04
Hi

I am using Mythbuntu Intrepid.  I am having problems enteringg and displaying the digital channel numbers.

I have channel names that look like 124-5 which as you can see is 5 characters long.  In the on screen display for watching TV it will only let me enter 4 characters from the keyboard.  It will also only display 4 characters.  I can only get to these channels using the arrow keys, but since it only displays 4 characters I don't know which channel I am actually on. 

What am I doing wrong? How can I change this behavior? Do I need to ugrade to a newer Mythbuntu version?

---

### Post by klc5555 on 2010-04-04
> **oldtincup said:**
> Hi

I am using Mythbuntu Intrepid.  I am having problems enteringg and displaying the digital channel numbers.

I have channel names that look like 124-5 which as you can see is 5 characters long.  In the on screen display for watching TV it will only let me enter 4 characters from the keyboard.  It will also only display 4 characters.  I can only get to these channels using the arrow keys, but since it only displays 4 characters I don't know which channel I am actually on. 

What am I doing wrong? How can I change this behavior? Do I need to ugrade to a newer Mythbuntu version?

These are the actual channel and subchannel number that the cable company is transporting the broadcast in on. 

But you don't need to use these actual channel and transport numbers in tuning mythtv. Mythtv will internally use a four-digit code that you'll never see (except in file names) to uniquely identify identify each channel. You, in turn, assign more normal-looking virtual channel numbers to each of these that you receive, and these virtual channel numbers are what you will use in myth to change channels to and to record on.

How does this work? Let's say in LiveTV you pull up with your keyboard (maybe using the up/down arrows) some channel "32-124" that you know happens to be the Fox News Channel (for example). You would rather have this station on a channel number "41" the way a normal TV would.  When the station is on-screen, type "e" (for edit) and enter "41" for channel number, replacing "32-124" and it's done. Mythtv now has it at ch. 41 until you change it again or the day your database fries. The LiveTV "e" screen also allows you to edit the SchedulesDirect xlmtvid number, the channel name, and the callsign.

You can also do all this from the "channel editor" in the backend setup, if you prefer.

Just be careful not to double assign stations to the same virtual channel number --two ch. 41s, for example.

---

### Post by oldtincup on 2010-04-04
Yes.  But I wanted to have the channel match my television, which has a QAM tuner and uses the channel subchannel format.

---

### Post by klc5555 on 2010-04-04
Ah, sorry. Your first post didn't make that clear. Never heard of anyone wanting to do it that way before. 

But I think it's a limit of the OSD in 0.21 to display only 4 characters in the channel number. There doesn't appear to be any limit in actually tuning a longer number on the keyboard. At least I have no trouble dialing up five-character 118#5 on a keyboard in 0.21, which is the only 5-character channel in my own cable package that has content so mind-numbing that I've never assigned it a conventional channel number. 

I don't know whether a character display limit in the OSD exists in myth 0.22/0.23 or not.

---

### Post by novellahub on 2010-04-06
Have you tried inputting just 1245 into the remove and see if it changes the channel?

---

### Post by oldtincup on 2010-04-07
Thanks.  Inputting 1245 does change the channel.  I do have a few channels that are longer (eg. 123-12) entering 12312 does *not* change the channel and only 4 characters are displayed.

I suppose that I could rename the few channels that are longer, but, that wouldn't be the optimal solution.  Any other ideas?

---

