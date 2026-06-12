---
title: "unable to skin VLC: package zips will not extract"
date: 2011-04-08
forum: Multimedia Software
---

### Post by kopiluac on 2011-04-08
Hi,
I recently downloaded vlc to my Linux OS distro Ubuntu 10.10.

I  love the player, but am unable to skin it. I have dl'd several packages  and they will not extract, even from root. Every time I attempt to  extract the .vlt files from zip, I briefly see the extraction progress  bar followed by this error: "An error occurred while extracting files." 

Thanks

---

### Post by wolfen69 on 2011-04-08
Are you trying to extract it by right clicking and *extract here*?

---

### Post by kopiluac on 2011-04-08
> **wolfen69 said:**
> Are you trying to extract it by right clicking and *extract here*?

Yes. I've tried every way possible. 

However, since posting this I've resolved the issue. Apparently, these .vlt files aren't meant to be extracted. For Ubuntu users utilizing VLC, simply download your preferred skin packages from videolan.org to your desktop and drag and drop them into the following directory: usr/share/vlc/skins2

Yeah, I know that the official whitepaper on this over at videolan says the path for Linux/Unix is ~/.local/share/yadda/yadda/yadda;)  Ignore that and use the path I've listed above if you're using Ubuntu 10.10. It might be that in earlier versions, but mine was in the usr path NOT the .local one.

Anyway, after you drag and drop your .vlt packages in, open VLC and navigate to tools/preferences. Tick the "use custom skin" radio button and then use browse to navigate to your preferred skin using the usr path I outlined in paragraph one (don't forget to save), or simply right click on the VLC media player and navigate to "interface/choose skin." From there you'll see a another menu expand with all the skins you've put into the skins2 directory. Choose a skin. Close and restart VLC to see your new skin in all its glory. NOTE: custom skins doesn't support the Advanced User Controls options like, Looping, and so forth. Only the default VLC engine supports that. So if you need the functionality of advanced user controls, save yourself the headache and don't use custom skins. I found this out the hard way. 

Good luck!

---

