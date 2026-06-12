---
title: "Unable to toggle tuners after 0.21 upgrade"
date: 2008-03-12
forum: Mythbuntu
---

### Post by r_endymion on 2008-03-12
I have two tuners installed:

/dev/video1
Leadtek TV Expert 2000 XP
/dev/video0
Hauppage WinTV PVR250

Since taking the upgrade, I can't view TV on the Leadtek card when I also have the Hauppage card enabled. When just the Leadtek card is enabled it works fine by itself, but with both cards enabled only the PVR 250 will display live TV, nothing happens when I press "Y" to switch tuners. I can, however, record from the Leadtek card.

I get the following errors in the terminal window when editing the settings for the Leadtek (V4L) card in backend setup:

```

Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
DiSEqCDevTree, Warning: No device tree for cardid 1
Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
Can't open DVB frontend (/dev/dvb/adapter0/frontend0).
DiSEqCDevTree, Warning: No device tree for cardid 1

```

Also, the tuner cards keep flip-flopping on reboot, /dev/video1 becomes /dev/vidoe0 and vice-versa.

I am a fresh green noob when it comes to Linux and this issue has me completely stymied.:confused:

---

### Post by r_endymion on 2008-03-12
Ok, I think that I have figured it out.

Prior to the 0.21 upgrade, I was able to use the same video source for both tuners, but now, apparantly, I cannot.

I created a new video source for the Leadtek tuner and can now view Live TV on either tuner once again.

---

