---
title: "Can't set Starting channel"
date: 2015-06-12
forum: Mythbuntu
---

### Post by linuxrrules on 2015-06-12
In the Back End settings, under "Input connections", I cannot fill in "Starting channel".  It says: Please add
I can not type anything in nor do any of the arrow keys show me any options.

Details:
* Fresh install of Mythbuntu 14.04.02
* My tuner capture card is supported.  It is a -  Kworld UB435-Q V3
* All instructions provided to set up the Backend were successfully followed (except for one issue noted below)
* I was successfully able to scan SchedulesDirect for available channels and I accepted them.

Here is what I have for the "Connect source to input screen":
     Capture device:   [DVB:/dev/dvb/adapter0/frontend0]
     Input:                   DVBInput
     Display name (optional):
     Video Source:      SchedulesDirect
     Use quick tuning: Never
     Use DishNet long-term EIT data: <unchecked>
     Starting channel:  Please add

I spent hours googling and found one link where another user had [this issue]("http://www.gossamer-threads.com/lists/mythtv/mythtvnz/467049") back in 2011 for a much older card.  The fix was that he did was to revert to MythTV .23 (.24 caused him the issue).  I don't see how this could even be viable in my situation since MythTV is currently on version .27.  Going back to something that old would break something else.

Specifying the Starting Channel is a must because I can't watch Live TV without it.  

Prior to me exiting the setup for "Input Connection" in the backend setup, I receive the following dialog box containing:
Card 1 (type DVBInput) is set to start on channel Please add, which does not exist.
Card 3 (type DVBInput) is set to start on channel Please add, which does not exist.
button - Yes Please
button - No, I know what I am doing

I am forced to select the "No, I know what I am doing" button because it won't let me put in a starting channel.

When I then try to play Live TV on the frontend, I get a "Please Wait" message for a fraction of a second and then nothing happens.  The backend log shows a series of errors:

Jun 11 23:49:57 mythbuntu1 mythbackend: mythbackend[1435]: E TVRecEvent channelutil.cpp:1939 (GetChannelData) GetChannelData() failed because it could not#012#011#011#011find channel number 'Please add' in DB for source '1'.
Jun 11 23:49:57 mythbuntu1 mythbackend: mythbackend[1435]: E TVRecEvent recorders/channelbase.cpp:221 (IsTunable) ChannelBase[1]: IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
Jun 11 23:49:57 mythbuntu1 mythbackend: mythbackend[1435]: E TVRecEvent channelutil.cpp:1939 (GetChannelData) GetChannelData() failed because it could not#012#011#011#011find channel number 'Please add' in DB for source '1'.
Jun 11 23:49:57 mythbuntu1 mythbackend: mythbackend[1435]: E TVRecEvent recorders/channelbase.cpp:221 (IsTunable) ChannelBase[1]: IsTunable(DVBInput,Please add) Failed to find channel in DB on input '1' 
Jun 11 23:49:57 mythbuntu1 mythbackend: mythbackend[1435]: E TVRecEvent recorders/channelbase.cpp:171 (Init) ChannelBase[1]: Setting start channel 'Please add' failed, #012#011#011#011and we failed to find any suitible channels on any input.

Is there a workaround for this issue?

Thanks for reading this long post.

---

### Post by MoebusNet on 2015-07-09
Your error message said ...'failed to find any channels on any input.' You need to scan for channels from your input card. An easy way to do this is from 'Channel Editor'. There is a button to scan for channels; click it and let it finish scanning.

---

