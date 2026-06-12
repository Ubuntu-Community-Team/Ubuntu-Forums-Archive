---
title: "Aspect ratio problem after hard reset due to failed suspend."
date: 2010-11-07
forum: Mythbuntu
---

### Post by heyho on 2010-11-07
Don't know if this has cropped up before, but I was wondering if there is a way to fix this without (another) reinstall.

Suspend and hibernate both fail on my (trial) backend machine.  I would like to get these functions working, but that'll be a different thread.

After attempting a suspend/hibernate, I end up with a blank screen and have to perform a hard reset.  Upon reboot, not only have I lost networking, but the aspect ratio of the playback is wrong - it is "letterboxing" 16:9 broadcasts, and I cannot get it back to how it was.  Desktop resolution is fine (1920x1080).  I have tried every menu and setup screen I can find, but to no avail!

---

### Post by stevobailey on 2010-11-09
Weird; I'm having exactly the same problem. I did a hard reset and ever since I can't get wide-screen working. the resolution I usually use doesn't display correctly on my TV anymore. The other one I've chosen (1360 x 768) displays the desktop as wide-screen but MythTV displays as stretched 4:3. Could it be possible that the hard reset has fried part of my video card? If so it's a bit of a coincidence that two people (both from Kent) have the same problem within a day of each other! Any help anyone can provide on this would be much appreciated.

---

### Post by stevobailey on 2010-11-10
I forgot to add that I tried this in both Lucid (my everyday OS) and Jaunty (a backup OS), and the problem exists in both. This leads me to believe that it's a hardware issue, but I'd like to know for sure. Also, the desktop displays in the correct ratio; only Mythtv (menus and playback) display in 4:3, despite updating the settings to force 16:9.

---

### Post by heyho on 2010-11-10
Well, I've done another re-install, and after a day of use I'm back to the letterboxed 16:9.

I've a sneaking suspicion it may be to do with my screen and connection method.  It's a no-name 22" LCD TV, connected via VGA, as that's the only option available at the moment.  It's a 1920x1080 panel, but it's only detected as 1440x900 for some reason, so I have to force it to native in nvidia-settings.

Desktop displays perfectly, so it's weird that the myth screen is now wrong again.  Even using "mythfrontend --geometry 1920x1080" makes no difference.  Also, I'm now also left with the top panel visible when the frontend is active.

All other frontends on the system are fine.  I plan to get a new graphics card with DVI/HDMI out anyway, so hopefully that will sort things out.

I hope it's not due to living in Kent!

---

