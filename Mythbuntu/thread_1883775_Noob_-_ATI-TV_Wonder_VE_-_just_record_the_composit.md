---
title: "Noob - ATI-TV Wonder VE - just record the composit input"
date: 2011-11-19
forum: Mythbuntu
---

### Post by 1999F250 on 2011-11-19
Hi,
I have a ATI-TV Wonder VE and I would like to use it to record 'just like a VCR' with Mythbuntu.  I am having issues getting the backend server set up so it will record off the composit video in.  Is there a guide or FAQ that explains how to do this?

Config:
  Intel D915GAV P4 3.4GHz dual core 4Gig Ram,  320G HD, nVidia 8400GS.
  Mythbuntu 11.10 - installed today.  FE and BE on the same box.

Backend config
General (all defaults)  (NTSC)
Capture cards  [ V4L: /dev/video0 ]
    Video device:  /dev/video0
    Probed info:  BT878 video (ATI TV-Wonder VE) [bttv]
   VBI device:  /dev/vbi0
   Audio devic:  ALSA:default
   Force audio sampling rate: (None)
   Default input: Composit1
Video sources (I signed up for Schedules Direct event though I don't need a schedule)
   (I enterd the data for SD but it is not letting me show what I entered)
Input connections  [ V4L : /dev/video0 ] (Composit1) ->
   Capture device:  [ V4L : /dev/video0 ]
   Input:  Composit1
   Display name:  Composit1
   Video source:  {blank}
   External channel change command: {blank}
   Preset tuner to channel: 3  { just trying to get it to work}
   Starting channel: Please add channels to this source { cant change this}
  (page 2 is defaults)
  



Currently getting  (var/log/mythtv/mythbackend.log)
2011-11-19 19:32:11.415 TVRec(1): Changing from None to WatchingLiveTV
2011-11-19 19:32:11.457 GetChannelData() failed because it could not
            find channel number 'Please add' in DB for source '1'.
2011-11-19 19:32:11.496 ChannelBase(1): IsTunable(Composite1,Please add) Failed to find channel in DB on input '1' 
2011-11-19 19:32:11.537 ChannelBase(1) Error: Setting start channel 'Please add' failed, 
            and we failed to find any suitible channels on any input.
2011-11-19 19:32:11.579 TVRec(1): HW Tuner: 1->1
2011-11-19 19:32:11.627 TVRec(1) Error: Channel: 'Please add' was not found in the database.
            Most likely, your DefaultTVChannel setting is wrong.
            Could not start livetv.
2011-11-19 19:32:11.687 TVRec(1) Error: CreateLiveTVRingBuffer(Please add) failed
2011-11-19 19:32:11.729 TVRec(1) Error: Failed to create RingBuffer 1

I am comfortable with linux, but don't know much about video/MythTV.

Thanks,
CW

---

### Post by klc5555 on 2011-11-21
Your backend is complaining in the log that your Video Source has no channels. The backend needs at least one known channel on the Video Source to start the card up on. You do not need Schedules Direct or any other grabber for your Video Source for what you're trying to do.

You can add a dummy channel manually for your video source in the Channel Editor.  Set your manually added channel to whatever number you want. Name your new channel whatever you want.

When this added channel information has been saved through the channel editor, there will now be a channel to be found in the database. Your dummy channel should now be a choice along with 'Please Add', and you set your startup channel to it in the Input Connection menu for the composite input you were setting up.

You should be able to watch/capture/record whatever is getting piped in through the composite feed, essentially 'just like a VCR', though if this is all you really want to do, there are much simpler Linux apps and applets out there to do it.

---

### Post by 1999F250 on 2011-11-22
Thanks klc5555 that did the trick!

CW

---

