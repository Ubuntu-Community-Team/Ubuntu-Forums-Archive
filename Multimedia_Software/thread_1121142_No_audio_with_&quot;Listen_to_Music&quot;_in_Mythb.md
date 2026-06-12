---
title: "No audio with &quot;Listen to Music&quot; in Mythbuntu 9.04"
date: 2009-04-09
forum: Multimedia Software
---

### Post by daveisfera on 2009-04-09
I just ripped some CDs on an install of Mythbuntu 9.04, but when I go to "Listen to Music" I don't hear anything. I get audio when watching TV in MythTV and if I load up the files in VLC, then they sound just fine. Any ideas on what the issue could be?
Thanks,
Dave

---

### Post by daveisfera on 2009-04-09
I fixed this by changing the output device in Utilities/Setup->Setup->General->3rd page from "ALSA:default" to "ALSA:plughw:0,3" (where 0,3 is the card #,device # of the device I wanted to play sound with from "aplay -l").

Also, I noticed that the visualizations weren't working because none are selected by default. You can select them in Utilities/Setup->Setup->Media Settings->Music Settings->Player Settings->3rd Page->Edit Visualiazations.

---

