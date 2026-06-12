---
title: "No more sound!"
date: 2007-03-01
forum: Multimedia &amp; Video
---

### Post by Troubled on 2007-03-01
I've recently installed MPlayer on my Edgy distribution, but suddenly, on this boot up, it crashed. Along with this error, my system no longer plays any sound! Apparently whatever MPlayer used for output isn't capable of putting out any more sound, and MPlayer itself wasn't working.

So I ran make uninstall on MPlayer to see if it would resolve the problem, seeing as how it was dead anyways. It didn't. So now, I don't have MPlayer _or_ sound. Any suggestions on restoring my sound output? (My sound card seems to be fine, but going to System > Preferences > Sound and clicking Check just gives me errors.)

Help would be helpful, especially fast help. Help!

---

### Post by DrMega on 2007-03-01
You have tried restarting haven't you (sorry if that sounds patronising, but I've pulled my hair out over stuff that sorted itself out on a reboot).

The other thing is to see what is configured as your default sound card. I have a TV tuner card (which doesn't work incidentally, but that's another story), and on more than one occassion, Ubuntu (both Dapper and Edgy) have set its sound chip to be my sound card.

To check this out, go to System->Preferences->Sound and make sure it is set to the proper sound card/onbaord sound or whatever such config you have.

---

### Post by Troubled on 2007-03-01
Three or four consecutive restarts didn't help me.
I actually lost sound rather suddenly; I had it working fine yesterday. And everything seems to be alright; I've gone under System > Preferences > Sound, and it didn't help; I've opened the volume tool (from clicking the speaker icon on the taskbar twice), and it didn't help either.

I've even reinstalled MPlayer using Synaptic instead of manually, and now even MPlayer tells me that it can't load sound. What happened?

---

### Post by moore.bryan on 2007-03-01
*i had a similar issue with xmms because i had more than just alsa installed... have you tried specifying alsa as your output?*

---

