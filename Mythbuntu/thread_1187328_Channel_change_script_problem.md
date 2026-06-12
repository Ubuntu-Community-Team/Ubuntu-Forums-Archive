---
title: "Channel change script problem"
date: 2009-06-14
forum: Mythbuntu
---

### Post by nrune on 2009-06-14
I have some settings that I want to pass to the PVR 150 that is recording. However the change channel script works fine in command line but fails when used directly from Mythbuntu.  Help? 

mceirb1 script:
```
#!/bin/bash
 #!/bin/sh
 REMOTE_NAME=RC64
 irsend SET_TRANSMITTERS 2
 for digit in $(echo $1 | sed -e 's/./& /g'); do
         irsend SEND_ONCE $REMOTE_NAME $digit
         sleep 0.8  # note, you may have to tweak the interdigit delay up a bit, depending on your STB model

#irsend SEND_ONCE $REMOTE_NAME ENTER
v4l2-ctl -d 1 -c brightness=176
v4l2-ctl -d 1 -c contrast=96
v4l2-ctl -d 1 -c hue=32
v4l2-ctl -d 1 -c saturation=48
v4l2-ctl -d 1 --set-audio-input=1
done
exit 0
```

Any ideas as to why this script would work fine in the command line but not work when issued from mythbuntu?

Any help appreciated.

---

### Post by dhotman on 2009-06-16
Greetings,

I can see that you posted only a day ago but was wondering if by any chance you've managed to find out what the problem is?

I am experiencing exactly the same issue: the script works perfectly fine from the shell but the exact same script doesn't work when called from the myth backend.  The troubleshooting that I have managed to do so far leads me to believe that myth is not sending the channel number through to the script.  The log of my channel changer script reports:

> irsend: not enough argumentsI'm not really sure how to check but this problem could be caused by some or other value being missing in the channel data that is stored as part of the EPG.

Any ideas would be helpful :)

Thanks in advance

---

### Post by dhotman on 2009-06-16
Been trying to determine if my theory about myth not sending the channel number to the channel change script is right and this is the additional information I've managed to gather.  I started the mythtv backend in a verbose mode using the following command:

>  mythbackend --verbose channelAnd this is the relevant output

> 
2009-06-16 19:36:57.456 Seem to be woken up by USER
2009-06-16 19:37:09.309 MainServer::HandleAnnounce Monitor
2009-06-16 19:37:09.309 adding: pvr as a client (events: 0)
2009-06-16 19:37:09.309 MainServer::HandleAnnounce Monitor
2009-06-16 19:37:09.310 adding: pvr as a client (events: 1)
2009-06-16 19:37:09.315 MainServer::HandleAnnounce Playback
2009-06-16 19:37:09.315 adding: pvr as a client (events: 0)
2009-06-16 19:37:09.318 TVRec(1): Changing from None to WatchingLiveTV
2009-06-16 19:37:09.318 TVRec(1): Start channel: 103.
2009-06-16 19:37:09.322 TVRec(1): HW Tuner: 1->1
2009-06-16 19:37:09.323 Channel(/dev/video0): Device name 'Hauppauge WinTV PVR-150' driver 'ivtv'.
2009-06-16 19:37:09.343 ChannelBase(1): Input #1: 'Composite 1' schan(103) sourceid(1) ccid(1)
2009-06-16 19:37:09.343 ChannelBase(1): Current Input #1: 'Composite 1'
2009-06-16 19:37:09.343 Global TVFormat Setting 'PAL-I'
2009-06-16 19:37:09.344 Channel(/dev/video0): Input #1: 'Composite 1' schan(103) tun() v4l1(PAL) v4l2(PAL-I)
2009-06-16 19:37:09.344 Channel(/dev/video0): SetFormat(Default) fmt(PAL-I) input(1)
2009-06-16 19:37:09.344 Channel(/dev/video0)::SwitchToInput(in 1, '')
2009-06-16 19:37:09.346 Channel(/dev/video0): SetInputAndFormat(1, PAL-I) (v4l v2)
2009-06-16 19:37:09.346 Channel(/dev/video0): SetChannelByString(103)
2009-06-16 19:37:09.349 Channel(/dev/video0): SetFormat(Default) fmt(PAL-I) input(1)
2009-06-16 19:37:09.349 External channel change: /usr/local/bin/chan_changer.sh
2009-06-16 19:37:09.350 Waiting for External Tuning program to exit
2009-06-16 19:37:10.351 ret_pid(25469) child(25469) status(0x100)
2009-06-16 19:37:10.351 External Tuning program no longer running
2009-06-16 19:37:10.351 ChannelBase: external tuning program exited with error 1
2009-06-16 19:37:10.351 TVRec(1) Error: Failed to set channel to 103. Reverting to kState_None
2009-06-16 19:37:10.351 TVRec(1): Changing from WatchingLiveTV to None
Some input from someone who understand the code here would be incredibly helpful.

