---
title: "Mythbuntu 11.04 HD PVR Green Image - Not starting"
date: 2011-08-05
forum: Mythbuntu
---

### Post by Nausser on 2011-08-05
I've just upgraded my Mythbuntu from 10.10 (hated every minute of it) to 11.04 (loved every second of it... at first).

Back Story:
I have an HD PVR to get all my cable channels. I was using a Cisco RNG-150 connected via component and optical for audio. Had to compile the drivers for the HD PVR separately but it worked (besides breaking my lirc, just used a wireless keyboard) Everything was tolerable until Comcast pushed the Xfinity branding down the pipe and managed to kill my firewire channel control. I've since learned other people have been suffering from the same effect with the Cisco RNG-150.

Current:
I had read that 11.04 had native support for the latest model HD PVR (the one I have) and it had better reviews for lirc as well. So I did the upgrade and rebooted to a perfectly working system. Except for the firewire control of course. So I decided to take my chances on a different brand of box and had it swapped out. As soon as I connect the new cable box, the HD PVR stops working. Myth merely displays a full black screen or more commonly, a full green screen. When I look at th HD PVR box, the blue light around the top doesn't come on so its working I think, just not initiating for some reason. I've seen the green screen before, usually just for a few seconds before sync. I will post my dmesg to show that it is being loaded correctly. Let me know if there are other logs I can post to give more information.

```
dmesg |grep hdpvr
[   13.481742] hdpvr 2-3:1.0: firmware version 0x15 dated Jun 17 2010 09:26:53
[   13.672967] hdpvr 2-3:1.0: device now attached to video0
[   13.672990] usbcore: registered new interface driver hdpvr
```
Also, I try to test with:
```
cat /dev/video0 > test.ts
```
This runs, however, does not produce an actual transport stream viewable by anything. Player says stream contains no data. Nothing seems to trigger the blue halo light on the HD PVR to turn on. Lastly, I've double checked the firmware with a windows computer to make sure that didn't get screwed up.

**Update:**
I was fiddling with the v4l2-ctl command just to make sure I had some sort of interaction with the HD PVR. I could apply different values to the unit with no problems. I upped the video bitrate and changed the audio encoding value. This information is on the MythTV wiki page for the HD PVR found here [http://www.mythtv.org/wiki/Hauppauge_HD-PVR]("http://www.mythtv.org/wiki/Hauppauge_HD-PVR").
After doing so (I don't know that it had any effect) but I tried to run the above cat command to record to a transport stream file and this time it worked. Naturally the next test was the Mythbuntu frontend and I still have the same problem. The blue halo light on the HD PVR box turns on as soon as I cat the recording over. Myth does not yet have this effect. I really wish I wasn't the only one having this issue... Not that I wish bad on anyone else. I will keep you posted on any more findings I have.

**UPDATE:**
Okay, I HATE issues that fix themselves(sort of). After working on some other things, I did a system restart a few times. Was getting lirc functioning correctly and decided to try live TV again on the HD PVR and now it works as it always has. So I guess now I may never know for sure what it was. That's the part I H.A.T.E.

---

