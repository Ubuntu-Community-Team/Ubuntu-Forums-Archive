---
title: "PixelView Pro Signal Faint in Feisty"
date: 2007-08-27
forum: Multimedia &amp; Video
---

### Post by JoseArmandoJeronymo on 2007-08-27
I have a PixelView Pro video capture card as below from lspci:

01:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
01:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
 
In order to have it working I created a bttv file in /etc/modprobe.d with the following lines:

options bttv card=37 tuner=5 radio=1 gbuffers=8 automute=0 gpiomask=0x3F audiomux=33,32,35,35,40 bttv_verbose=0
# first try autodetection, if it fail uncomment this line
options tuner addr=0x61

 I am in Brazil and we use the US-broadcst freq table here. System is PAL-M. The card captures composite and S-video all right but does not capture VHF from my SatTV tuner and shows but ghosts and "hissy" sound from local UHF stations which I see perfectly on my TVs).

I have tried fine tuning with no results. Is there any further adjustment or configuration parameters that could help?

Thanks in advance.

---

### Post by JoseArmandoJeronymo on 2007-10-08
To cut a long story short in case anyone has the same problem, I only solved the problem when I physically inspected the video capture card and discovered the tuner is one Temic NTSC (4032 FY5) of which maker I had never heard of.

I then created a file /etc/modprobe.d/bttv and put this on it:

options bttv card=70 tuner=6 radio=0 gbuffers=8 automute=0 gpiomask=0x3F audiomux=33,32,35,35,40 bttv_verbose=0

Then I turned the computer off for 2 minutes to make sure the "memory' in the tuner was erased.

The card works fine now.

---

