---
title: "HVR-1600 Signal Strength"
date: 2011-01-27
forum: Mythbuntu
---

### Post by tim273 on 2011-01-27
Hello Everyone,

If this specific thing has been discussed before, I apologize.  I have a working HVR-1600 which properly tunes both analog and digtal OTA ASTC.  Everything works fine (including the remote and blaster).  I also have a digital to analog converter box (apex) that I used to tune ota and there's a certian station that is far away that registers about 45 to 55 on the signal strength on the apex.  If the signal is 50 or above on the apex, it works fine on the 1600, As it drops below 50, I get increasing dropouts and buzzing on the 1600 (to the point where its unwatchable), while it's working fine all along on the apex.  

I know that there's some tuned drivers at Kernal Labs, but those are only for clearQAM not for ASTC.  Does anyone else have this problem?

All stations that have a signal strength above 50 are fine.  I'm running Mythbuntu 10.10 (just upgraded yesterday).

Thanks,
Tim

---

### Post by klc5555 on 2011-01-28
> **tim273 said:**
> Hello Everyone,

If this specific thing has been discussed before, I apologize.  I have a working HVR-1600 which properly tunes both analog and digtal OTA ASTC.  Everything works fine (including the remote and blaster).  I also have a digital to analog converter box (apex) that I used to tune ota and there's a certian station that is far away that registers about 45 to 55 on the signal strength on the apex.  If the signal is 50 or above on the apex, it works fine on the 1600, As it drops below 50, I get increasing dropouts and buzzing on the 1600 (to the point where its unwatchable), while it's working fine all along on the apex.  

I know that there's some tuned drivers at Kernal Labs, but those are only for clearQAM not for ASTC.  Does anyone else have this problem?

All stations that have a signal strength above 50 are fine.  I'm running Mythbuntu 10.10 (just upgraded yesterday).

Thanks,
Tim

Since the 1600 handles OTA digital directly, or at least is supposed to, I'm surprised that you use an OTA digital-to-analog converter at all.

But in any event, the normal solution would be to use a small signal amp somewhere upstream of the card's input. Possibly between the card and the converter, or more likely between the converter and the antenna. Whichever works better.

---

### Post by tim273 on 2011-01-31
I think you misunderstood me.  What I meant was I used a converter box to check the signal strength since the signal strength indicator on the HVR-1600 doesn't work, it always shows 0% (that's another thing).  So I am connecting the HVR-1600 to a powered 4-way splitter which is connected to an antenna and the DTA converter is just for comparison (also hooked to the splitter).  The 4-way splitter says to not use a preamp.  

So to state the problem more clearly, the HVR-1600 is getting OTA digital but it cuts out on the slightly weaker signals that the DTA converter box plays just fine.  On the DTA converter box those signals display 45-50 on its signal meter. Is anyone else having this problem? Maybe it's time to throw out the HVR-1600 in favor of an HDHomerun?  Has anyone gotten the signal strength to work on the HVR-1600 for OTA ATSC?

I hope that clears it up.

---

### Post by tmcgary on 2011-01-31
Tim,

the hvr-1600 is known to be twitchy when it comes to its input signal strength requirements. See here:

[http://ubuntuforums.org/showthread.php?t=1584143&highlight=tmcgary](http://ubuntuforums.org/showthread.php?t=1584143&highlight=tmcgary)

I'm not sure of a solution for your particular situation.  I run mine with a four-way powered splitter and its works pretty well with Time Warner QAM signal out of the wall (no cable box). Good luck!

Tom

---

