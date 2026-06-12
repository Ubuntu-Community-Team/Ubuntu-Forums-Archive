---
title: "tv out (nothing seems to work.)"
date: 2009-01-17
forum: Multimedia Software
---

### Post by Miles_Prower on 2009-01-17
I have an Nvidia GeForce4 MX4000 that I've been trying to convince to push video out to my tv. It's been frustrating. The card has an s video out on it, which is maked TV-OUT. Simply plugging the card into the tv does not produce an image; the tv and pc won't recognize each other. 
Tried [this]("http://ubuntuforums.org/showthread.php?t=98456"), [this]("https://help.ubuntu.com/community/NvidiaTVOut"), installed nvtv, could not get the *&%$&#% tv to display even a flicker. Scoured /etc/Xorg.conf and /var/log/Xorg*.conf for anything usefull, couldn't find anything. Is there a comprehensive guide to <strikethrough>banging your head against a brick wall</strikethrough> editing the xorg.conf for tv out anywhere? Hmm... Well... I guess... If I bought [this]("http://www.amatteroffax.com/itempagey_invid_1289053_d_graphics-cards-ati-radeon-9250-agp-wb-128mb-ddr-dvi-tv-out.html") and [this]("http://www.google.com/products/catalog?q=dvi+component&btnG=Search+Products&cid=10527616510705200140#ps-sellers"), I could run the component cables to the tv, then?

---

### Post by CarpKing on 2009-01-17
Have you tried setting it up via Nvidia-settings?  For me it was just a few clicks.  If you already tried that and it didn't work, I'm afraid I have nothing else.

---

### Post by Miles_Prower on 2009-01-17
tried that. It turned all my terminals into pure white rectangles. Couldn't type anything with the gui up. Deleted xorg.conf, replaced it with the backup,back to normal. 


SOLVED!

Put a claw hammer though the TV. Now it's not an issue anymore.

---

