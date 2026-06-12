---
title: "HDPVR as generic input device"
date: 2010-11-20
forum: Mythbuntu
---

### Post by davidstoll on 2010-11-20
Does anyone know how to use the HDPVR as a generic input without channel guide info?  Basically, if I want to hook up a device that isn't channel based...like a game console or other video box.

If so, how do I set recordings?

I wonder if I should setup a device in schedules direct, choose only one channel, renumber it to 0 (or 999, or whatever) and make sure it is a channel with no information...?

Any other ideas that actually make sense?  ;)

---

### Post by LowSky on 2010-11-21
if you just want it to record random gaming videos why even use myth? just use a easy termianl command to reocrd the input, like so

cat /dev/video0 > test.ts

---

### Post by davidstoll on 2010-11-21
It's easier to schedule it.  Easier to use a remote.  Easier to setup via mythweb.

...and you can make it time bound.

I've used the cat command before, but it craps out after a few seconds on the HDPVR device.

---

### Post by nickrout on 2010-11-21
I have done this before, albeit with a PVR-150. You don't need schedules direct.

In backend setup set up your hdpvr then setup a source as "no grabber" and call it dummy.

In "input connections" connect the card to the video source and enter /bin/true as the channel change script.

Then set up a channel - give it whatever number you aren't already using.

Then do manual scheduling.

It's a while since I did this, but I think I got all the steps right.

---

### Post by davidstoll on 2010-11-22
> **nickrout said:**
> I have done this before, albeit with a PVR-150. You don't need schedules direct.

In backend setup set up your hdpvr then setup a source as "no grabber" and call it dummy.

In "input connections" connect the card to the video source and enter /bin/true as the channel change script.

Then set up a channel - give it whatever number you aren't already using.

Then do manual scheduling.

It's a while since I did this, but I think I got all the steps right.

I get an error that says the device does not have any channels associated with it.  I can say "Continue, I know what I'm doing".  I guess that's ok, but would rather setup some kind of channel list.  This is obviously why I'm not seeing it in the channel guide, but I don't see a way to add a channel on the backend setup.

---

### Post by davidstoll on 2010-11-22
> **davidstoll said:**
> I get an error that says the device does not have any channels associated with it.  I can say "Continue, I know what I'm doing".  I guess that's ok, but would rather setup some kind of channel list.  This is obviously why I'm not seeing it in the channel guide, but I don't see a way to add a channel on the backend setup.

I take that back.  You have to go to #5 Channel Editor to add channel 0 (or whatever) and then go back to #4 Input Connections to place it on the HDPVR.

Now I see channel 0 in the channel guide!  However, when I go to it, all I get is a black screen and I can't get out of it except to kill the frontend process.  However if I "cat" the same input, I do get what I expect from the input.

Also if I schedule a manual recording, I get a error (red f) failure to record.

Any suggestions at this point?  Thanks again for the help.

---

### Post by nickrout on 2010-11-22
> **davidstoll said:**
> I take that back.  You have to go to #5 Channel Editor to add channel 0 (or whatever) and then go back to #4 Input Connections to place it on the HDPVR.

Now I see channel 0 in the channel guide!  However, when I go to it, all I get is a black screen and I can't get out of it except to kill the frontend process.  However if I "cat" the same input, I do get what I expect from the input.

Also if I schedule a manual recording, I get a error (red f) failure to record.

Any suggestions at this point?  Thanks again for the help.

did you specify the channel change script as /bin/true

I would take a look at the backend logs when trying to record.

---

### Post by davidstoll on 2010-11-22
> **nickrout said:**
> did you specify the channel change script as /bin/true

I would take a look at the backend logs when trying to record.

Yes, I set the channel change script to /bin/true.

Here is what the backend log says...

```
2010-11-22 18:30:40.846 Channel(/dev/video2) Error: GetCurrentChannelNum(0): Failed to find Channel
2010-11-22 18:30:40.858 Channel(/dev/video2)::TuneTo(0): Error, failed to find channel.
2010-11-22 18:30:40.869 TVRec(4) Error: Failed to set channel to 0. Reverting to kState_None
2010-11-22 18:30:40.876 TVRec(4): Changing from RecordingOnly to None
```

