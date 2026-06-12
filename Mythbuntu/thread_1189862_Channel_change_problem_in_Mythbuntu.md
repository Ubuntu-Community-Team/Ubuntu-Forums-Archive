---
title: "Channel change problem in Mythbuntu"
date: 2009-06-17
forum: Mythbuntu
---

### Post by dhotman on 2009-06-17
Greetings,

I am experiencing a problem with an external channel changer script at Mythbuntu.  The script works perfectly fine from the shell but the exact same script doesn't work when called from the mythtv backend. The troubleshooting that I have managed to do so far leads me to believe that mythtv is not sending the channel number through to the script. The log of my channel changer script reports:

> irsend: not enough argumentsI'm not really sure how to check but this problem could be caused by some or other value being missing in the channel data that is stored as part of the EPG.

In trying to determine if my theory about mythtv not sending the channel number to the script is right and this is the additional information I've managed to gather. I started the mythtv backend in a verbose mode using the following command:

> mythbackend --verbose channel                      And this is the relevant output

> 2009-06-16 19:36:57.456 Seem to be woken up by USER
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
2009-06-16 19:37:10.351 TVRec(1): Changing from WatchingLiveTV to None                                           I followed the instructions found here on how to do the setup:

> [http://www.mythtv.org/wiki/IR_Blaster](http://www.mythtv.org/wiki/IR_Blaster)Any ideas would be helpful :smile:

Thanks in advance

---

### Post by Triptol on 2009-06-17
You might want to check this script: /usr/local/bin/chan_changer.sh

---

### Post by dhotman on 2009-06-17
Hello Triptol

Thanks for the reply. This is what the /usr/local/bin/chan_changer.sh script looks like:

```
[FONT=Verdana][SIZE=1]
#!/bin/sh

LOG=/var/log/mythtv/changer.log
exec >> $LOG 2>&1

[/SIZE][/FONT][FONT=Verdana][SIZE=1]REMOTE_NAME=dstv_blaster

for digit in $(echo $1 | sed -e 's/./& /g'); do
      irsend --device=/dev/lircd SEND_ONCE $REMOTE_NAME $digit
      sleep 0.8
done[/SIZE][/FONT]

```It accepts the channel number as $1, splits the digits and then sends then using irsend.

This script works 100% every time when run from the command line but it doesn't work when mythtv invokes it.  Somehow mythtv is not sending the channel number and this results in the irsend error being reported in the log.

---

### Post by azmyth on 2009-06-17
LOG=/var/log/mythtv/changer.log

I suspect mythtv or the script user doesn't have permissions to write to this file thus it fails.

I don't know how big the log file will get but I'd write a script to purge it every so often through a cron job.

---

### Post by dhotman on 2009-06-18
Hello azmyth

Thanks for the advise on log rotation, I've setup logrotate to handle these logs but at the moment the log file is less than 100k and only has a handful of entries.

The channel changer script is definately being called by mythtv and when it is invoked it puts entries into the log file reporting:

> irsend: not enough arguments 			 		

I added a line into the script to write $1 into the log file and this is always emtpy/null when the script is invoked my mythtv.

My question here is how can I check what mythtv is sending the channel number to the script?

Thanks

---

### Post by azmyth on 2009-06-18
I assume you added the change channel script to the tuner in mythtv-setup /usr/local/bin/chan_changer.sh ?

I'd ssh in and then as a normal user $ircat mythtv and then start hitting remote buttons on your remote. You should see this in the ircat terminal.

---

### Post by locovaca on 2009-09-04
I know this is an old thread, but I was having the same problem with setting up a Firewire box.  The problem was that I didn't have the frequency (on the V4L setup screen when setting up a channel) box filled in.  Once I filled that in it sent the channel id to the script.

In other words, it doesn't use the channel number on the first page, it uses the one on the third page.

---

### Post by Chewiesw on 2009-12-09
Dhotman, did you ever get Myth to cahnge the channels on your STB? I have excatley the same problem

---

