---
title: "SPDIF Out Audio vs. RCA"
date: 2012-03-20
forum: Mythbuntu
---

### Post by Senkoboy on 2012-03-20
I am running Myth.23.  I have a DVI out on my video card hooked to a HDMI cable for my video and RCA cables for my audio. Everything works good except I have to really crank up the volume on my TV to watch HD recordings. Analog recordings might be at a 12 on my tv, SD Digital 25 and HD sometimes up to 45.  I don't know why the audio is so low on HD, but I know others have had similar problems. My motherboard (Intel DP35DP) has a SPDIF out jack.  If I were to hook my computer to a Soundbar with a SPDIF cable would the volume levels be more even?  How much difference would it make? I know now the sound card converts the digital signal to analog, & out to the TV. Is the Digital is just a pass thru, to be converted by a receiver or soundbar?  The same HD show over my antenna can be watched at around 20 on my TV, why do I lose so much volume when it goes through the computer?  

Thanks, Love my mythbox just trying to improve it a little. :guitar:

---

### Post by BicyclerBoy on 2012-03-21
The volume difference could be due to downmix of 5.1 to 2.0 stereo.
Are your HD recording 5.1 ?

I imagine your HD recording could be 2ch AAC & AC3 5.1.
What is the volume like if you play the 2 ch track (HD)?

It could be possible to output your audio over HDMI, either S/PDIF or real HDA audio..
What's the video card?
Would the TV accept HDMI audio?
Does it have S/PDIF iec958 input (coax or toslink) ?

Digital audio over S/PDIF is just raw PCM for stereo but it is a pass-thru' datastream for AC3/DTS.

Your analogue recordings are from tuner card ?
If so then the recording levels could be set for that alsa device.

AFAIK MythTV 0.24 had some tweaks to try to normalise the output levels across the different coders/formats..
Using S/PDIF pass-thru'& 0.24+fixes, I find the 2 ch AAC tracks are about 3dB louder than AC3 5.1 (dvb-t SD/HD).

---

### Post by Senkoboy on 2012-03-21
I have a GeForce 8500GT Video Card with DVI & VGA out. It doesn't have a place to input digital audio.  I have a DVI to HDMI cable hooked to a Samsung TV.  My Tv will accept audio through a HDMI cable, my Roku box works great.  The TV doesn't have a Digital input, just a Toslink out. 

Not sure if any of my HD recordings are in 5.1, but I know I know some are in Dolby.  I record some HD from OTA and some from QAM from my cable.  I'll check for other tracks on my HD recordings and see.

It's not that the analogue recordings are low, they are close to the same if I just watched them without Myth. I am not using that tuner much anymore anyway, our cable went digital.  

I can watch HD with the volume set at 20, didn't think I should have to turn recordings up to 45.  My myth box is on the other side of the wall from my TV, my cables run to a wall plate, then to my TV.  Might be 6 or 8 ft. total length.

Looking at something like a Vizio VSB200 HD Sound Bar with a toslink cable?  didn't know it it would make a big difference.

Thanks

---

### Post by Senkoboy on 2012-03-21
> **Senkoboy said:**
> 

Not sure if any of my HD recordings are in 5.1, but I know I know some are in Dolby.  I record some HD from OTA and some from QAM from my cable.  I'll check for other tracks on my HD recordings and see.


I checked a HD recording tonight, it is in Dolby Pro Logic II (AC3 5.1) That is the only audio track that Myth and Handbrake show.

---

### Post by BicyclerBoy on 2012-03-21
Some of the old gen graphics cards (8500GT etc) had a S/PDIF input header.
This is called pre-azalia HDMI audio, just S/PDIF from mobo soundcard codec over a different cable..

It is not HDA HDMI audio..

I would upgrade to mythv 0.24+fixes..could be a fix for downmix levels..

I was suggesting you lower the levels of the (new) analogue recordings by using the input mixer..

---

### Post by Senkoboy on 2012-03-22
> **BicyclerBoy said:**
> Some of the old gen graphics cards (8500GT etc) had a S/PDIF input header.


No S/PDIF input  on my card.   I would like to do an upgrade sometime, working too many hours right now to try it.

Thanks  :)

---

### Post by BicyclerBoy on 2012-03-22
If you upgrade the video card to GT240 or maybe GT430 you will get improved vdpau & PQ & have HDMI audio..
No soundbar junk needed, mind you flat screen TVs have the worse sound possible.

---

### Post by Senkoboy on 2012-03-22
> **BicyclerBoy said:**
> If you upgrade the video card to GT240 or maybe GT430 you will get improved vdpau & PQ & have HDMI audio..
No soundbar junk needed, mind you flat screen TVs have the worse sound possible.

That might be the best option, even if I upgrade Myth.

---

