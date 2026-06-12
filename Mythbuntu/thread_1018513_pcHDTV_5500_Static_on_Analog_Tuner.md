---
title: "pcHDTV 5500 Static on Analog Tuner"
date: 2008-12-22
forum: Mythbuntu
---

### Post by Zerocool3001 on 2008-12-22
I recently installed a HD 5500 on a Mythbuntu 8.10 system. My intention is to use it as a replacement dvr (frontend and backend) with the option for moving it eventually to a backend position. While in a frontend position the only cable input is an analog one. Ive installed the latest v4l-dvb driver and configure two video inputs (they were auto detected), one as analog and one as digital.

When I perform a channel scan on the analog or digital inputs I get signals on some channels. However when I attempt to watch any analog channel, all I get it static and an occasional frame. I've tried everything I can think of. Any help would be appreciated.

---

### Post by calraith on 2008-12-25
> **Zerocool3001 said:**
> When I perform a channel scan on the analog or digital inputs I get signals on some channels. However when I attempt to watch any analog channel, all I get it static and an occasional frame. I've tried everything I can think of. Any help would be appreciated.

I have the same card.  That card has both an analog and a digital tuner, but only one can be open at a time.  When you set up the DVB tuner for QAM broadcasts, mythtv-setup defaults to leaving the digital tuner open all the time, rather than opening it on-demand.  So, when you go to watch analog broadcasts, the digital tuner is still active.

In mythtv-setup, go to Capture Devices --> DVB:0.  Go to Recording Options.  Check mark "Open DVB card on demand" and uncheck "Use DVB Card for active EIT Scan."  Finish, exit, and I believe all will be right with the world.  I don't believe this change will require you to re-run mythfilldatabase.

---

### Post by Zerocool3001 on 2008-12-26
> Check mark "Open DVB card on demand" and uncheck "Use DVB Card for active EIT Scan."

I do believe I've set the "Open DVB card on demand" option when I was originally attempting to use the digital tuner. Since I didn't touch the EIT settings, the "Use DVB card for active EIT scan" option should be off.

---

### Post by calraith on 2008-12-28
> **Zerocool3001 said:**
> I do believe I've set the "Open DVB card on demand" option when I was originally attempting to use the digital tuner. Since I didn't touch the EIT settings, the "Use DVB card for active EIT scan" option should be off.

Can you verify this information by actually opening mythtv-setup and looking in Capture Devices, rather than accepting all this on faith?  What is and what should be are often completely different.

---

### Post by jnorth on 2009-01-26
I learned the hard way that there are a couple of quirky things about this card.
1.  When setting up capture cards, you MUST set up the DVB side first.  If you have any doubt about which one you did, re-do it.  Set up the DVB card first, save, then go back in and set up a V4L analog device for the ntsc side.
2.  You have to place both capture cards from this card in the same input group.  I thought I had done this when setting it up, but for some reason it kept reverting to DVB on the DVB side, and Generic on the V4L device.  So - create a new input group and select it for both devices.  See screenshot below that shows this config page on page 2/2 in mythtvbackend-setup under Input Connections>DVB  (The page for the Input Connections>V4L-television input should be the same).

Hope this helps some... let me know if my directions are confusing, they often are, so I won't be offended.  ;)

Input Connections Screen - you need to go in to both the DVB and the V4L/Television inputs and make the change:
[ATTACH]101104[/ATTACH]

Input groups screen on page 2 after choosing to edit either the DVB or V4L/television input group:
[ATTACH]101102[/ATTACH]

---

### Post by jnorth on 2009-01-26
What that does, by the way, is restrict MythTV to only using one input at a time.  I thought it was doing that already since I had the "Open on demand" setting checked on, but it was not.  It was still getting confused about what card was what, once I set them up in the same group, no more problems.  I've been running this way for just over a week now with no issues.

---

