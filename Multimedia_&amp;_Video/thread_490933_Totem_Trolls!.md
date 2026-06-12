---
title: "Totem Trolls?!"
date: 2007-07-03
forum: Multimedia &amp; Video
---

### Post by ausmuso on 2007-07-03
Here's a curly one:
I have two pretty similar (homebrew) computers. One runs an AMD Athlon XP2600+ on a Gigabyte 7VT600, the other an Athlon XP2400+ on a Gigabyte GA-7VA motherboard. Both have 1GB RAM, same VIA chipsets, same Award BIOS, same AC97 sound, same NVidia cards, same make/model DVD (burner) drives.

Both run Ubuntu Feisty, installed from the same medium a few days apart. Both are loaded with the same slew of extra multimedia codecs and libraries. Under the circumstances you would expect Totem in both machines to digest DVDs the same way wouldn't you?
But would you believe:

Totem #1 treats DVDs by the book, including the DVD menu which you can call up anytime by clicking on the right pull-down whatsit. Totem #2 blithely ignores any menus and launches straight into the main DVD contents, whatever you try.

Whoever said PCs were predictable, rational things?

Old Croc

---

### Post by RomeReactor on 2007-07-03
Hi. Sounds like Totem #1 is **totem-xine** and Totem #2 is **totem-gstreamer**.

---

### Post by vpl on 2007-07-03
Hi, can anybody help me? How can I set the video driver in Totem??

Thanks:popcorn:

---

### Post by RomeReactor on 2007-07-03
Hi **vpl**. I'm not sure what you mean by driver; totem actually uses one of two backends (**xine** and **gstreamer**). That's about the only choice you've got there. If you are referring to this, then open Synaptic (System->Administration->Synaptic Package Manager) and search for either **totem-xine** or **totem-gstreamer**. I recommend totem-xine.

And welcome! :KS

EDIT: Post back if you have any doubts or more questions.

---

### Post by vpl on 2007-07-03
I'm using notebook IBM T40p in Docking Station and external dilsplay. When I play some movie I hear only a sound and black window instead of video. If put the notebook out from the docking station everything works perfect. I had the same problem with MPlayer. When I set the "Default video driver" to "vo=gl" in "mplayer.conf" it started work. I thing that with totem it will be similar.

---

### Post by RomeReactor on 2007-07-03
Unfortunately, with totem there's no option to select the video driver in its preferences. Sorry I can't help, I know next to nothing about configuring multimedia in laptops. Hopefully someone more knowledgeable will chime in with a fix to your problem. Again, sorry.

---

### Post by ausmuso on 2007-07-03
> **RomeReactor said:**
> Hi. Sounds like Totem #1 is **totem-xine** and Totem #2 is **totem-gstreamer**.

Thanks, Romereactor. This might well be the heart of the problem. I'll just uninstall the Totem#2 and then get Totem Xine through Synaptic.

All good clean fun! And if it doesn't work, there's always vlc!

Later: I DID IT AND IT WORKED! Totem #2 is now working by the book too.

Aren't Ubuntu Forums a wonderful thing?

---

