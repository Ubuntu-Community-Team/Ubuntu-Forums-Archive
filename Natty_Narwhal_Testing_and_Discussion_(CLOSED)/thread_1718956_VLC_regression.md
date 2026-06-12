---
title: "VLC regression"
date: 2011-04-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by beew on 2011-04-01
There was an annoying problem with VLC in Lucid (regardless of VLC version), when it plays certain mp3 files there is a short hiccup sound in the beginning, it is very brief and only happens with certain files, but annoying enough that I thought of uninstalling VLC in Lucid. That problem went away in Maverick but apparently has now returned to Natty. I haven't been able to find a way to fix it in Lucid, so I don't expect to be able to fix it in Natty either. Just very disappointed.

---

### Post by bikeboy on 2011-04-01
Using ALSA or pulse as the output module? Might be worth swapping to see if it's an issue with one or the other. Pretty hard to fix a problem when most people aren't affected and thus don't know it exists. I will try to reproduce it when I get Natty installed (planned for a netbook soon) but certainly don't remember that issue on Lucid.

Edit: I should have said, I'm referring to the setting within VLC itself, not a gnome setting. It's in the basic settings under Audio.

---

### Post by beew on 2011-04-01
> **bikeboy said:**
> Using ALSA or pulse as the output module? Might be worth swapping to see if it's an issue with one or the other. Pretty hard to fix a problem when most people aren't affected and thus don't know it exists. I will try to reproduce it when I get Natty installed (planned for a netbook soon) but certainly don't remember that issue on Lucid.

Edit: I should have said, I'm referring to the setting within VLC itself, not a gnome setting. It's in the basic settings under Audio.

Hi,

In Lucid if I set the output to ALSA the hicup sounds go away but after about 10 minutes there wouldbe no sound at all so that was not an option. With pulse it was the same story,--no hicup but silent after a while,-- if I remember correctly. With OSS the hicup was even louder.

I should add that in Natty it wasn't as bad as in Lucid, the hicup was shorter and not as loud, also in both Natty and Lucid it only happens with  some MP3s (the same ones) But in Maverick all MP3 play fine.

At some point the hicup  went away in Lucid but was replaced by something worse, VLC could not play fullscreen without freezing, that was independent of VLC version and I tried a portable version of VLC and there was not change. It seems like a Lucid problem rather than VLC.

Thanks for the response anyway.

---

