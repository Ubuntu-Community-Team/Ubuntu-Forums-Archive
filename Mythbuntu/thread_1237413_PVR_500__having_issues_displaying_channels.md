---
title: "PVR 500  having issues displaying channels"
date: 2009-08-11
forum: Mythbuntu
---

### Post by lustreking on 2009-08-11
I just started playing with Mythbuntu 9.04 and a Hauppauge WinTv PVR 500.

I have cable tv and myth detected the channels properly, but when I try to watch or record, all but the first 13 channels are static.  A television plugged into the same cable line displays all channels properly.

Any thoughts?

---

### Post by klc5555 on 2009-08-11
> **lustreking said:**
> I just started playing with Mythbuntu 9.04 and a Hauppauge WinTv PVR 500.

I have cable tv and myth detected the channels properly, but when I try to watch or record, all but the first 13 channels are static.  A television plugged into the same cable line displays all channels properly.

Any thoughts?

The PVR 500 is an analog-only tuner, which is why it's not sold in the US any longer. Depending on what type of cable provider you have and where you are, your provider may have already transitioned everything above the terrestrial VHF 13 over to digital. The television you plugged into the cable line, if it was made in the last few years, probably also has a clear QAM tuner for non-encrypted digital content, which it finds above ch. 13.

That would be my first guess, pending additional information.

---

### Post by lustreking on 2009-08-11
I would say that I've had the television for at least 10 years.

---

### Post by klc5555 on 2009-08-11
> **lustreking said:**
> I would say that I've had the television for at least 10 years.

OK, well, assuming your cable provider still provides analog cable through ch. 99,  and analog chs. 14-99 are unencrypted and unfiltered, the 500 should get them all, on both of its tuners.

The only suggestions I might make are to be sure you have the cards (each tuner counts as a card in the backend setup) set up in the backend as MPEG-2 hardware decoders (with the ivtv drivers) and not as "v4l analog" and then rescan the cards for stations in Input Connections.

---

### Post by lustreking on 2009-08-12
> **klc5555 said:**
> 
The only suggestions I might make are to be sure you have the cards (each tuner counts as a card in the backend setup) set up in the backend as MPEG-2 hardware decoders (with the ivtv drivers) and not as "v4l analog" and then rescan the cards for stations in Input Connections.

I deleted the card and input connections and set them up again, making sure that I chose IVTV MPEG-2, and when I scanned for the channels, I made sure that I chose us-cable.

It detected all the proper channels, but they (above 13) still show only display static.

I reinstalled several times over the weekend, and I do know that, at one point, I was watching a show on channel 79, but not now.  Maybe I'll try another reinstall.

---

### Post by klc5555 on 2009-08-12
> **lustreking said:**
> I deleted the card and input connections and set them up again, making sure that I chose IVTV MPEG-2, and when I scanned for the channels, I made sure that I chose us-cable.

It detected all the proper channels, but they (above 13) still show only display static.

I reinstalled several times over the weekend, and I do know that, at one point, I was watching a show on channel 79, but not now.  Maybe I'll try another reinstall.

I've nothing substantial to contribute here further, but there is a thread similar to this going on over at the Mythtv group (Gossamer Threads), where the user is no longer able to get a PVR 150 (i.e. a PVR500, but with only one tuner) to receive what ought to be most of the remaining analog channels on his cable account. It might be worth keeping track of what happens in this discussion in case it also eventually solves (or explains) your problem.

The thread is at: [http://www.gossamer-threads.com/lists/mythtv/users/391762](http://www.gossamer-threads.com/lists/mythtv/users/391762)

Sorry I can't offer more immediate help. :(

---

### Post by emperor on 2009-08-20
Having the same problem with Ubuntu 9.04 and PVR-350; no channels display above 13. Cable signal is there as the tuner can scan the channels in setup and other TV's and tuners work properly 2-99. System was working properly in Fedora 8 prior to "upgrade" to Ubuntu 9.04. Installed Server edition 9.04 AMD_64 but tried both server and generic kernels with the same result.

---

### Post by ahood on 2009-08-21
If live TV can be watched and recordings created for channels 1-12, then this suggests that the card is configured and operates correctly to receive an analog signal. 

It is strange that channels 13 and above do not receive a video signal.

If an analog TV is connected directly to the coaxial cable (no box of any sort in between the standard def TV and coaxial cable) and channels 13 and above can be watched, then this suggests that the cable provider has not moved channels 13 and above to the digital spectrums (see [**[COLOR="Blue"]What happens to analog channels when moved to digital?[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=1234794").

Quite perplexing. Will have to think of possible reasons/solutions.

---

### Post by emperor on 2009-08-22
> **ahood said:**
> If live TV can be watched and recordings created for channels 1-12, then this suggests that the card is configured and operates correctly to receive an analog signal. 

It is strange that channels 13 and above do not receive a video signal.

If an analog TV is connected directly to the coaxial cable (no box of any sort in between the standard def TV and coaxial cable) and channels 13 and above can be watched, then this suggests that the cable provider has not moved channels 13 and above to the digital spectrums.

Yes, I believe the PVR-350 is working correctly. The same problem occurs when using an HVR-1600, no analog above 13. I have another non-Myth  analog tuning card in my daughters computer and it tunes correctly and the analog TV works correctly. 

Also the cx18 loaded for the HVR-1600 has a major bug that causes the ethernet port to shutdown on my server The cx18 driver and the nVidia 6150 chipset are not happy either as the "nVidia" video driver will not load. So, Ubuntu 9.04, nVidia,  MythTV and releated tuner cards are not playing nicely at the moment on this system. As a result, I am pulling my MythTV backend out of the Ubuntu file server and moving it to a new dedicated MythTV backend computer and will install MythDora, a Fedora based distribution, instead.

---

### Post by emperor on 2009-08-23
The channel 13 limit is apparently caused by the video souce channel frequency being set to "Default". It needs to be set to "us-cable". This change corrected the channel 13 barrier problem for me.

Reference link that helped!
[http://www.mythtvtalk.com/forum/installation-issues/5134-mythtv-displays-static-all-non-vhf-channels-above-2-13-a.html](http://www.mythtvtalk.com/forum/installation-issues/5134-mythtv-displays-static-all-non-vhf-channels-above-2-13-a.html)

---

### Post by lustreking on 2009-08-23
> **emperor said:**
> The channel 13 limit is apparently caused by the video souce channel frequency being set to "Default". It needs to be set to "us-cable". This change corrected the channel 13 barrier problem for me.


Great!  My notes say that I had channel frequency set to default also.  I'll have to dig out the hard drive I have it installed on and give that a try.

---

