---
title: "strange video-output with Internal player"
date: 2008-04-09
forum: Mythbuntu
---

### Post by BeXS91 on 2008-04-09
Hi all!

I got a stange behaviour of the video output of the internal video player in mythbuntu 7.10 (add some photos below).
The entire screen becomes green and the normal output can be seen twice or even multiple times. (the same output with TV or DVD)
I tested playback in VLC and - changing video output to opengl - everything is fine. Hence i changed output program of DVD to VLC and everything was fine.
But i think i cannot do so with TV?

Is there a possibility to change video output of the internal player of mythtv either?

Thanks for advice.

greetings
ben
=======================
System:
AMD 2400+@2GHz
512 MB ATI Radeon X1600Pro @ fglrx
Mythbuntu 7.10
MSI Digivox Mini SL clone

---

### Post by agent5150 on 2008-04-10
I have the same problem, Video works fine as long as i don't pull up a website in Myth OR exit frontend and launch a setup item and the password prompts comes up and dims the whole screen behind the pop up.  after that... I get green screens in Live TV, DVD, Xine, Mplayer, VLC you name it.

I suspect it is caused by desktop effects like fglrx... but I don't know how to disable it.

Running .21 myth on mythbuntu 7.10 with Nvidia 6150 on board asus m2npv-vm board 1gb ram & PVR-350.

---

### Post by BeXS91 on 2008-04-10
i've checked my drivers again and found a newer version of the ati proprietary driver. after the installation all colors were correct, but only the picture is still displayed twice (see picture).

I temporarily switched to progressive in tv-mode. this corrected the problem until i changed the channels. after that. the entire screen was completely green.

any suggestions?

---

### Post by ruminant1 on 2008-04-11
I saw this behavior and it's fixed now but I'm not sure which of these two things fixed the problem:

1) make sure xvideo is working.  Type xvinfo and see if you get something useful.  Mplayer in the frontend defaults to using xvideo.

2) there was a setting somewhere that said something about using different resolutions for the gui and playback.  I think I did better when this was off.   I'm not in front of my mythbox right now, so I can't investigate further.

I hope this helps.

---

### Post by ruminant1 on 2008-04-12
Funny.  This morning I was using my mythbox and I accidentally clicked on "watch TV."   I never use this feature because the box is hooked to my TV.  Anyway, even though the behavior you described no longer happens to me when I watch my recordings, there it was on live TV!

It turns out that I can get it to look OK if you set the video scan to "progressive."  On some channels, this is challenging because the menu was unreadable, but I found that if I activated the guide, then went back to the signal, it worked long enough for me to set the scan.

It seems there must be a setting somewhere to set the scan for all channels, but I don't know where that is.

---

### Post by BeXS91 on 2008-04-13
Searching again and again i found a solution that is working for me. I set the decoder in frontend-config->config->playback->current video playback profile from standard decoder to libmpeg2.
now i'm able to watch tv & recordings the way i should be.

but i spot another strange thing. if i switch the channels sometimes (might depend on the transponder) the hole video output "crashes" so nothing can be recognized. if i go back to main menu and start livetv again that channel (transponder) is working but the same behaviour if i switch back to a channel of the other transponder.

any ideas?

greets
ben

---

### Post by BeXS91 on 2008-04-13
> **ruminant1 said:**
> 
It turns out that I can get it to look OK if you set the video scan to "progressive."  On some channels, this is challenging because the menu was unreadable, but I found that if I activated the guide, then went back to the signal, it worked long enough for me to set the scan.

It seems there must be a setting somewhere to set the scan for all channels, but I don't know where that is.

I tried it with manually switching to progressive (before i found out my solution above). But this only helped for seconds and than the picture freezed, so i had to end LiveTV and restart again.

---