---

### Post by davidstoll on 2010-12-02
I'm still getting the "failure to record" error, but the channel 0 is in the channel guide.

Any ideas for how to troubleshoot?

I would really appreciate any further assistance that can be provided.

Thanks!

---

### Post by nickrout on 2010-12-02
> **davidstoll said:**
> I'm still getting the "failure to record" error, but the channel 0 is in the channel guide.

Any ideas for how to troubleshoot?

I would really appreciate any further assistance that can be provided.

Thanks!

As I don't actually have an hdpvr and I am working from memory for my pvr150 setup I would have to recommend the mailing list for further assistance at this point.

---

### Post by davidstoll on 2010-12-24
Turns out I had a defective unit.  I sent it back and got a replacement.

However, I am still having a problem.
By the way /dev/videoHDPVR points to the HDPVR input which happens to change after I reboot sometimes, but the shortcut follows the change.  Currently it is video0.

Channel(/dev/videoHDPVR) Error: GetCurrentChannelNum(0): Failed to find Channel
Channel(/dev/videoHDPVR)::TuneTo(0): Error, failed to find channel.
TVRec(4) Error: Failed to set channel to 0. Reverting to kState_None
TVRec(4): Changing from RecordingOnly to None

---

### Post by newlinux on 2010-12-24
> **davidstoll said:**
> It's easier to schedule it.  Easier to use a remote.  Easier to setup via mythweb.

...and you can make it time bound.

I've used the cat command before, but it craps out after a few seconds on the HDPVR device.

The cat command with the HDPVR works fine for me. Seems like you have it setup properly to do what you want. Is the channel 0 you created in the source that is connected to the HD-PVR Input?