Thanks

---

### Post by mitchell2345 on 2009-06-16
how did you enter your cmd in mythtv-setup?

---

### Post by nrune on 2009-06-16
Um the changing channels part of the script works fine, it is the...
> v4l2-ctl -d 1 -c brightness=176
v4l2-ctl -d 1 -c contrast=96
v4l2-ctl -d 1 -c hue=32
v4l2-ctl -d 1 -c saturation=48
v4l2-ctl -d 1 --set-audio-input=1


Part that does not work in mythtv but does work in command line.

---

### Post by dhotman on 2009-06-17
Hello Nrune,

Sorry I hijacked your post like that, I understood your issue differently :oops:

I've created a new thread here:
[]("http://ubuntuforums.org/showthread.php?t=1189862&highlight=Channel+change+problem+Mythbuntu")
[http://ubuntuforums.org/showthread.php?t=1189862&highlight=Channel+change+problem+Mythbuntu](http://ubuntuforums.org/showthread.php?t=1189862&highlight=Channel+change+problem+Mythbuntu)

Good luck

---

### Post by azmyth on 2009-06-17
> **nrune said:**
> Um the changing channels part of the script works fine, it is the...


Part that does not work in mythtv but does work in command line.
Assuming you're script isn't throwing an error, my guess would be is it's sending the commands but the blaster is still flashing the change channel thus the command is adjusting nothing. I'd add a sleep command after the change channel and make it long to test.

---

### Post by kyphos on 2010-12-03
> **nrune said:**
> I have some settings that I want to pass to the PVR 150 that is recording. However the change channel script works fine in command line but fails when used directly from Mythbuntu.  Help? 


@nrune,
It's been a year and a half since you started this thread, but I think I might have figured it out. I've spent the last couple of weeks trying to improve video quality captured on the S-video input on my PVR-150, and concocted a script very similar to yours. Tonight I stumbled across your thread while troubleshooting another problem I've having.

(I'm guessing that your intent was to tweak video on the S-video input based on your command to set the audio_input to 1)

The reason that the video parameters you specified with the v4l2-ctl commands didn't work is that myth sends its own settings to the PVR-150 immediately after your external change channel command script executes. Your script DID set the tuner card as you wanted, but myth then overrode your settings.

The myth data architecture defines a set of video parameters (hue, contrast, brightness, saturation) PER CHANNEL. These parameters can be edited in the Channel Editor (part of back-end setup), or via MythWeb.  My solution was to tweak the video settings for Channel 1 (having configured the S-video input on the PVR-150 to be Channel 1 in my channel table).

My channel changing script also tried to fiddle the audio level (volume setting) for the S-video input.  Alas, mythtv also overrides the volume parameter my script sent, using the volume setting specified in the Recording Profile for the MPEG class of encoders. Unfortunately, I've never been able to find a way to get different volume settings for the different inputs to the PVR-150 card (tuner input vs S-video input).

If anyone knows a method to accomplish this, please post back.

---

