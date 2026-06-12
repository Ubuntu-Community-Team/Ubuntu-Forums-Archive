---
title: "[SOLVED] XvMC problems on one channel's recordings"
date: 2008-12-01
forum: Mythbuntu
---

### Post by tr1plej on 2008-12-01
I'm using Mythbuntu 7.10 with a Celeron D 3.2 Ghz processor, Nvidia FX5200, and two Air2PC(rev.1) ATSC tuner cards in Minnesota.

I have my Mythbox set to use XvMC to decode the HDTV streams.  When I updated to MythTV 0.21, recordings from channel 4(WCCO/CBS) stoped playing, but everything else worked fine.  I would get a black screen, and if I left it like that it would cause mythfrontend to freeze.  I could set MythTV so use software decoding, and it would play the steam, but my computer is barely fast enough to play it that way.

Here's the weird part.  I could go to 'Watch LiveTV' and channel 4 played fine with XvMC.  It's just when I try to play anything from channel 4 in 'Recordings' that I have problems.

For awhile I used transcode to copy the audio and video into a new mpeg-ts stream and replace the old file.  After doing that MythTV can play the file with XvMC, but I didn't like having to wait 'til the show finished recording then an additional 5-10 minutes for it to 'fix' the file so I could watch it.

I tried updating to 8.04 and 0.21-fixes; even installed the newest Knoppmyth version using MythTV 0.21; all had the same problem with channel 4.

I have since downgraded to MythTV 0.20.2 and everything is working again.  However I miss many of the features in 0.21 and would like to keep my Mythbox somewhat up to date.

I've attached two mythfrontend logs.  One is from trying to play a recording from channel 4.  The other is going though stuff that works: LiveTV channel 4, recordings from other channels, etc.

Thanks in advance for the help.

---

### Post by false_apology on 2008-12-01
I'm a bit of a newbie to MythTv myself, but I had a similar experience so i'll share my story. I was using XvMC also, and I could not playback this one channel. My situation was slightly different then yours; I could not play it live or recorded. I would get those same "Unknown decoding error" messages in my mythfrontend.log too. The only way I was able to fix it (and I acknowledge this makes no sense) was to set up a playback profile where EVERYTHING went to XvMC. For some reason when I had multiple conditions in my playback profile, this problem would occur. (For example, if I used CPU+ or if I set up one to send SD to ffmpeg and only HD to XvMC). How is your playback profile setup? Try creating a custom one, with just one entry, sending everything to XvMC.

My CPU is powerful enough for HD, but I was using a cheap PCI (NOT PCIe) video card. I have since upgraded to a faster AGP card so I can play HD using ffmpeg so I don't have to hassle with XvMC anymore.

Good luck!

---

### Post by tr1plej on 2008-12-03
Thank you false_apology.  I feel kinda stupid now 'cuz it turns out I'm the one who broke it.

When I first upgraded to MythTV 0.21, I had the same issue false_apology had.  I figured out that all the channels I was having issues with were 1080i/p channels.  Since the profiles changed decoding based on resolution, I made a new profile that set everything to use XvMC, and everything worked.

I started having issues with XvMC being able to play DVDs correctly, so I added a condition in my profile to use a software decoder on anything equal to or less than DVD resolution.  Apparently that's when I started having issues with channel 4.  I just didn't put two and two together until false_apology reminded me.

I have now set everything back to using just XvMC, and all the channels and recordings are working fine.  So far I haven't had any issues with the internal DVD player, but I haven't done too much testing yet.  I'll just have to switch to Xine if I have problems.

So there seems to still be a bug in profiles, but this is a workaround(how does one report a bug like this?).  I think my channel 4 issues are with the first frame not showing the correct resolution, and without that the profiles don't know what to use on it.  One solution would be for MythTV to have a default decoder and the profile only overrides that.

---

### Post by novellahub on 2008-12-03
Just curious.  Can your play WCCO content using the CPU++ profile?  I guess I would think a 3.2 ghz processor would be powerful enough without using XvMC.  I have a AMD Athlon X2 3800+ processor and use about 60% CPU playing that CBS channel.

---

