---
title: "too many video packets in the buffer[...]"
date: 2006-07-07
forum: Multimedia &amp; Video
---

### Post by Bossieman on 2006-07-07
This is the very annoying error message I get from trying to play a DVD with mplayer
> 
Too many video packets in the buffer: (4096 in 8248919 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.


This starts about 10 seconds after the movie starts playing. I have searched this forums with out any solution for this. 
What can I do to solve this? Its very annoying.

DMA is enabled, I have a Aspire 1300, 256 Mb ram and a Savage card.

---

### Post by warjowuch on 2006-07-17
same here, on travelmate 212txv. Mplayer.
Does toten-xine work with your laptop? Mine crashes immediately after UI is fully rendered.

---

### Post by warjowuch on 2006-07-22
*bump* any others have this problem? Some solution out there, or is it just a too slow laptop for ubuntu? (WinME works with playing dvd's)

---

### Post by tseliot on 2006-07-22
1) Post the model of your graphic card

2) Did you install the driver for your graphic card?

3) Post the output of this command:
```
sudo hdparm -d /dev/hda
```
[B]
NOTE: replace "hda" with the name of your dvd player[/B]

---

