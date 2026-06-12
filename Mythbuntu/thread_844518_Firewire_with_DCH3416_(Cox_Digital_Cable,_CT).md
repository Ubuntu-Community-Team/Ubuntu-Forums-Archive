---
title: "Firewire with DCH3416 (Cox Digital Cable, CT)"
date: 2008-06-29
forum: Mythbuntu
---

### Post by IgnacioMiller on 2008-06-29
Hey all,

I decided to take the mythtv plunge this afternoon. I downloaded Mythbuntu 8.04 live cd and installed it on a AMD Athlon 64 3600+, with a gig of memory and a Nvidia 7900GS for video out. I used the motherboards built in firewire connection to connect the mythbox to my Motorola DCH-3416, provided by Cox Digital Cable (Connecticut). After researching online for the correct settings to use with my provider, I changed the firewire capture card settings from 'point to point' to 'broadcast' and I was then transferring the signal perfectly.

However, not all is peachy. I have found three channels that will give me video so far, 1, 17 and 710. 1 is the cable's self-advertisement channel, where they tell you what's going to be on on-demand that week and such. 17 is pbs. 710 is the HD version of PBS Channel 1 works perfectly but channel 17's top row has misplaced pixels and is very 'laggy', the video skips around a lot and such. 710 works perfectly. I will continue to try more channels as the day progresses.

My only question is: How can I tell if the channel is encrypted or if there is something wrong with my configuration?

Thanks for such an awesome project in the form of Mythbuntu. It made it so easy to get my setup going, firewire and all. This would have been unheard of even a few months ago. Much kudos to the devs and volunteers!

Thanks,
Dan

---

### Post by IgnacioMiller on 2008-06-29
Channel issue resolved, but pixel issue remains on SD channels.

---

### Post by majoridiot on 2008-07-01
> **IgnacioMiller said:**
> Hey all,

I decided to take the mythtv plunge this afternoon. I downloaded Mythbuntu 8.04 live cd and installed it on a AMD Athlon 64 3600+, with a gig of memory and a Nvidia 7900GS for video out. I used the motherboards built in firewire connection to connect the mythbox to my Motorola DCH-3416, provided by Cox Digital Cable (Connecticut). After researching online for the correct settings to use with my provider, I changed the firewire capture card settings from 'point to point' to 'broadcast' and I was then transferring the signal perfectly.

However, not all is peachy. I have found three channels that will give me video so far, 1, 17 and 710. 1 is the cable's self-advertisement channel, where they tell you what's going to be on on-demand that week and such. 17 is pbs. 710 is the HD version of PBS Channel 1 works perfectly but channel 17's top row has misplaced pixels and is very 'laggy', the video skips around a lot and such. 710 works perfectly. I will continue to try more channels as the day progresses.

My only question is: How can I tell if the channel is encrypted or if there is something wrong with my configuration?

Thanks for such an awesome project in the form of Mythbuntu. It made it so easy to get my setup going, firewire and all. This would have been unheard of even a few months ago. Much kudos to the devs and volunteers!

Thanks,
Dan

[https://help.ubuntu.com/community/MythTV_Firewire/scanfw](https://help.ubuntu.com/community/MythTV_Firewire/scanfw) is a firewire scanner for encrypted channels.
a new version is forthcoming, but that one will get you going in the meantime.

as for the "pixel" issues, you can crop them off with the overscan settings in mythfrontend setup...
under "playback", i think.

---

