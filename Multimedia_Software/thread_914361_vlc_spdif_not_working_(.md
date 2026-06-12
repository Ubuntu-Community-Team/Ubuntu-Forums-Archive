---
title: "vlc spdif not working :("
date: 2008-09-08
forum: Multimedia Software
---

### Post by at0mic on 2008-09-08
Hi,

Im trying to get VLC spdif audio to work and it just wont. totem doesnt have a problem or rythembox... ive tried all output modules and have selected " spdif if available" but it just wont output any sound... helP for the love of linux?

---

### Post by roadrun777 on 2008-09-08
I am curious about this as well.
I know exactly what the problem is that your having, but I don't know enough about linux to help you.
Linux enumerates the different features of a sound card using different methods. Each sound daemon enumerates differently.

The sound system of *nix has always been mysterious to me, since there isn't much documentation on it.

You should figure out what your sound card is, and which driver it is running. For example, my sound device only has an ALSA driver available. So in VLC I always make sure to force it to use ALSA.

If someone could explain how to find out the sound card feature enumeration and alias list, then you could easily type that into the output device in the VLC config. Which should force it to use the SPDIF.

Even if you can't change the device using the configuration menus, you might be able to change it via command-line or it's configuration file (usually in .VLC). As a last resort you could download the source code, and try to figure out how / what / or where it links to the SPDIF in the code. It might be as simple as just renaming a device name in the code from something like "SPD1" to "SPDIF1" and recompiling. That's just an example though.

I wish someone would port AC3filter for ubuntu and add a feature to it that lets you make an spdif "alias" device so that no matter what program you use, if you connect it to this 'device alias' it always uses AC3filter as the spdif source. Then on the front end make the port aware of OSS, ALSA, and Pusle spdif device names, along with a special linux sound config panel. The thing I love about ac3filter is that you can take a multi-channel source, say 5.1 channel sound, and convert it to another format like dolby pro-logic or vice verse. It also lets you control the sound matrix mapping, so you can pipe specific channels to specific speakers, which even the most expensive head units are lacking of this feature.

---

