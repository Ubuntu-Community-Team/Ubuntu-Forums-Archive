---
title: "A little lag, and sounds at higher frequency"
date: 2009-04-10
forum: Mythbuntu
---

### Post by sublimation on 2009-04-10
Hello all, this is my first Mythbuntu box, so bear with me if I'm a little green. I've got a combined backend/frontend with Mythbuntu 9.04, and a Kworld PlusTV capture card.
So after [a little tweaking]("http://ubuntuforums.org/showthread.php?t=884438") to get my Kworld PlusTV PCI card up and running, I got the backend running smoothly by following the typical setup steps.

When I run a direct stream program like TVtime I get perfect smooth video. Using the suggestion from the above link:
```
$arecord -D hw:1,0 -r 32000 -c 2 -f S16_LE | aplay -
```
I can get sound to play correctly, albeit not synced with the TVtime video, but correctly nonetheless. I'm not terribly interested in running TVtime, as I'm really looking to use Mythbuntu for my tv-watching/recording, etc.

When I run Mythbuntu's Watch TV command, voila, I get video and sound... but there are problems. The video seems to run, stop, run, stop, run, stop; as though it were trying to run things too fast, catching up with itself, and pausing again. while slowing down to .6x gives me what seems like a smooth, more or less realtime video, but with a little jumpyness. It's a little hard to tell, but that I can live with.

The sound however is the real issue. While everything is synced correctly, the sound is all at a higher frequency. Basically everyone sounds like they've inhaled helium. It's more than a little distracting. I've played around with setting the sampling frequency to no avail.

Is there anything I'm missing here that I should be setting to fix my troubles?

Any and all suggestions are always appreciated.

---

