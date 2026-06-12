---
title: "Suspected IVTV firmware/driver issues"
date: 2014-04-29
forum: Mythbuntu
---

### Post by bwatson on 2014-04-29
I've been a happy MythTV/Mythbuntu for the past several years.  Started with Myth 0.19ish and early Mythbuntu releases.

I've got a pretty rock solid setup: 1 primary backend/frontend, 1 secondary backend/frontend, and 1 frontend.  I think I last built these guys from scratch around the Mythbuntu 10.04 timeframe and have been slowly upgrading since then.  I think I last upgraded to the version that supported MythTV 0.25 so I could enable AirPlay.

So my secondary backend/front end crashed (suspected HDD issue) and I was forced to rebuild.  I had no idea where all my old discs were and, even if I could find it, the odds of finding active repos to upgrade again were slim.  So I decided to give 14.04 a shot!

The install was easier than I can remember with the older versions.  Probably 20 mouse clicks.  However, when it comes time to do some actual TV tuning, I get nothing but static/noise.

Both backends are equipped with 2x Hauppauge PVR-500 cards.  Not a single one of these 8 inputs can tune a single channel anymore.  The only thing that has changed in my setup is the version of MythTV/Mythbuntu (all hardware, coax cable connections, cable subscription, etc. are unchanged).

To date, I've:
[LIST]
[*]double checked the cable feed(s) by connecting the coax to a regular TV set --> works fine so I know the signal is there
[*]tried the whole "cat /dev/videoX > test.mpg" thing while using ivtv-tune to change channels --> nothing but static (a.k.a. "snow")
[*]tried the channel scan during Mythbackend Setup and I always get "Failed to find/add new channels"
[*]downloaded/installed Mythbuntu 12.04 --> same problem!
[LIST]
[*]This strikes me as "odd" because I thought I was around this version after several upgrades from the old 9/10.X days
[/LIST]
[/LIST]

There are other "issues" (e.g. NVidia stability issues on DVI-to-HDMI) that I'm still working, but I really want this tuning thing working.

What can I try next?  Is there a way to get older versions of IVTV (say from the 2010 or earlier timeframe) that I could load into 14.04?

Very Respectfully,

Ben

---

### Post by khPWXxF on 2014-04-30
Mythbuntu 12.04 is still available for download and had 0.25 Mythtv so should be compatible.

Hauppauge T500:  Did you turn on low noise amp and then power cycle the box (total power off)?

Phil

---

### Post by bwatson on 2014-04-30
> **khPWXxF said:**
> Mythbuntu 12.04 is still available for download and had 0.25 Mythtv so should be compatible.

Hauppauge T500:  Did you turn on low noise amp and then power cycle the box (total power off)?

Phil

Yes I've already downloaded Mythbuntu 12.04 after having issues with 14.04.  I've installed 12.04 on both backend machines and have the same issue.  I suspect I gradually "made it" to 12.04 after several distribution upgrades over the years, but we all know upgrading isn't the same as a fresh install and I feel that my IVTV settings/firmware/drivers/etc were carried over from upgrade to upgrade.

Hauppauge T500?  Not sure what that means unless it is analagous to PVR-500.

"Turn on low noise amp"?  What is that?  I'd be willing to give it a shot.  How do I do this?

I've power cycled these boxes several times, to include shutting of the PS and even pulling the power cord.


As a side note, because I've finally entered the HD age, I'm considering swapping the Hauppauge PVR-500's for HD Homeruns, which would likely render this entire discussion moot.  Anyone know how well Cox Communications plays with HD Homerun?

---

### Post by khPWXxF on 2014-04-30
Sorry - misread your original post.  The T500 is a pci card with dual DVB-T tuners.  It has a configurable signal amp;also loadable firmware which is only refreshed after a cold boot.  Not your device though.
Phil.

---

### Post by dannyboy79 on 2014-05-06
i am using xubuntu 14.04 with mythtv 0.27+fixes and my PVR-350 and PVR-500 both work just fine. Have you checked your dmesg output for ivtv errors?

---

