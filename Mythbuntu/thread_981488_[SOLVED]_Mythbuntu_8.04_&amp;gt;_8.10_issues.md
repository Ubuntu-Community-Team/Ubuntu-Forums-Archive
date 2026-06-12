---
title: "[SOLVED] Mythbuntu 8.04 &amp;gt; 8.10 issues"
date: 2008-11-13
forum: Mythbuntu
---

### Post by GuiGuy on 2008-11-13
I'm in Australia:

After what I thought was a reasonably clean upgrade, the following have come to light:

[LIST=1]
[*]SBS, a local free to air digital TV broadcaster,  does Not Record from Schedules
[*]ffmepg doesn't do xvid/ divx anymore
[/LIST]

SBS- While the program guide selections for SBS are working as expected, recording schedules are ignored. I'm at a brick wall on this now. 

ffmpeg- complains that 
> Your ffmpeg installation doesn't support encoding to xvid.
  (It must be compiled with the --enable-libxvid option)

It's frustrating because I've used ffmpeg for since I don't know how long and haven't encountered this before. Posts elsewhere say complete removal and re-install AFTER the upgrade should fix it. I tried that without success. I'm open to suggestions.

Thanks

---

### Post by Lindsay.Mathieson on 2008-11-24
> **GuiGuy said:**
> I'm in Australia:

SBS- While the program guide selections for SBS are working as expected, recording schedules are ignored. I'm at a brick wall on this now. 



Hi GuiGuy, you still having problems with this? I'm in Brisbane and recording SBS fine - Hope you didn't miss the new TopGear :)

---

### Post by GuiGuy on 2008-11-24
> **Lindsay.Mathieson said:**
> Hi GuiGuy, you still having problems with this? I'm in Brisbane and recording SBS fine - Hope you didn't miss the new TopGear :)

It's all good thanks. I had to rescan. 

Re topgear, didn't miss it but had already seen it. The interweb tubes and all that :)

regards

---

### Post by FakeOutdoorsman on 2008-11-24
You will need to use the [unstripped ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6197965&postcount=11") available in the Ubuntu multiverse repository.

Then, in your encoding command, change "-vcodec xvid" to "-vcodec libxvid".  Other encoder and option names may have changed as well.  You can see them all with "ffmpeg -formats".

---

### Post by Lindsay.Mathieson on 2008-11-24
Thats good guiguy, and thanks FODM

---

### Post by GuiGuy on 2008-12-06
> **FakeOutdoorsman said:**
> You will need to use the [unstripped ffmpeg libraries]("http://ubuntuforums.org/showpost.php?p=6197965&postcount=11") available in the Ubuntu multiverse repository.


Many thanks

---

