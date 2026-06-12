---
title: "Nvidia ION2 VDPAU persistent lip sync problem on MythTV 0.27"
date: 2014-03-18
forum: Mythbuntu
---

### Post by Antti_Savinen on 2014-03-18
Hello all,


I really need your help! I've googled night after night, but I haven't solve this one yet. I hope I can get help specific from _ION2 + VDPAU_ users.


**PROBLEM SYMPTOMS**


Lip sync is drifting for all recorded programs. It's worst with HD content, but lip sync is not perfect with SD content either. I'm using advanced 1 de-interlacing. It's worst with Advanced 2 (even if playback is smooth!) and also with other less demanding de-interlacing. Playback info shows drifting as well. CPU is not maxed out. Pause/play and skipping might re-sync audio, but not always. Adjusting audio delay doesn't help because of the drifting.


I can stream recorded programs from backend via DLNA to my new LG smart TV and lip sync is perfect! So the actual files are OK. Progressive videos (MKV x.264 HD/SD) playback is also OK with myth frontend. I'm using VDPAU for all decoding.


**HARDWARE AND SETTINGS**


I have separated master backend and frontend. Both running mythbuntu 12.04 and MythTV upgraded to 0.27. Lates updates today and around ones a week from now on. NVIDIA binary drivers on frontend. I had same problem with mythtv 0.25 as well before upgrading to 0.27.


Capturing: Silicon dust HD Homerun tuning DVB-C HD (H.264) and SD (MPEG2). Finnish DNA welho network so content is 25 fps (pal).


Frontend: Zotac ZOTAC ZBOX ID41 (Intel Atom D525 1.8 GHz Dual-Core / Next Generation NVIDIA ION)


Playback for HD: VDPAU + Advaced 1 de-interlacing
Plauback for SD: VDPAU + Advaced 1 de-interlacing + vdpauhqscaling filter


Audio is routed trough SPDIF to amplifier. All audio configurations made with mythtv settings. Separate digital output device checked to enable AC3/DTS passthrough.


Sorry for lengthy post and thanks in advance!


-Antti

---

### Post by blm-ubunet on 2014-03-18
Your setup is not too dissimilar to mine..except (mine is) more capable CPU & GPU.
I can't recall every having lip sync problems & never drifting sync..

Can you start the mythfrontend with logging & post log after playing a recording for couple minutes?
```
mythfrontend -v playback > fe-playback-log.txt
```

---

### Post by Antti_Savinen on 2014-03-19
Hi blm-ubunet,

I did what you asked and here is the log.

[ATTACH]251291[/ATTACH]

Playback info showed Lip sync: 0.20, then -0.10 when I reopened the view and while open it jumped to -0.03. Jump occured when news ended and commercials started. Lip sync was off all the time. Even when the value was -0.03. 

-Antti

---

### Post by blm-ubunet on 2014-03-19
AFAIU The playback OSD jitterometer does not show you the lip-sync offset..this value is the PTS offset between video & audio streams in the ts file.
Different streams have different PTS offsets.

MythTV (all video players) uses the "user" AV sync offset (audio/AV sync offset)** & the stream PTS to calculate the right time to render the video & audio streams.
**-The AV sync offset is done from playback menu/audio/audio offset-sync. This GUI does not timeout (close) in master.

You have been adjusting the lip-sync with this OSD GUI ?
The sync value is persistent & (unfortunately) common for all channels.
Altho I don't find adjust is required between dvb SD/HD, DVD & BD playback.

AV sync/offset adjustment is required due to different decoding/interlacing processing time + display delay times.
For ex. 2x adv de-interlacing could create a 2 field delay. I see about 4 field delay (100ms).

Errors in log:
1.  2014-03-19 18:59:24.736917 E  ALSA: Requested 500000us got 170666 buffer time
(could be problem with AC3 playback)
2.   2014-03-19 18:59:24.738156 E  AFD: Unknown decoding error
(might be problem)

1.
In terminal run this & start myth FE again:
```
echo 192 | sudo tee /proc/asound/card0/pcm0p/sub0/prealloc
```
unfortunately this does not survive a reboot, the root cause could be the bad choice of permissions by alsa.
I fix it with chown/chmod in system startup scripts.

