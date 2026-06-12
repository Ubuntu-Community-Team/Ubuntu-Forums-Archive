---
title: "ALSA 'arecord' / Lame elongating tracks"
date: 2013-06-29
forum: Multimedia Software
---

### Post by fairysdad on 2013-06-29
Those who browse different boards here may have seen my other thread on scheduling recordings.

Well that is done now (ish) and I'm looking at the recordings I've made - for trialling when I'm at home I've got a radio plugged into the line-in of my computer (where in practice it will be the feed from the studio of the actual radio station) tuned in to BBC Radio 4.

While checking the recordings, I've noticed that they're longer than they should be - a file that should be 1:34.00 long is actually 1:42.19 (also just checked, a 20 second one is just under 22 seconds). Because I've recorded Radio 4, who are notorious for tight timekeeping, I've got recordings of the [top-of-hour 'pips']("http://en.wikipedia.org/wiki/Greenwich_Time_Signal"). These show me that in 60 minutes, I gain 5m 18s. As the attached image shows, the two sets of pips are out of sync - the top one is from my automatic recording, the bottom ones from a file downloaded from the BBC website (unfortunately, I didn't get the final pip, but it still gives the idea!). They show that I gain an extra half-second for every 5 seconds.
[ATTACH=CONFIG]244265[/ATTACH]

Why is this happening? In the actual recording, there's no real audible difference; the pips do have a slight different tone to them - my recording is slightly lower, implying that for some reason either 'arecord' or Lame is slowing the recording down slightly.

The code I use for the recording is this (which is, mostly, sample code found from elsewhere)

```
arecord -f dat -d 5640 -t raw -D hw:0,0 | lame -r - myfile.mp3 --tt "Test Recording"
```

Annoyingly, given that I'm dealing with radio stuff at fixed lengths (for instance, using the recordings to automatically generate pre-recorded shows), the fact that I'm gaining time isn't really something I could look over, unlike other people who may be using this, so it would be quite useful to know what might be happening here!

This is using 12.04 Server.

---

### Post by fairysdad on 2013-06-30
Sorry, more double-posting...

I had a look at the code, and realised that with the '-f dat' bit in the code, I was recording at 48Khz, yet the MP3s that Lame produced were standard 44.1Khz. So I removed that; I also removed the -t raw so 'arecord' uses its default setting.

Now I end up with something odder - I now have the correct length recording (a setting it to record for 14 minutes actually produces a 14-minute file), but the sound is still off - BBC Radio 4's pips are still offset by the same amount...

:confused:

Anybody?

---

