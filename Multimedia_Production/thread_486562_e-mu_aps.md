---
title: "e-mu aps"
date: 2007-06-28
forum: Multimedia Production
---

### Post by cern.th.skei on 2007-06-28
has anyone ever managed to get any sound out of their e-mu aps under ubuntu at all?

have tried absolutely (i think) every tips tricks and suggestions i have found... 
but still no sound...

"asoundconf list"
shows the card as APS, so i guess the driver is loaded and 'running' ???

so, does the "(partially supported)" bit i've seen here and there (alsa lists, etc) mean that it works, except you will just get silence out?? :-)

everything seems to be ok, the mixer is up and running, jack starts, energy xt2 starts, vu-meters and everything moves, butm no sound...

same with absolutely all other audio progs...

cern.th.skei

had to go back to a "crappy" sb audigy 2 nx (usb2).... not too good for "pro" audio work...
do i really have to get a new card?

---

### Post by robertc36 on 2007-06-29
i thought i would reply to your post as a courtesy;  i have posted twice about emu 1212m and no-one has answered.
So seems this is probably not a great place to post about emu.

---

### Post by alistair_blunt on 2007-07-01
hi, 
i've the emuAPS and, with it, all the problems you encountered,
same situation (everything seems ok but no sound at all)
i'm planning to change os but i don't know which one can handle the APS without troubles...
i've tried many Live CD but every OS detects the 10k1 chipset but no one makes it playable...
i really like my Feisty Fawn but with no sound it's quite useless. It's a pity...
alistair_blunt

---

### Post by cern.th.skei on 2007-07-01
too bad... i really liked my (old) e-mu, suited me perfectly...
but, i thinnk i'll give up, and get a new card to replace it..
cern.th.skei

---

### Post by adarkmethod on 2007-07-04
> Hi,

Last updated: 11-11-2006

To test support for the E-Mu cards, one also need the alsa-firmware package.

Small update for those interested. I am the developer currently working on writing a Linux ALSA driver for the:

a) EMU 1212m
b) EMU 1820m

Special WARNING note: The EMU 1212m/1820m seems to have two different variants. The variant with PCI card with MODEL: EM8810 is the one that I have tested with. There are reports of other variants that do not work yet.

Other EMU hardware samples (sound cards) have arrived, so one might expect support in the future for:
a) 1616M PCI
b) 02 CardBus Card
c) 0404 PCI
I have the firmware loading into the 0404 PCI and I am able to loop back analog in to analog out. I am still looking onto getting capture and playback working. Once that works, I will be committing the work so far to the alsa hg repository.
d) 0404 USB 2.0
e) 0202 USB 2.0


The first version of the driver for 1212m and 1820m is now out there. If one is adventurous, one can check out the HG repository and hear sound from the cards in Linux.
It will be released with the next Linux kernel 2.6.19 or alsa-driver 1.0.14.

Not all features are supported yet, but I would welcome some people testing the features it currently has.
Please note, this driver has been written in my free time, with no financial support from E-MU except donation of the two sound cards and a useful datasheet. I welcome constructive feedback.

What should work:
1) 44.1kHz and 48kHz are currently supported.
2) Playback to ALSA devices at 16bit:
front
rear
center_lfe
side
surround40
surround51
surround71
3) That playback or ALSA devices arrives in DSP channels 0-7. One can then select with alsamixer which actual physical output one wished the sound to come from. It loads with mostly sensible defaults.
4) Stereo 16bit sound capture with the default device
5) 8-channel 24bit (S32_LE) in-phase capture suitable for use with jackd/ardour.
6) 8-channel 24bit (S32_LE) in-phase playback suitable for use with jackd/ardour. Note: This has not been tested yet, so might not work very well.
7) Switches to enable PADS (attenuation) to the inputs and outputs.

What is not yet supported:
1) Any rate apart from 44.1 and 48kHz. (I know how to do it, I just need time to implement support for it. Fairly big task.)
2) A patchmix type application. (I really need help here)
3) sync card. (need people to test this for me)
4) ADAT/SPDIF (need people to test this for me)
5) Anything else not mentioned above. :-)

[https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1](https://bugtrack.alsa-project.org/wiki/wikka.php?wakka=emu&show_comments=1)

please note, I havent tried this, but i really want a 1212m to do some recording with, so i'd really like to hear that this works well

---

### Post by robertc36 on 2007-07-04
Me too lol.
Really needs patchmix equivalent though or could get very confusing.

---

### Post by viktormas on 2008-05-19
"...has anyone ever managed to get any sound out of their e-mu aps under Ubuntu at all?..."

After two or more years, my dear EMU APS  works on Linux! I am so glad, I had to post it.

I love this little card and I agree with the comments about its beauty on this forum.

So, recently I installed Ubuntu Studio (8.04) and with a built-in audio card (Realtek something). I got the midi going - so nice, so beautiful. I am using Qsynth with the Soundfonts available from the net and from my EMU APS CD collection.

I couldn't get the audio going, so I just decided tonight to put the EMU APS on my new system.

I switched Jack and it recognized it: EMU APS [4001].
I started Qsynth and Rosegarden, loaded 'Highway Star' from Deep Purple as a midi file and pressed that (dreaded) Start button. 

All was flashing, Rosegarden was sending signal to Qsynth, Qsynth was 'bursting' with activity. I even opened the Meterbridge (which displays jack's audio activity.
all was flashing and moving, but no sound.....

So, I called my fiancee, Ginka, and asked her to tell, as a total 'stranger' to Linux ?Audio, what it could be. She received a 2-minute course in Jack, Qsynth and Rosegarden and was left with the question: what's going on?

She said, well, if the cables are connected ok, then it must be that the audio is going through some other output, maybe headphone?

Well, my thought was 'coaxial' (digital out).

Sure enough, once I connected the digital out of the EMU APS to my old Mindisk player, the most beautiful sound came to my ears: EMU APS on Linux!

Thus, analog outputs do not work (line out or headphones out, for those who have the Edrive). Coaxial digital out works on Ubuntu Studio 8.04 and is completely recognized by ALSA. The fader for volume in alsamix is the 'Wave' fader. The 'IEC958 optical raw' switch MUST be SWITCHED OFF.
The only other thing that reacts at all for now is the 'Tone' switch: when activated, gives extra bass (although in the old EMU APS mixer there wasn't such a thing).

So happy!

The only thing now is, I guess, wait and search for news, drivers, till the whole thing is complete (all outputs and inputs).

It's such a clean and nice, crisp, perfect sound.

One more thing: in Jack, Emu 10k Wave Table is recognized, with 4 ports, all dead.

---

