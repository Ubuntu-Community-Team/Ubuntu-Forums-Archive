---
title: "Kworld ATSC 115 Sound Problems"
date: 2008-06-26
forum: Mythbuntu
---

### Post by Twintop on 2008-06-26
Hi all,

I have a Kworld ATSC 115 installed and mostly working on Mythbuntu 8.04. I am able to watch TV with MythTV (though it is a bit choppy), but the real problem is with the audio. Everyone is too high pitched (sound like chipmunks). Does anyone have any advice on how to resolve this? Sound from any other program works perfectly.

Thanks!

---

### Post by Twintop on 2008-06-26
Bumping this for the day crew, if anyone has any thoughts.

---

### Post by mark467 on 2008-07-08
I am having the same issue it seems. My Audio/Video worked fine for a few weeks and this started in the middle of a movie the other day. Here is my post about it

[http://ubuntuforums.org/showthread.php?t=852499](http://ubuntuforums.org/showthread.php?t=852499)

Have you found out any solutions or places to start on this?

---

### Post by Twintop on 2008-07-08
mark467, I have not found any solutions to this as of yet (but have not had a lot of time the last few weeks to dig around or get dirty with it, either). I would like to note that when I reinstalled Mythbuntu, I can't get any signal from my card now. Before, I installed the system and popped the card in after. I think that I'll be giving it another shot when I get home tonight, and will report back my findings.

---

### Post by kwisher on 2008-07-17
I am also having the same issue. Anyone discovered a fix yet?

---

### Post by novellahub on 2008-07-18
> **Twintop said:**
> mark467, I have not found any solutions to this as of yet (but have not had a lot of time the last few weeks to dig around or get dirty with it, either). I would like to note that when I reinstalled Mythbuntu, I can't get any signal from my card now. Before, I installed the system and popped the card in after. I think that I'll be giving it another shot when I get home tonight, and will report back my findings.

Do you have the firmware file in the /lib/firmware directory?  I have found that my Kworld 115 card would not lock in channels without it in the directory (dvb-fe-nxt2004.fw)

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#Avermedia](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#Avermedia)

```
$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2004
$ sudo cp dvb-fe-nxt2004.fw /lib/firmware
```

---

### Post by kwisher on 2008-07-18
> **novellahub said:**
> Do you have the firmware file in the /lib/firmware directory?  I have found that my Kworld 115 card would not lock in channels without it in the directory (dvb-fe-nxt2004.fw)

[https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#Avermedia](https://help.ubuntu.com/community/MythTV_Feisty_hardware_list#Avermedia)

```
$ chmod +x get_dvb_firmware
$ ./get_dvb_firmware nxt2004
$ sudo cp dvb-fe-nxt2004.fw /lib/firmware
```

Does this fix the audio problem?

---

### Post by Twintop on 2008-07-19
novellahub, that doesn't seem to do anything for me unfortunately (audio or video). Here's a quick excerpt of messages that mythtv spits out to the console:

```
2008-07-19 19:17:59.213 A audio timecode 159355
2008-07-19 19:17:59.271 NVP: Video is 3.12642 frames behind audio (too slow), dropping frame to catch up.

```

It looks like the problem is lying in my card not grabbing frames as often as it should, and causing it to be choppy/sped up. Recordings look the same as livetv, also.  I'm still trying to figure it out...

---

### Post by TheAnt on 2008-07-20
Hello all, I've been following this thread for a couple of weeks now and was also having the same stuttering strange audio problem that you report here. I have Mythbuntu 8.04 with a Kworld 115 card as well. After looking around the web for similar issues I discovered that I could display live analog TV using Mplayer properly with this command.

mplayer -v tv:// -tv driver=v4l2:norm=NTSC:input=0:alsa:adevice=hw.1,0:forceaudio:immediatemode=0:audiorate=32000:amode=1:width=384:height=288:outfmt=yuy2:device=/dev/video0:chanlist=us-bcast:channel=4

 It would appear that there is a mismatch in the audio rate of the capture card and the audio rate of playback. I'm able to duplicate the chipmunk like audio if I change the "audiorate=32000" to 44100 or 48000 with the previous mplayer command... Might be worth a try to see if you can do the same.

 After a bit more searching I re-read this [http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting](http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting)  the section on "Distorted audio on input". So I tried changing the "Live TV" profile as suggested from using MP3 to uncompressed... and it worked! No more chipmunks or dropped video frames (which I believe is MythTV's way of trying to keep the audio and video in sync). I think that there is a section in there to change the bit rate as well... but I have not tried that yet. So perhaps give this a try...

(Text taken from [http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting](http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting))
...
The solution is to modify the recording options. You'll need to do this for each of several recording profiles in the Utilities/Setup -> Setup -> TV Settings -> Recording Profiles -> Software Encoders area -- live TV, default, low quality, and high quality. It's easiest to adjust these options using the live TV option and then copy your best options to the other profiles.
...

Hope that helps,

---

### Post by Twintop on 2008-07-20
TheAnt, thank you **|------ this much ------|** (not to scale) for posting this. I did exactly what you said on a brand new installation and it worked perfectly. Let me say this again:

[SIZE=7]Thank you![/SIZE]

:-D I'm just so happy/gitty right now!

---

### Post by kwisher on 2008-07-20
> **TheAnt said:**
> Hello all, I've been following this thread for a couple of weeks now and was also having the same stuttering strange audio problem that you report here. I have Mythbuntu 8.04 with a Kworld 115 card as well. After looking around the web for similar issues I discovered that I could display live analog TV using Mplayer properly with this command.

mplayer -v tv:// -tv driver=v4l2:norm=NTSC:input=0:alsa:adevice=hw.1,0:forceaudio:immediatemode=0:audiorate=32000:amode=1:width=384:height=288:outfmt=yuy2:device=/dev/video0:chanlist=us-bcast:channel=4

 It would appear that there is a mismatch in the audio rate of the capture card and the audio rate of playback. I'm able to duplicate the chipmunk like audio if I change the "audiorate=32000" to 44100 or 48000 with the previous mplayer command... Might be worth a try to see if you can do the same.

 After a bit more searching I re-read this [http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting](http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting)  the section on "Distorted audio on input". So I tried changing the "Live TV" profile as suggested from using MP3 to uncompressed... and it worked! No more chipmunks or dropped video frames (which I believe is MythTV's way of trying to keep the audio and video in sync). I think that there is a section in there to change the bit rate as well... but I have not tried that yet. So perhaps give this a try...

(Text taken from [http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting](http://www.mythtv.org/wiki/index.php/Sound_Troubleshooting))
...
The solution is to modify the recording options. You'll need to do this for each of several recording profiles in the Utilities/Setup -> Setup -> TV Settings -> Recording Profiles -> Software Encoders area -- live TV, default, low quality, and high quality. It's easiest to adjust these options using the live TV option and then copy your best options to the other profiles.
...

Hope that helps,

WooooHoooo!!!! Thank you for finding this solution. I have been trying to get this to work for over a week now. Now to add in the second Kworld-115 for my digital channels.

---

