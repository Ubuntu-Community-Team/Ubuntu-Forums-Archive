---
title: "Svideo in not working on a pcHDTV 5500"
date: 2010-08-22
forum: Mythbuntu
---

### Post by enricor77 on 2010-08-22
> **tgm4883 said:**
> You are having some very NOT common issues. I have a 9.10 0.23 backend with an HVR-1600 and pcHDTV-5500 and it works flawlessly. I don't use it for live TV though, as I record all the shows I want to watch. 



Really? Who are you paying?
Hi [[COLOR=#339900]**tgm4883,**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664")
I am trying to get my PCHDTV-5500 to work connected to the svideo or composite or coaxial exit of my direct tv box. 
I am getting black and white video. Can you help me, sharing a quick how to ?
I am going crazy, I had the pvr-150 configured with an annoying static popping sound in background, after trying zillions of patches, scripts I thought about replacing it with the PCHDTV but no luck so far. 
I used to have an old Matrox..good times with kernel 2.4 :-(

Thanks,
E.

---

### Post by nickrout on 2010-08-22
back and white through s-video usually means either:

1. a bad lead - there are a lot of rubbish s-video leads being sold. or

2. the wrong choice of pal/ntsc etc.

---

### Post by tgm4883 on 2010-08-22
Yea, usually black/white picture is wrong setting for PAL/NTSC. That being said the pcHDTV 5500 doesn't have a hardware encoder, so I wouldn't use it with analog TV.

Further support for this issue should go on in another thread

---

### Post by nickrout on 2010-08-22
I too wondered how it ended up here!

---

### Post by enricor77 on 2010-08-23
> **enricor77 said:**
> Hi [[COLOR=#339900]**tgm4883,**[/COLOR]]("http://ubuntuforums.org/member.php?u=191664")
I am trying to get my PCHDTV-5500 to work connected to the svideo or composite or coaxial exit of my direct tv box. 
I am getting black and white video. Can you help me, sharing a quick how to ?
I am going crazy, I had the pvr-150 configured with an annoying static popping sound in background, after trying zillions of patches, scripts I thought about replacing it with the PCHDTV but no luck so far. 
I used to have an old Matrox..good times with kernel 2.4 :-(

Thanks,
E.

I just sent this email to the support:
To the support of PCHDTV,

I have recently purchased the PCHDTV-5500. I have successfully connected the card to the S-Video  exit of my Direct Tv box (Analog);however, no audio is captured.
I am using Mythbuntu 9.10 and mythtv 0.22 as player. 
I tried to compile the drivers from the cd or downloaded from the website but I received errors during the make step. The cx88_audio and other modules are loaded automatically by the system. 
I have connected the PCHDTV-5500 audio jack to the Mic or Line In on my audio card with is not muted and working properly.
 I verified that the S-Video exit is sending both audio and video, using a PVR-150.
I have followed the configuration steps on the wiki page to configure the card in mythtv both as analog and digital setting the open on demand flag and the sample rate at 48K.
I read that the card is sometimes shipped with the audio capture feature disabled and there is a way to enabled changing a registry on the cx88 eprom.

If I connect a jack from the composite exit of the directtv box to the line in I get audio, which is out of synch and not present into the recordings, same if I bridge the audio jacks through the card (directtv to PCHDTV , PCHDTV to line-in)
 
What am I missing?

Thank you so much for your help

An additional note:
Selecting /dev/dsp1 as audio device for the V4l Analog I get a static noise which is present also in recordings.

---

### Post by tgm4883 on 2010-08-23
> **enricor77 said:**
> I just sent this email to the support:
To the support of PCHDTV,

I have recently purchased the PCHDTV-5500. I have successfully connected the card to the S-Video  exit of my Direct Tv box (Analog);however, no audio is captured.
I am using Mythbuntu 9.10 and mythtv 0.22 as player. 
I tried to compile the drivers from the cd or downloaded from the website but I received errors during the make step. The cx88_audio and other modules are loaded automatically by the system. 
I have connected the PCHDTV-5500 audio jack to the Mic or Line In on my audio card with is not muted and working properly.
 I verified that the S-Video exit is sending both audio and video, using a PVR-150.
I have followed the configuration steps on the wiki page to configure the card in mythtv both as analog and digital setting the open on demand flag and the sample rate at 48K.
I read that the card is sometimes shipped with the audio capture feature disabled and there is a way to enabled changing a registry on the cx88 eprom.

If I connect a jack from the composite exit of the directtv box to the line in I get audio, which is out of synch and not present into the recordings, same if I bridge the audio jacks through the card (directtv to PCHDTV , PCHDTV to line-in)
 
What am I missing?

Thank you so much for your help

An additional note:
Selecting /dev/dsp1 as audio device for the V4l Analog I get a static noise which is present also in recordings.

Svideo does not carry audio. You would need to use Svideo and then the red+white composite jacks (3 cables total). All three of these would need to be connected to the pcHDTV 5500

---

### Post by enricor77 on 2010-08-23
> **tgm4883 said:**
> Svideo does not carry audio. You would need to use Svideo and then the red+white composite jacks (3 cables total). All three of these would need to be connected to the pcHDTV 5500

I tried that but I don't audio in the recordings...

Should I use the coax input instead?

---

### Post by tgm4883 on 2010-08-23
> **enricor77 said:**
> I tried that but I don't audio in the recordings...

Should I use the coax input instead?

You probably didn't have the pcHDTV 5500 set up an an analog tuner. I ususally tend to stay away from software encoders, although I don't do analog anymore so it doesn't matter.

---

### Post by enricor77 on 2010-08-23
> **tgm4883 said:**
> You probably didn't have the pcHDTV 5500 set up an an analog tuner. I ususally tend to stay away from software encoders, although I don't do analog anymore so it doesn't matter.

It is configured as V4L in mythtv. Can you help me troubleshoot it? 
I saw the cx88_alsa driver been loaded. The alsamixer has the capture check on the cx88.

Thank you for your help.

---

### Post by enricor77 on 2010-08-24
> **enricor77 said:**
> It is configured as V4L in mythtv. Can you help me troubleshoot it? 
I saw the cx88_alsa driver been loaded. The alsamixer has the capture check on the cx88.

Thank you for your help.

Quick update: 
I got the anolog tuner to work under Mythbuntu  10.04 32bit.
I am asking some clarifying (for dummies :-) ) questions to the support about the S-Video and Composite inputs, which is really helping.
It is nice to have community and vendor help lol

---

