---
title: "ALSA issues: Channel mapping and volume"
date: 2011-01-15
forum: Multimedia Software
---

### Post by daniel.pool on 2011-01-15
Hi there,

I'm having some sound issues with my HTPC XBMCbuntu build (specs at end of post) and was hoping for some community advice. I've done some reading around and think that I have a solution to most of the issues I'm having, but basically this project was started with sound quality as a goal, so if anyone can suggest a better solution I'm all ears.

Basically I have the following issues:

[LIST=1]
[*]Volume is extremely loud. Right now in alsamixer I have the volume set to -38dB (1%) of gain and it is what I would term "normal" listening level. The next step down is off. I've actually blown the front grill off a test speaker whilst playing around with sound on the card;
[*]The centre and LFE speakers are mapped to the wrong channels; and
[*]I can only get output from the rear speakers when I use pcm.surround71, any of the others (surround40, surround51) and nothing comes out.
[/LIST]
So, I figure the solution lies in editing the ~/.asoundrc as I can do the following:

[LIST=1]
[*]Address the volume issues by lowing the output for each speaker in the ttable mappings;
[*]Swap the mixed up speakers/channels over again in the ttable mappings; and
[*]Change the surround51 to be an 8 channel mapping with the side channels set to a volume of 0.
[/LIST]
So basically does anyone have a better solution or can they confirm that this would be the approach to fix this? Also could they confirm that if I were to play an Dolby Digital or DTS movie that the sound card would decode these correctly?

Thanks in advance,
~Dan

Setup:
Alsa version 1.0.23 (comes with Ubuntu)

Ubuntu x64 server 10.10 "Maverick Meerkat" Minimal (2.6.35-24-generic)
XBMC 10.0 r35648 (Compiled : Dec 17 2010)
[SIZE=1]Asus AT3N7A-I ION Motherboard, Intel Atom 330, 2GB Kingston EEC DDR2 PC2-6400 (800), GeForce 8300 mGPU  (Built-in), Auzentech X-Merridian 7.1 (Oxygen HD, CMI8788), 32 GB OCZ SSD 2.5" SATA, LG GGC-H20L  Blu-Ray & HD-ROM, PicoPSU 120W Red[/SIZE]

---

### Post by gordintoronto on 2011-01-15
One of the advertised features of your sound card is, "the highest analog output levels of any sound card on the market." And you're complaining? [smile]

Are your speakers plugged directly into the sound card?

By the way, it's irrelevant to your question, but the Ion chipset includes GeForce 9400 video, not 8300.

I don't have any answers to your actual questions, but perhaps someone else does.

---

### Post by daniel.pool on 2011-01-15
> **gordintoronto said:**
> One of the advertised features of your sound card is, "the highest analog output levels of any sound card on the market." And you're complaining? [smile]

Are your speakers plugged directly into the sound card?

Good point, but I would have not expected the output to be quite that high, sending such a large signal into most amplifiers can result in smoke or worse fire. IIRC my amp has a limit of ~150mv before I'll start seeing puffs of smoke. Perhaps the solution here lies in lowing the gain input on the amp ... or seeing if the card output can be lowered. I'm sending the signal into a 8x100W amp and then onto some 87dB efficient speakers, though I'm currently only actively using 5 channels, the extra capacity being there so I can bi-amp the front channels/go 7.1 at some future date.

> **gordintoronto said:**
>  By the way, it's irrelevant to your question, but the Ion chipset includes GeForce 9400 video, not 8300.

Ouch, that's a copy and paste error that's been in my signature (on another forum) for the best part of a year ... how embarrassing :oops:

---

### Post by lidex on 2011-01-16
Does this setup utilize pulseaudio?

---

### Post by daniel.pool on 2011-01-16
> **lidex said:**
> Does this setup utilize pulseaudio?

Hi lidex,

No, so far as I know pulse is not involved, XBMC used to be a pure ALSA app (and therefore hog all the sound) though I think that you can now enable pulseaudio support if you want to share sound resources.

Is there an easy way to test (a quick google hasn't thrown up anything)?

I'm assuming pulse isn't involved though as I have to kill XBMC in order to run speaker-test.

~dan

---

### Post by lidex on 2011-01-18
Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by daniel.pool on 2011-01-22
> **lidex said:**
> Use the alsa-info-script to provide detailed information.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

Hey Lidex,

Sorry I've been an age replying. I'd tried the configuration I'd considered and a few more things last weekend and then haven't had a chance to look at this issue since; work, children and social life have all conspired to take priority briefly.

I ran the command and have taken a look at the [output]("http://www.alsa-project.org/db/?f=9de27b0b5b7c921de437bc4efc26009c33362269") generated (just so you know, the system doesn't have a gui. XBMC is the only application installed and that provides a 10' home theatre front end, I SSH onto the box in order to configure/maintain it).

You'll notice I've pushed the volume up to 70% in alsamixer. This is because during movie/audio playback in XBMC the sound is suddenly extremely quiet. However, both speaker-test/aplay and XBMC's menu sounds still suffer the loudness issue (I've turned off the menu/system sounds for now). Since there are multiple threads discussing quiet playback issues in XBMC I'm guessing that I should take that particular issue to that forum. I've also done more checking on the card and as gordintoronto said the outputs run "hot", i.e. 5Vrms, where as most devices expect an input of 2Vrms (not sure where I got 150mv, possibly it was 1.5Vrms and I got confused). I've seen a few suggestions for adding some resistors to the output or it seems my only solution there is to never go more than 40% volume if the output is directly through ALSA. XBMC seems to apply some of it's own sound processing though, so I'll either have to turn that off to get the sound out directly, or adjust something there so the volume is matched between alsa and the dvdplayer.

After some research into the X-meridian card it seems that it uses the side speakers as the rear output for a 5.1 source and the rear speakers for the rear output in 7.1. I found two possible solutions to that. Either plug the rear speakers into the side channel and push everything out 5.1 (which I've opted for) or use the ttable mappings to change the surround51 to be 8 channel and switch the side speakers off. Until I get a 7.1 speaker system, I figure the rears plugged into the side channels are OK. A little annoying though, why can't the rear channel just always be the rear channel?

I've also swapped the centre/LFE channels in the .asound.rc. However, whilst that means I'm now getting the output from the correct speakers the centre channel sounds really muddy and dialog in movies is almost completely inaudible. I'm wondering if the X-meridian has a low-pass filter on what it thinks is the LFE and as I'm sending centre channel sound through it it's getting cut off? In which case the easiest solution might be to swap the channels physically by swapping the RCA plugs over rather than try any software mapping? Not sure why the LFE/Centre would be backwards to the conventional norm though :confused:

I might shove a windows install on a spare HDD to see if these problems present themselves with the Azuentech drivers (I don't remember having them last time) but who knows what happens on that OS.

Thanks for your help so far though.

---

### Post by daniel.pool on 2011-01-23
> **daniel.pool said:**
> In which case the easiest solution might be to swap the channels physically by swapping the RCA plugs over rather than try any software mapping? Not sure why the LFE/Centre would be backwards to the conventional norm though 

Decided not to go near windows, I can confirm that the straight swap of the RCA's and changing the ttable back to normal for the LFE/centre now results in a much clearer centre channel.

I'm thinking that my volume issues might well be a non-software fix as well. I've read of a few people either modding the card or adding resistors to the output terminals.

Thanks for your help guys, I'm going to mark this thread solved.
~Dan

---

