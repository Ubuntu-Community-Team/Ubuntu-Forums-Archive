---
title: "No picture via HDMI/Receiver"
date: 2010-04-19
forum: Mythbuntu
---

### Post by leeko on 2010-04-19
Hi,

I'm building my home theater around my mythbuntu box, a zotac IONITX-A-U with HDMI. But, I've run into an issue with no picture on my TV whenever I try to connect via my receiver. My setup is below:

1) PC: Zotac IONITX-A-U, builtin HDMI connected to
2) Receiver: Pioneer VSX-519V-K, connected via HDMI to
3) TV: Element 37" LCD flat-panel 

With this setup, I get a blue screen with "not supported" on the screen. It doesn't show any kind of picture getting through. When I connect the PC directly to the TV, the picture is flawless @ 1366x768x63Hz. 

I've tried 2 different HDMI 1.3 cables, but no difference. I tried both HDMI inputs on the TV, no joy. 

I'm not sure how to go about troubleshooting this; I could try editing the xorg.conf, but the TV doesn't give me any picture even in the BIOS, which should be running at a failsafe 640x480. 

Hoping someone can help! I'd like to use the HDMI passthrough on my receiver... 

Thanks in advance, 

Lee

---

### Post by rickg100 on 2011-06-17
Hey, did you ever resolve this. I have the same PC hardware, and am having the same problem.

When I hook the myth box up to my TV via HDMI it works fine. But if I do it through the receiver I get no picture.

Interestingly, if I start with it hooked up directly to the TV, wait for it to fully boot, and then change the cables so it goes through the receiver, then it works. But if I start with it hooked up to the receiver, I get nothing.

---

### Post by nickrout on 2011-06-17
It's probably an issue with the amp not passing edid info to the computer. Try connecting direct computer->tv and saving the edid info, then amend your xorg.conf to use that edid instead of whatever the amp is telling it to use.

---

### Post by rickg100 on 2011-06-21
This sounds promising, but I'm not sure how to do that - google searches have been close, but can't quite figure it out. Any tips?

---

### Post by nickrout on 2011-06-21
nvidia-settings has a function to save the edid information to a file,

Then in xorg.conf you need a line like:

Option "CustomEDID" "/path/to/edidfileyousaved"

---

