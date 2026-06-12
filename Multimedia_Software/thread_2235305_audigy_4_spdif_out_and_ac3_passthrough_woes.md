---
title: "audigy 4 spdif out and ac3 passthrough woes"
date: 2014-07-20
forum: Multimedia Software
---

### Post by Totzo on 2014-07-20
As the title suggests I'm having a load of bother with my audigy 4 sound card sending a digital signal to my reciever. It works fine under windows where the amp recognizes DTS/Dolby and outputs multichannel audio accordingly but not in ubuntu where all the lovely software I use is! The setup is just a coax cable (mini jack to rca that came with my camera bizarrely enough but seems to work) from the spdif out on my card to the coax in on the amp.

If I play standard stereo it sends a pcm signal and is played back on the amp no problem but as soon as pass through is enabled nothing seems to get sent (Decoder Off shown on the amp).

I've done a fair bit of trawling around on the internet and found no solution and wondered if the card is just not supported for ac3 pass through in Linux? Has anyone else got this working on the same/similar hardware? I tried uninstalling pulseaudio in case that was causing issues but it made no difference. Tried every setting I could find in alsamixer.

My motherboard is pretty dated so doesn't have onboard spdif out to test as an alternative so I was wondering if I should just buy another cheapo sound card that is known to work fine.

Thanks in advance for any advice :)

---

### Post by Totzo on 2014-07-22
Oh well, no replies, in case anyone comes across this post I thought I'd put my solution here. I decided to scrap my sound card for now and bought a modern nvidia graphics card with HD audio built in. I got a gt 630 which supports pci-e 1.0 thankfully with the added bonus of no cooling fan noise due to it being heat sink only. Not a powerhouse card but enough for HDTV and video. I now have full pass through support through hdmi including True-HD which spdif can't handle and it only cost me £40 plus a few quid for hdmi cables. Way less than my problematic sound card cost back in the day! The only issue I had was that my 1366x768 TV was detected as being 1080p using hdmi so I had to play around with under scanning in the nvidia-settings thingy. I tried using DVI for video and HDMI for audio but it caused more problems than solutions so I've opted to have a bit of my desktop obscured unless I mouse to the edge of that bit of the screen, not a biggy as this is a mythtv box.

I should add that I did have to remove pulseaudio and set volume control off for it to play well with mythtv

---