If you give up on this you can still schedule recordings with the cat command (assuming you get that to work) using the "at" command. Basic usage is in the man pages and the below thread has some examples:
[http://ubuntuforums.org/showthread.php?t=431793](http://ubuntuforums.org/showthread.php?t=431793)

---

### Post by davidstoll on 2010-12-24
> **newlinux said:**
> The cat command with the HDPVR works fine for me. Seems like you have it setup properly to do what you want. Is the channel 0 you created in the source that is connected to the HD-PVR Input?

If you give up on this you can still schedule recordings with the cat command (assuming you get that to work) using the "at" command. Basic usage is in the man pages and the below thread has some examples:
[http://ubuntuforums.org/showthread.php?t=431793](http://ubuntuforums.org/showthread.php?t=431793)

The cat command does work for me now (as it did a while back), but Hauppauge determined it was a faulty device and replaced it.  I just got it back.

So, any errors that I got before may have been related to a faulty unit.  I'm starting over.  Cat now works just fine.

However, it must be that something is not quite set right for my input device.  I set it up as stated above, but it still fails (see errors about two posts above this) for what I am getting now with the new unit.

If I check my past or upcoming recordings it shows a manual record in red and has an "f" error code.  Recorder failure.

I tried via mythweb too.

---

### Post by davidstoll on 2010-12-29
Backend error log.
Not sure how to interpret.
Can someone make a suggestion as to what to try next?

from mythbackend.log

```

2010-12-29 13:44:01.613 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:01.694 TVRec(4): Changing from None to RecordingOnly
2010-12-29 13:44:01.726 TVRec(4): HW Tuner: 4->4
2010-12-29 13:44:01.792 Channel(/dev/video0) Error: GetCurrentChannelNum(0): Failed to find Channel
2010-12-29 13:44:01.799 Channel(/dev/video0)::TuneTo(0): Error, failed to find channel.
2010-12-29 13:44:01.807 TVRec(4) Error: Failed to set channel to 0. Reverting to kState_None
2010-12-29 13:44:01.815 TVRec(4): Changing from RecordingOnly to None
2010-12-29 13:44:01.832 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:01.850 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2010-12-29 13:44:01.859 Canceled recording (Recorder Failed): test (Manual Record) "Wed Dec 29 13:45:00 2010": channel 10001 on cardid 4, sourceid 6
2010-12-29 13:44:01.875 scheduler: Canceled recording (Recorder Failed): test (Manual Record) "Wed Dec 29 13:45:00 2010": channel 10001 on cardid 4, sourceid 6
2010-12-29 13:44:01.891 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:01.907 ProgramInfo(10001_20101229134400.mpg), Error: GetPlaybackURL: '10001_20101229134400.mpg' should be local, but it can not be found.
2010-12-29 13:44:01.924 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:01.967 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:02.889 Reschedule requested for id 0.
2010-12-29 13:44:03.526 Scheduled 184 items in 0.6 = 0.01 match + 0.62 place
2010-12-29 13:44:03.533 scheduler: Scheduled items: Scheduled 184 items in 0.6 = 0.01 match + 0.62 place
2010-12-29 13:44:04.918 ProgramInfo(): Updated pathname '':'' -> '10001_20101229134400.mpg'
2010-12-29 13:44:04.975 Error deleting 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/MythBuntu/10001_20101229134400.mpg' could not open
        eno: No such file or directory (2)
2010-12-29 13:44:04.992 Delete Error 'GetPlaybackURL/UNABLE/TO/FIND/LOCAL/FILE/ON/MythBuntu/10001_20101229134400.mpg'
        eno: No such file or directory (2)
2010-12-29 13:44:09.002 Reschedule requested for id 0.
2010-12-29 13:44:09.619 Scheduled 184 items in 0.6 = 0.01 match + 0.60 place
2010-12-29 13:44:09.629 scheduler: Scheduled items: Scheduled 184 items in 0.6 = 0.01 match + 0.60 place

```

---

### Post by davidstoll on 2011-02-07
> **nickrout said:**
> I have done this before, albeit with a PVR-150. You don't need schedules direct.

In backend setup set up your hdpvr then setup a source as "no grabber" and call it dummy.

In "input connections" connect the card to the video source and enter /bin/true as the channel change script.

Then set up a channel - give it whatever number you aren't already using.

Then do manual scheduling.

It's a while since I did this, but I think I got all the steps right.

Any idea how to "add a channel" to this input?  If there is no schedules direct database to call and you can't "fetch channel info" from the unit...it doesn't like that I have not assigned a starting channel to it.

:(

---

### Post by newlinux on 2011-02-07
in mythtv-setup there is a channel editor that you can use to add/modify/delete channels.

---

### Post by davidstoll on 2011-02-07
> **newlinux said:**
> in mythtv-setup there is a channel editor that you can use to add/modify/delete channels.

Ah, there it is, thanks...I had it before, but I had to totally re-install Mythbuntu.  :(

Anyway, I was hoping this issue would clear up, but it still doesn't work.  I get a red recorder failed "f" error.

The log looks the same as above.

Can anyone give me any further hints or things to look at?

---

### Post by newlinux on 2011-02-07
Is the start channel the same as the channel you added? And you have the channel changer as /bin/true?

---

### Post by davidstoll on 2011-02-07
> **newlinux said:**
> Is the start channel the same as the channel you added? And you have the channel changer as /bin/true?

Yes to both.

---

### Post by davidstoll on 2011-02-07
One other thing I should mention...maybe this will spark a thought...

When I have the HDPVR setup in the backup setup, live TV doesn't work.  When I select live TV I get a black screen with "please wait..." for a few seconds and then it goes back to the MythTV menu.  Also, other inputs have difficulty recording when the HDPVR is setup as an input in the backend setup.

Specifically, when I setup the inputs and actually have the "dummy" channel guide entered into the HDPVR, that's when the frontend chokes.

Could it have something to do with the frequency table?  I have to choose us-bdcast or us-cable or something else random...there is no "none".

?

---

