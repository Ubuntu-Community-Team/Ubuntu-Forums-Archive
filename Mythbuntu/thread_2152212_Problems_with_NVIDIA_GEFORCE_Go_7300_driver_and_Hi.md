---
title: "Problems with NVIDIA GEFORCE Go 7300 driver and Hisense TV"
date: 2013-06-07
forum: Mythbuntu
---

### Post by prosmart on 2013-06-07
Greetings

I had my previous Mythbuntu setup working well but then I tried to upgrade :(

After getting things horribly screwed up with the machine hanging, not recognising the track-pad, not recognising that I had a TV, in the end I decided to re-install and that's when the fun (fun?) started.

Here's the setup.

Mythbuntu 12.04.2 on a Toshiba Satellite A100 with NVIDIA GEFORCE GO 7300. Display is via s-video cable to a Hisense TV Model HLS106T69PZ. No tuner yet - I'm testing with my ripped (legally!) DVD collection.

Previously, everything just worked (in a display sense). Now, regardless of which driver I try (currently using "Version Current"), the best I can do (on the TV) is 1024 x 768. It is capable of 1920 x 1080. As you might imagine, the way it looks at the moment is woeful.

Can anyone advise me as to how I should go about getting a better resolution than I currently have?

Happy to supply any further details that might be useful.

Be gentle with me please, Mythbuntu is rather new to me.

Thanks and Regards

Nigel.

---

### Post by BicyclerBoy on 2013-06-08
s-video does not support video modes higher than about 1024x768 & even that is way beyond the usable limit.
s-video is a usable match to SD DVD especially if the TV has a good scaler.

You might get better picture using some other lower video mode.

Can you use VGA ?..it is still capable of higher resolution & refreshrates than HDMI.. 

The 7300 has no h/w for video decode.

---

### Post by prosmart on 2013-06-08
Thanks for the input - much appreciated.

In a moment of desperation I uninstalled all of the restricted NVIDIA drivers and associated bits and lo and behold I got a much more watchable screen.

I'm putting this to bed for now until I can get the $$ together to build a halfway decent PVR box.

Cheers

Nigel

---

