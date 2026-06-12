---
title: "Nvidia 173/180 driver causing low volume?"
date: 2009-05-09
forum: Mythbuntu
---

### Post by gwagchunks on 2009-05-09
Hi Everyone

I'll try and keep it short! I have loaded 9.04 mythbuntu. TV playback was choppy but volume was perfect. I loaded Nvidia driver 180, rebooted, then picture is great, but volume really low. I checked volume settings with aumix and mixer and made all 100, no joy. I reloaded 9.04 again, same result, volume good, picture choppy. I then tried Nvidia driver 173, same as the 180 picture great, volume low. If I turn speakers to full, just about hear TV but lots of hiss. Any ideas please? 

Thanks
Mobo: gigabyte EP31-DS3L (using AC audio not HD) 
TV cards: (happauage nova td-500 and pvr-150)

---

### Post by DominicF on 2009-05-11
Hi,

I've been playing with mythbuntu 9.04 and Nvidia drivers and I too noticed somethig odd with the volume i.e. being low.  But haven't got round to do any further checks.

---

### Post by gwagchunks on 2009-05-11
Thanks for the reply DominicF

Sorry you have the issue too, at least I know it's not me going mad! I'm going to try 8.10 and see if this has the same issue. I went to 9.04 as I couldn't get DVD playback to work properly, but I think I know what to do now. I'll try tomorrow and report back what I find.

Thanks
Mobo: gigabyte EP31-DS3L (using AC audio not HD)
TV cards: (happauage nova td-500 and pvr-150)

---

### Post by nickrout on 2009-05-11
> **gwagchunks said:**
> Hi Everyone

I'll try and keep it short! I have loaded 9.04 mythbuntu. TV playback was choppy but volume was perfect. I loaded Nvidia driver 180, rebooted, then picture is great, but volume really low. I checked volume settings with aumix and mixer and made all 100, no joy. I reloaded 9.04 again, same result, volume good, picture choppy. I then tried Nvidia driver 173, same as the 180 picture great, volume low. If I turn speakers to full, just about hear TV but lots of hiss. Any ideas please? 

Thanks
Mobo: gigabyte EP31-DS3L (using AC audio not HD) 
TV cards: (happauage nova td-500 and pvr-150)

Tell us more - how are your speakers connected? spdif? analogue? hdmi?

And to what? powered speakers? digital amp? tv?

---

### Post by codymyth on 2009-05-11
The same exact thing happend to me. I install updates and i lost my sound. to try and fix it i maxed all my volume mixers and maxed my volume on my surrond sound and could just barely hear a sound.

I have my speakers hooked up through the headphone jack and then into the red and white rca ports on home theather system

---

### Post by gwagchunks on 2009-05-12
Hi Codymyth

Sorry yeah should have posted that! I have a pair of Antec Lansing powered speakers (with a lime green plug on the cable) plugged into the "lime green" socket on back of the mobo. I have tried every other socket (has 5 other sockets for sub woofer/mic etc) but no joy. I do not have a receiver so I'm not using spdif/digital. I have it setup to dual boot to windoze and the sound is fine there. It's also fine in 9.04 until I load the Nvidia driver (I have a Asus Nvidia EN8500GT pci-e card). I too tried maxing all the volume levels with alsamixer etc to 100, but no change. I will try 8.10 tonight and see if it does the same thing, unless there is something anyone can suggest. 

P.S. The mobo manual says it has Realtek ALC888 codec, Hi def audio, 2/4/5.1/7.1 channel, suppoort for spdif in/out and cd-in

Thanks

---

### Post by nickrout on 2009-05-12
you have to make sure that not only are they set to 100% but also that they are not muted.

---

### Post by gwagchunks on 2009-05-13
Hopefully this is working now. I loaded 8.10 from scratch, volume OK, video choppy. Loaded nvidia 1.73, video good but volume low, tried nvidia 1.77 video good, volume low. Went to alsamixer, made everything 100 not muted. Volume was a little bit better, went back to alsamixer most levels back at around 70. I Googled about a bit and then set levels and then tried 'alsactl store'. Volume better. Then (slap head moment!) I found the keyboard shortcut for volume (square braces on the keyboard []) and made volume 100 and it's all good! :) Might have tried this sooner if I had a working remote... still working on that. I may get around to seeing if this is a fix for 9.04 but as this is the best I have gotten Myth to work - if it aint broke I'm not gonna fix it! Thanks to everyone for their suggestions, hopefully this thread will help someone.

---

