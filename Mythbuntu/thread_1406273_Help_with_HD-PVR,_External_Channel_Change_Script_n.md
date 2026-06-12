---
title: "Help with HD-PVR, External Channel Change Script not called properly."
date: 2010-02-13
forum: Mythbuntu
---

### Post by bluebeeryale on 2010-02-13
Hi all.  

After banging my head against the wall, Google, and my mythbuntu 9.10 dvr, I'm putting up a flare for help.  (The definition of insanity is doing the same thing over and over, expecting a different result -- well, I'm now self-aware that I've wasted a good 7 hours on this today.)  Apologies for the long explanation, but I've tried and checked just about everything I could find.   

Fundamentally, my issue is that mythtv does not seem to be consistently using the external channel change script setup for my hd-pvr.

Setup Summary:
---------------------  
- Moto6200 Cable box connected to HD-PVR component cables, then USB to mythbuntu 9.10 -- Myth0.22
- firmware on HD-PVR updated
- firewire connection to 6200 box
- HD-PVR setup in backend
       - all three (component/s-video/composite) set up in 'input connections')
       - 'Preset tuner to channel'  blank
       - 'External channel change command' = /usr/local/bin/6200ch_wrapper.sh 
       - 'Starting channel' 780 (this is the line that would get updated on successful change -- don't know how to blank it -- i set it to 780)

- external script has an 'echo' line that i added so i can see when it runs:  "Firewire Channel Change to: ###"   (script works fine from command line, and works /when/ called by MythTV.)

Issue:
---------
Initially selecting "watch tv" calls external script to ch780, video appears on screen.  

Type 787 to change channel, mythtv does NOT call external script. 

The image freezes, then a few seconds later, see cable box get ch780 (not desired 787),screen blank for a few seconds, followed by frontend bailing out to main menu with "Irrecoverable recorder error (OK)".  Pressing Watch TV again call's external script to 780 (last successful value in backend?), and signal appears ok.

MythTV /does not/ call script in LiveTV channel changes, but attempts to change channel on own (see log below).   After a few seconds, it seems to give up, backend calls channel script to 'reset' to previous successful channel, and then front-end gets mad?  I've also noticed similar non-calling of external script on recording attempts.


Any thoughts/suggestions/help greatly appreciated.
--matt


Log
------

**MATT: About to select "Watch TV"**
2010-02-13 17:24:29.761 MainServer::ANN Playback
2010-02-13 17:24:29.785 adding: mythbuntu as a client (events: 0)
2010-02-13 17:24:29.786 TVRec(19): Changing from None to Watching WatchingLiveTV

2010-02-13 17:24:29.789 TVRec(19): HW Tuner: 19->19
**Firewire Channel Change to: 780**
rom1394_0 warning: read failed: 0x0000fffff000040c
rom1394_0 warning: read failed: 0x0000fffff0000410
2010-02-13 17:24:31.273 ret_pid(0) child(5380) status(0x0)
starting with node: 0
node 1: vendor_id = 0x00000ce5 model_id = 0x0000620a
AV/C Command: 780 = Op1=0x00487C27 Op2=0x00487C28 Op3=0x00487C20
2010-02-13 17:24:32.276 ret_pid(0) child(5380) status(0x0)
2010-02-13 17:24:32.845 ret_pid(5380) child(5380) status(0x0)
2010-02-13 17:24:32.851 External Tuning program exited with no error
2010-02-13 17:24:33.031 AutoExpire: CalcParams(): Max required Free Space: 87.0
GB w/freq: 15 min
2010-02-13 17:24:34.234 RecBase(19:/dev/video0): GetKeyframePositions(1,92233720
36854775807,#0) out of 1


MATT: Xavier 17, Florida 8  (Mom=happy, Dad=not so much);)
**MATT: Change Channel to 787**
2010-02-13 17:25:32.814 TVRec(19): HW Tuner: 19->19
2010-02-13 17:25:34.594 Channel(/dev/video0): SetInputAndFormat() failed
2010-02-13 17:25:34.598 TVRec(19) **Error: Failed to set channel to 787.** Reverting
 to kState_None
2010-02-13 17:25:34.602 TVRec(19): Changing from Watching WatchingLiveTV to None

2010-02-13 17:25:34.607 Recording designated 1080i/p because width was 1920
2010-02-13 17:25:39.882 MainServer::ANN Playback
2010-02-13 17:25:39.889 adding: mythbuntu as a client (events: 0)
2010-02-13 17:25:39.944 MainServer::ANN Playback
2010-02-13 17:25:39.944 adding: mythbuntu as a client (events: 0)
2010-02-13 17:25:39.951 TVRec(19): Changing from None to Watching WatchingLiveTV

2010-02-13 17:25:39.955 TVRec(19): HW Tuner: 19->19
**Firewire Channel Change to: 780**
rom1394_0 warning: read failed: 0x0000fffff000040c
rom1394_0 warning: read failed: 0x0000fffff0000410
2010-02-13 17:25:41.437 ret_pid(0) child(5395) status(0x0)
starting with node: 0
node 1: vendor_id = 0x00000ce5 model_id = 0x0000620a
AV/C Command: 780 = Op1=0x00487C27 Op2=0x00487C28 Op3=0x00487C20
2010-02-13 17:25:42.439 ret_pid(0) child(5395) status(0x0)
2010-02-13 17:25:42.991 ret_pid(5395) child(5395) status(0x0)
2010-02-13 17:25:42.998 External Tuning program exited with no error
2010-02-13 17:25:43.179 AutoExpire: CalcParams(): Max required Free Space: 87.0
GB w/freq: 15 min
2010-02-13 17:25:43.216 MainServer, Warning: Unknown socket closing MythSocket(0
xffffffffb4b2b228)
2010-02-13 17:25:43.218 MythSocket(ffffffffb4b2b228:-1): writeStringList: Error,
 socket went unconnected.
                        We wrote 0 of 10 bytes with 1 errors
2010-02-13 17:25:43.857 TVRec(19): Changing from Watching WatchingLiveTV to None

2010-02-13 17:25:43.865 Recording designated 1080i/p because width was 1920
2010-02-13 17:25:47.463 Finished recording College Basketball "Xavier at Florida
": channel 6780


MATT:  Frontend bailed to Main Menu:  Error:  Irrecoverable recorder error (OK)

---

### Post by yonkiman on 2010-02-18
I installed and use the "mythchanger" program to change channels via firewire - it works well for me (live TV and recording).

---

### Post by Nausser on 2011-02-25
How do I install mythchanger in MythTV version .24? I tried to install the package, however, it is not available. I would think it would come by default by now.

Secondly, if version .24 of myth can use my firewire connection to the cable box to change the channels, what do I enter into the "External channel change command:" portion of the HD-PVR input setup? I assume that is where the instructions need to be added to accomplish this.

-Brian

**Update**: Okay, I've got mythchanger installed. What do I enter into the HD-PVR input config where it states:
"External channel change command:"?

In the meantime, I will keep looking.

---

### Post by Akriss on 2011-02-25
Here's a post that helped me get mytchanger working.
hope it helps you as well.

[https://home.timconrad.org/display/taci/Channel+Changing+via+Firewire]("https://home.timconrad.org/display/taci/Channel+Changing+via+Firewire")

---

### Post by Nausser on 2011-02-26
okay. thanks.
I will give it a try and let you know if I pull out on top.

**UPDATE:** I've got it all working perfectly! Thank you very much.

As a note for others, I have a Cicso RNG150 and use the force option "-f" with number 6, so "-f6" with the "/usr/local/bin/change_channel" script.

---

### Post by Nausser on 2011-04-18
Still working fine, however, I have an issue of my cablebox turning itself off every few weeks or so. Myth doesn't seem to know that the box is off even though I believe it should via the firewire control connection. I first though the cablebox was turning off due to heat buildup, however, I've installed a fan over top the cablebox and it stays cool but still randomly turns off.

Can this script be modified to enable the "on if off" command?

---

### Post by pilesofspam on 2011-08-31
I know this is an old thread, but I managed to get this phenomena to stop (I mean the irrecoverable recorder error) by shortening the sleep delays between characters in the channel change script.  I figured this might be the case because single digit channel changes would sometimes work.  Shortening the delays enough still kept it all stable, and now all channels work.

---