### Post by nickrout on 2012-03-23
systems basically have two choices with digital audio streams - decode it, process it (change/boost volume/upmix/downmix etc) or leave it as it is and pass it on to the amplifier/tv etc to do the processing there. Purists prefer the latter. 

The fact is that broadcasters often broadcast ac3 or aac sound at different sound levels to regular mp2 sound. It's a fact that changing your hardware won't change.

---

### Post by Senkoboy on 2012-03-23
> **nickrout said:**
> systems basically have two choices with digital audio streams - decode it, process it (change/boost volume/upmix/downmix etc) or leave it as it is and pass it on to the amplifier/tv etc to do the processing there. Purists prefer the latter. 

The fact is that broadcasters often broadcast ac3 or aac sound at different sound levels to regular mp2 sound. It's a fact that changing your hardware won't change.

The only thing a newer video card would do is allow me to transmit a digital signal to my TV instead of analogue.
  _I guess my quetion is would the TV process  the audio better than my mythbox? _
 If I can watch a without myth at the volume set at 20, shouldn't I be able to watch the same show recorded with the same audio level.  It appears that my TV processes the audio differently, I just wondered if the change to digital audio would fix my volume problems.  
I can watch Netflix through my ROKU box via HDMI with the audio in the teens.

---

### Post by BicyclerBoy on 2012-03-23
The TV is likely more consistent.
But the recording levels of recorded media is all over the place as well.
CDs are too loud (marketing game)
DTS tracks are quiet (0dB matches real performance)

This is partly because CDs have marginal dynamic range for the required SNR..

But the AC3 downmix to PCM (& upmix) in ffmpeg has changed over time as has the implementation in mythtv.
I'm fairly sure the volume changes in mythtv0.24+fixes is less annoying..

If your analogue recordings were made from a capture card (I think) then recording level problem was created by you..

---

### Post by Senkoboy on 2012-03-23
> **BicyclerBoy said:**
> If your analogue recordings were made from a capture card (I think) then recording level problem was created by you..



My analogue recordings were made with a PVR-150 , they are about the same level as just watching TV, or Netflix, or a DVD.  It is HD recordings that I have to crank my TV up to 75% of the Max volume.

---

### Post by BicyclerBoy on 2012-03-24
I still think the AC3 decode/downmix is part of the problem.

Do you mean DVD playback on the PC?
which audio track on DVD AC3 or PCM/mpeg2?
DVD playback in MythTV or VLC etc.

Netflix in PC or other external box?
Is netflix running in browser (pulse audio stereo).

What audio levels do you get from VLC playback of your HD recordings.
I assume your VLC is using pulse audio.

---

### Post by Senkoboy on 2012-03-25
I know it is the AC3 5.1 downmix that is the problem.    [http://www.gossamer-threads.com/lists/mythtv/users/462305]("http://www.gossamer-threads.com/lists/mythtv/users/462305") .   I am not the only one to have this problem.  Is there a way to fix this with myth.23?

I downloaded a clip with 5.1 audio to my windows 7 machine, audio levels sounded just fine.

---

### Post by BicyclerBoy on 2012-03-28
You can't fix 0.23 without modifying the code of finding a modified 0.23 ppa. The latter is vey unlikely to exist..
If you are going to do that you may as well build 0.24+fixes or 0.25 from git..

MythTV0.24+fixes is available as ppa for *buntu versions lucid + later..from the mythtv audio developer who was indicated in your link to mythtv.org mailing lists..

If you output digital audio via S/PDIF (& AC3 as pass-thru'), then I would expect the volume changes between AC3 5.1 & AAC mpeg2 PCM to be acceptable.
But to do this you need an external HT amp/AVR or some cheap box.

A new video card (HDMI) can:
- GT240 delivers much better video than 8400/8500/9400 etc
- potential for digital audio not decoded/not down mixed
- HDMI receiver or TV
But some of the required audio setup is only in mythtv 0.24+fixes & 0.25.

---

### Post by Senkoboy on 2012-03-29
I have always said " If it isn't broke don't fix it"  I can live with my volume problems for now, but I will look into .24 or .25 and a newer video card when I have time.  Thanks for the replies !8-)

---

### Post by jyavenard on 2012-04-07
> **Senkoboy said:**
> I know it is the AC3 5.1 downmix that is the problem. Is there a way to fix this with myth.23?

No.

> I downloaded a clip with 5.1 audio to my windows 7 machine, audio levels sounded just fine.

The issue is with ffmpeg (and still is in today's version). It doesn't properly respect the Dolby rules on how to deal with audio levels.

In 0.24 and later, downmixing is not done by ffmpeg if you have a PC with SSE support. So there's no volume issue.

XBMC has a setting to boost volume level too...

I would upgrade to 0.25 if I were you. Audio code is at its best

---

