---
title: "HD-PVR setup for questions"
date: 2010-12-29
forum: Mythbuntu
---

### Post by Sternfan on 2010-12-29
Hi all,

I've finally acquired a spare PC that is worth using for a Mythbuntu box.  Having never set this up, I have some Qs...

I assume the setup is:

Verizon Box
     |
composite cabling
     |
  HD-PVR
     |
USB to the Mythbuntu Box 
     |
HDMI output to TV (mythbuntu box has hdmi card)

Does that look right?  Am I missing anything?

Also - let's say I am trying to record channel 500 - do I set that on the Verizon cable box?  Or on the Mythbuntu box?  Can I watch one channel and record another?  Or does the HD-PVR only send whatever channel the Verizon box is set at?

Any help greatly appreciated,
Rob

---

### Post by newlinux on 2010-12-29
> **Sternfan said:**
> Hi all,

I've finally acquired a spare PC that is worth using for a Mythbuntu box.  Having never set this up, I have some Qs...

I assume the setup is:

Verizon Box
     |
composite cabling
     |
  HD-PVR
     |
USB to the Mythbuntu Box 
     |
HDMI output to TV (mythbuntu box has hdmi card)

Does that look right?  Am I missing anything?

Also - let's say I am trying to record channel 500 - do I set that on the Verizon cable box?  Or on the Mythbuntu box?  Can I watch one channel and record another?  Or does the HD-PVR only send whatever channel the Verizon box is set at?

Any help greatly appreciated,
Rob

Use component cabling instead of composite. Otherwise, that will work.

If for some reason you want cable passthrough to your TV independent of watching your cable box through mythtv (for recorded shows, Ondemand, or what have you) you may either want to connect your cable box directly to the TV via HDMI (you may run into HDCP issues with recording from the HD-PVR this way if your TV is off - some channels may expect the hand shake whenever there is an HDMI connection and will disable all inputs if it doesn't get one - my directv box did this) or use the component passthrough on the HD-PVR to avoid this problem.

You should setup mythbuntu to be able to control your cable box via IR blaster or firewire connection. Then you would give myth the channel and it would tune your cable box for you. Your HD-PVR will only record what the cable box would be sending to the screen (menus, info bars, and all). So if your recording something that's what you will have to be watching too on the directv box).

---