2. Interestingly (but may be unimportant), the video stream is not #0. The video stream does not have to be stream #0 but some code does assume this. The mytharchive DVD creator fails if video is not #0.
MythTV is/has dropping/dropped support for teletext.

---

### Post by Antti_Savinen on 2014-03-19
Thank you for the introduction of AV sync theory. So if I understood correctly the AV sync offset is information only about video stream in question? 

I also went trough the log before posting it and found that alsa buffer issue with suggested cure. I did it and it seemed to help! Good wife has OK, or at least my wife didn't complaint about the lip sync... ;)

I switched to 2x adv with 1080i stream and AV sync was OK at start but eventually after few minutes off again. Is it possible that ION2 just can't handle 2x adv with HD? Back to ADV 1x for now.

For permanent cure to alsa permissions problem you suggested chown/chmod in system startup scripts? Could you help me a bit further with this one or share a link to resource where I can learn more?

Thanks again for your help. I really appreciate it!

-A

---

### Post by Antti_Savinen on 2014-03-20
> **blm-ubunet said:**
> 
You have been adjusting the lip-sync with this OSD GUI ?


Yes, I've tried but as I wrote before av sync has been drifting. It didn't make any sense to adjust delay if it wasn't constant. I give it a new try after this alsa buffer fix.

---

### Post by blm-ubunet on 2014-03-20
So to clarify..
You have been using the AV audio offset OSD GUI to adjust the AV sync dynamically until it looks okay?
&
You have been using the <m>/video/playback data  "jitterometer" OSD to monitor frame sync jitter & buffer stats?

It should not be possible for the AV sync to drift unless the recording is faulty &/or an AVI container..
Transport stream files were designed to prevent this nonsense.

The ION2 should be okay with 2x adv (vector adaptive) on 50Hz material.
AFAIK the ION2 has faster/more/private memory than ION1. ION1 was limited to 1x.

Could try set GPU to performance clock mode; use nvidia-settings to set clocking from adaptive to performance (max).

Maybe the CPU is throttling back & causing an I/O problem. The later atoms are more complex than N270 gen1.
Perhaps a CPU clock monitor or clock control programs could reveal something.

My observations (biassed) lead me to think the really strange playback problems seem to occur with ION systems..
Some of these problems were only resolved by changing the localhostname & so creating a new profile.

What is entered in your VDPAU playback filters for HD res ?
Some of those keywords have been changed/moved.

---

### Post by Antti_Savinen on 2014-03-20
OK, quick update.

Your summary was correct. I really thought that playback data was revealing that lips sync is off. Now I know better thanks to you.

I adjusted AV sync with offset OSD GUI. Lip sync was perfect in two HD recordings from different channels and in one SD recording watched today.
I don't know was it the 192 prealloc, or the phase of the moon but now it works OK!
I agree that there are real strange playback issues with ION systems. I've enjoyed perfect playback before and then faced AV sync issues again. I've tried mythtv few years back with ION1 system and back then I switched to WMC. Shame on me - I know. I will definitely try nvidia-settings you suggested.

About VDPAU playback filters:
--
cmp(>= 0 720) ... filt(vdpaucolorspace=auto)
cmp(> 0 0) ... filt(vdpaucolorspace=auto, vdpauhqscaling)
--
So only filter I've added is vdpauhqscaling for SD. HD is with default filter vdpaucolorspace=auto.

My problem is solved for now - I think. Thanks again for your very professional help. It's nice to have communities like this to support one's hobby.
I'll share here if I get Adv x2 working.

Cheers!

Antti

---

### Post by Antti_Savinen on 2014-03-22
Quick update

Adv 2x works perfectly for HD content on ION2! I had to more than double Audio sync value (Adv 1x --> Adv 2x). Adv 2x works even with vdpauhqscaling on SD content!

I'm willing to believe that the error was more with the user (me) rather than in the system. I've thought that adjust Audio sync value was for fixing poorly encoded video files, not constant setting. I've tried to adjust audio sync before with no luck. Maybe because too small adjustment values. After upgrading my TV lip sync went way of. Now audio sync value with my setup is 250ms and all is well! :-)


-A

---

