---
title: "Nub 9.10 question"
date: 2009-10-26
forum: Mythbuntu
---

### Post by dacodo on 2009-10-26
So this weekend I finally expunged Windows from our house. The last holdout had been an ageing XP XBMC/BeyondTV HTPC driving our 52" LCD.

I replaced this with 2 systems: A Mac Mini running Plex (a feature enhanced XBMC port), and a Mythbuntu 9.10rc system for analog cable/OTA PVR/live viewing.

After struggling for hours yesterday getting the mythbuntu sound to finally work (had to install Pulseaudio volume controller, still have no idea why, but that's the only thing I could do to make it work.)

Here is my nub question.... 
I have the 9.10rc 90% the way I want it. Is there any advantage to reinstalling with the final release? Or can I just run the update manager and get the exact same result?

---

### Post by johnnybirdman on 2009-10-26
> **dacodo said:**
> 

After struggling for hours yesterday getting the mythbuntu sound to finally work (had to install Pulseaudio volume controller, still have no idea why, but that's the only thing I could do to make it work.)

Here is my nub question.... 
I have the 9.10rc 90% the way I want it. Is there any advantage to reinstalling with the final release? Or can I just run the update manager and get the exact same result?

Sounds like you spent yesterday the same way I did, but you were successful getting sound to work, I was not.

Updates should give you a complete/full 9.10 system without a full re-do.  That being said, I always feel better with a fresh system... just remember your settings.

any chance you can elaborate on your sound issue.  I can't get my onboard Realtek ALC883 (Intel motherboard) working.

---

### Post by klc5555 on 2009-10-26
> **dacodo said:**
> So this weekend I finally expunged Windows from our house. The last holdout had been an ageing XP XBMC/BeyondTV HTPC driving our 52" LCD.

I replaced this with 2 systems: A Mac Mini running Plex (a feature enhanced XBMC port), and a Mythbuntu 9.10rc system for analog cable/OTA PVR/live viewing.

After struggling for hours yesterday getting the mythbuntu sound to finally work (had to install Pulseaudio volume controller, still have no idea why, but that's the only thing I could do to make it work.)

Here is my nub question.... 
I have the 9.10rc 90% the way I want it. Is there any advantage to reinstalling with the final release? Or can I just run the update manager and get the exact same result?

Update Manager will take care of it. No difference.

You might still want to burn a final release CD to have on hand in case some unforeseen software meltdown happens at some point in the future. 

And, of course, always keep your mythconverg database backed up.

---

### Post by dacodo on 2009-10-26
> **johnnybirdman said:**
> any chance you can elaborate on your sound issue.  I can't get my onboard Realtek ALC883 (Intel motherboard) working.

I am using an older Asus K8U-X... Instead of trying to get those drivers working I put in a number of PCI cards including an old SB Live but I wasn't getting audio out of any of them, no matter what I turned on in the mixer.

I finally found some Google reference to someone having a similar problem and they installed the Pulseaudio volume controller and it fixed it. So I just loaded up synaptic and installed pavucontrol and all it's dependencies. 

Seemed to solve my problems. No idea why the alsa volume controller failed. (I've always been a Linux server guy, never messed much with this desktop side of things.)

---

