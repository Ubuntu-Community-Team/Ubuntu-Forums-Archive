---
title: "Is ubuntustudio-desktop needed?"
date: 2008-01-03
forum: Multimedia Production
---

### Post by J4DED on 2008-01-03
I wanted to upgrade my fresh 7.10 install of xubuntu with the audio apps as described at [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy/") :> sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rtI am wondering if I could just run:> sudo apt-get update && sudo apt-get install ubuntustudio-audio ubuntustudio-audio-plugins linux-rtDo I NEED to add the packages from ubuntustudio-desktop or is it okay to add just ubuntustudio-audio, ubuntustudio-audio-plugins and linux-rt *without* adding ubuntustudio-desktop?

---

### Post by logos34 on 2008-01-03
> **J4DED said:**
>  or is it okay to add just ubuntustudio-audio, ubuntustudio-audio-plugins and linux-rt *without* adding ubuntustudio-desktop?

I think you need to grab the 'ubuntustudio-audio' and  '-plugins' packages **separately** as listed here:
[https://wiki.ubuntu.com/UbuntuStudio/PackageList](https://wiki.ubuntu.com/UbuntuStudio/PackageList)

I think that's the way I did it originally (but my memory could be faulty because I installed studio a number of times before fully transitioning from vanilla gutsy)

---

### Post by MetalMusicAddict on 2008-01-04
> **J4DED said:**
> is it okay to add just ubuntustudio-audio, ubuntustudio-audio-plugins and linux-rt *without* adding ubuntustudio-desktop?

You can do that. We planed out things for exactly this situation.

---

### Post by dbsoundman on 2008-01-04
I did that on my laptop, because I wanted ubuntu studio programs on there but I didn't want to do a fresh install with ubuntu studio 7.04. I wanted to just upgrade, but the upgrade no longer exists for 7.04. So I found the program files on synaptic I believe and downloaded it all. Just search synaptic for ubuntu studio.

I did notice that the version of Ardour it gave me appears to be older...but I may upgrade that later by downloading directly from the Ardour website.

-Dan

---

