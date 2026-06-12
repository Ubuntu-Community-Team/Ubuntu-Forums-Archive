---
title: "WMP Track Tagging - Ubuntu Alternative?"
date: 2010-01-08
forum: Multimedia Software
---

### Post by manco on 2010-01-08
I made the switch to all Ubuntu and I'm loving it.

One of my favorite Windows features was in Windows Media Player.

If I added an audio track to WMP, I could search within WMP (using internet) to find the album info.

It was something like, right-click, "Find album info"

It was a really great feature, and I'm looking for something like it on Ubuntu.

Anyone have a suggestion?

Thanks

---

### Post by newb85 on 2010-02-05
First off, welcome to the world of freedom!

Your answer will depend on what program(s) you use to replace your old friend WMP.  

I recommend Rhythmbox  for everything except ripping, because it should have basically all the same capabilities.  Rhythmbox will rip CDs, but you basically have no options, and it's really slow.  Instead, I recommend the use of Sound-Juicer (which you can install through Synaptic) for ripping.

That said, Sound-Juicer should automatically download album info from the web.

Oh, and by the way, if you are trying to rip into .mp3 format, you'll also need to install the packages libavcodec-extra-52 and gstreamer-plugins-ugly-multiverse.  This will require you to first enable the Multiverse repository (In Synaptic: Settings->Repositories).

Good Luck!

Edit: Actually, Rhythmbox will not play video.  I forgot that difference.

---

### Post by newb85 on 2010-02-05
You might also consider installing EasyTag.  It's very helpful when you don't like the automatically populated labels.

---

