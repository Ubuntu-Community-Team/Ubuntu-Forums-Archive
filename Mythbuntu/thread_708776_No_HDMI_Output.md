---
title: "No HDMI Output"
date: 2008-02-26
forum: Mythbuntu
---

### Post by Dragonflyoh on 2008-02-26
I have a Biostar Motherboard with Nvidia 7050 video built into the board. When connecting to my 37 Inch LCD monitor with the VGA connection all is fine. When I connect it with the HDMI cable I get nothing on the monitor. The posts I have been able to find about the subject mention using the Nvidia settings to correct the problem. I cannot get the settings as I get nothing on the monitor. My previous system had a Nvidia card with DVI output and I had the same problems with the DVI. I have a HD tuner that has DVI outputs and that works fine so I am sure the monitor is not the problem. I am thinking the problem is me but I don't know what I am not doing. Any help would be appreciated.

---

### Post by foxbuntu on 2008-02-28
Is this a DVI-to-HDMI Cable or Direct HDMI from the MOBO? If it is actually HDMI, I think the HDMI port support in the nvidia open source drivers  has not been fixed yet. If it is DVI-to-HDMI, there are known issues with many TV's no sending the correct information and the nvidia auto config will put the resoultion out of range. 

My advice is to stick with the VGA cable for now as much is not gained on a 720p TV as your max native resoultion is usually 1366x768 which is easily handled by VGA.

---

### Post by Dragonflyoh on 2008-02-29
Thanks for the help.

This is a direct HDMI on the motherboard and I am using a HDMI to DVI adapter.

I have found the cause of my problem, but not a solution. The Westinghouse Monitor has two (2) DVI connections and only one of them, DVI 1, supports EDID. My tuner was connected to the DVI 1 and worked fine. I tried connecting it to DVI 2 and nothing.

Somehow I need set up xorg.conf so it will have the correct modeline for my monitor and ignore the EDID errors.

The resolution on my monitor is 1080p.I am currently using VGA until I can get this corrected.

Do you have a reference for the Nvidia HDMI related problems? I may have issues beyond EDDI and my being a novice.

---

