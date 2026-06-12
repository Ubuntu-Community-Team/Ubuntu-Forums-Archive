---
title: "Help – MCEUSB IR Blaster"
date: 2008-07-09
forum: Mythbuntu
---

### Post by Tim L on 2008-07-09
I am still unable to get the IR Blaster on my MCEUSB to work correctly. From Mythtv the remote change command does not get to the IR LED. I am beginning to think it is something I have not done in Mythtv. I live in New Zealand and do not have an EPG.

I have followed the instructions in:
[https://help.ubuntu.com/community/MythTV_External_Channel_Changer](https://help.ubuntu.com/community/MythTV_External_Channel_Changer)

After following the above instructions, all the tests for the remote seem to work for example typing “./change-channel-lirc.sh 1” produces the correct result. I have put the channel change script in the correct place. Although the remote works in all other respects, the IR LED will not change the channel. The channel change does show on the TV correctly.

Please could someone tell me what I am missing.

---

### Post by freymann on 2008-07-09
> **Tim L said:**
> 
After following the above instructions, all the tests for the remote seem to work for example typing “./change-channel-lirc.sh 1” produces the correct result. I have put the channel change script in the correct place. Although the remote works in all other respects, the IR LED will not change the channel. The channel change does show on the TV correctly.

Please could someone tell me what I am missing.

 If it works from the command line but not from within Myth... then I would be taking a look at your /var/log/mythtv/mythfrontend.log and mythbackend.log files. 

 One of them will describe what the system is doing and log details about your channel change. You may be able to determine what is wrong by looking through the logs.

---

### Post by Tim L on 2008-07-09
Freymann – thanks I think I have found the problem in mythbackend.log as follows, but do not know what to do to correct or what it is saying, any suggestions?

GetChannelData() failed because it could not find channel number 'Please add' in DB <what is DB> for source '1'.
ChannelBase(1): IsTunable(Composite 1,Please add) Failed to find '1'
ChannelBase(1) Setting start channel 'Please add' failed, and we failed to find any suitible channels on any input.
TVRec(1): HW Tuner: 1->1
Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
Channel (/dev/video0)::TuneTo(1): Error, failed to find channel.
TVRec(1) Error: Failed to set channel to Please add.
TVRec(1) Error: GetProgramRingBufferForLiveTV()
ProgramInfo is invalid.

---

### Post by freymann on 2008-07-09
> **Tim L said:**
> Freymann – thanks I think I have found the problem in mythbackend.log as follows, but do not know what to do to correct or what it is saying, any suggestions?

GetChannelData() failed because it could not find channel number 'Please add' in DB <what is DB> for source '1'.
ChannelBase(1): IsTunable(Composite 1,Please add) Failed to find '1'
ChannelBase(1) Setting start channel 'Please add' failed, and we failed to find any suitible channels on any input.
TVRec(1): HW Tuner: 1->1
Channel(/dev/video0) Error: GetCurrentChannelNum(1): Failed to find Channel
Channel (/dev/video0)::TuneTo(1): Error, failed to find channel.
TVRec(1) Error: Failed to set channel to Please add.
TVRec(1) Error: GetProgramRingBufferForLiveTV()
ProgramInfo is invalid.

 Looks like you haven't set up your sources and inputs yet?

 Read the "General", "Video Sources" and "Input Connections" sections of this link:

[http://www.mythtv.org/docs/mythtv-HOWTO-9.html](http://www.mythtv.org/docs/mythtv-HOWTO-9.html)

 Since it can't find the channel info, I would assume you have done that wrong.... and/or... have you run mythfilldatabase ?

---

### Post by KillerKiwi on 2008-07-09
There a couple of epg for NZ

Theres reven's screen scrapper that runs on mono
[http://www.reven.co.nz/](http://www.reven.co.nz/)

And a zip file that's scrapped from a digital epg at
[http://epg.pvr.geek.nz/epg/](http://epg.pvr.geek.nz/epg/)

---

