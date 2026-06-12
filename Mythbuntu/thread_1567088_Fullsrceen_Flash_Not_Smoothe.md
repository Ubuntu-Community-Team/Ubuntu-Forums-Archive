---
title: "Fullsrceen Flash Not Smoothe"
date: 2010-09-03
forum: Mythbuntu
---

### Post by ellisgen on 2010-09-03
So I got Mythbuntu up and running on one of these: eMachines EL1333G-03w. I wanted a low power quiet desktop to use for a front/backend and that is what I got. So far it does great with my HVR-2250 for recording ATSC programming and playing it back fullscreen in Mythbfrontend. 

I added Hulu Desktop so that I could watch my favorite sci-fi shows, but have found that any fullsrceen flash from Hulu, Youtube, or Dootv.tv is not quite choppy and doesn't quite stutter, but it is not smoothe either. I am currently using the integrated 6150SE with the proprietary video driver installed. I have one more PCI slot available.

The question is: Is my CPU just too weak to do this smoothly, or do I need a different driver for the video card, or can I get a newer video card (PCI not PCIe) and make it better?

---

### Post by LowSky on 2010-09-03
Flahs in Linux relies completely on the CPU. Adobe still hasn't made GPU acceleration availible for linux.

what you can try is lowering the resoluiton in which hulu desktop opens it might help the problem.
see here: [http://www.mythtv.org/wiki/Hulu_Desktop_Integration#Fullscreen_Performance_Issues]("http://www.mythtv.org/wiki/Hulu_Desktop_Integration#Fullscreen_Performance_Issues")

---

### Post by ellisgen on 2010-09-04
Thanks LowSky. That does appear to be the solution. The problem I am running into now though is that my video card and TV do not share many video formats, and of the ones that they do share, only the 800x600 format will actually display without my TV saying "No inputs". But at 800x600, my TV product page says it is SVGA for that and the picture appears to not have as many colors (like maybe 256 colors).

Other matching video sizes cause the "No inputs."

Got any ideas on this one?

---

### Post by LowSky on 2010-09-04
you can also go into the setting on hulu and lower the quality

user name>preferences> quality

---

### Post by Tteddo on 2010-09-04
> **ellisgen said:**
> So I got Mythbuntu up and running on one of these: eMachines EL1333G-03w. I wanted a low power quiet desktop to use for a front/backend and that is what I got. So far it does great with my HVR-2250 for recording ATSC programming and playing it back fullscreen in Mythbfrontend. 

I added Hulu Desktop so that I could watch my favorite sci-fi shows, but have found that any fullsrceen flash from Hulu, Youtube, or Dootv.tv is not quite choppy and doesn't quite stutter, but it is not smoothe either. I am currently using the integrated 6150SE with the proprietary video driver installed. I have one more PCI slot available.

The question is: Is my CPU just too weak to do this smoothly, or do I need a different driver for the video card, or can I get a newer video card (PCI not PCIe) and make it better?

FYI, I have a quad core Athlon and have the same issue, so it's not just horsepower. Just started looking into this today.

---

