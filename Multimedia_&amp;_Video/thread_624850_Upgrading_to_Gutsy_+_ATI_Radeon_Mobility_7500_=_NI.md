---
title: "Upgrading to Gutsy + ATI Radeon Mobility 7500 = NIGHTMARE!"
date: 2007-11-27
forum: Multimedia &amp; Video
---

### Post by asbesto on 2007-11-27
Well, I was very happy having my IBM Thinkpad T40 running BERYL, Emerald and everything accelerated. It was funny!

I upgraded Feisty to Gutsy.

SHAME ON ME, SHAME ON ME. HORROR ON ME.

After this, my X started with no window decorations at all. 

So I tried disinstalling beryl and emerald, and re-installing then via Synaptic.

this was UNUSEFUL.

SO I tried disinstalling and re-installing xserver-xgl. NOTHING.

SO I tried fglrx. NOTHING TO DO.

SO now it's a real mess. I don't have any DRI acceleration, my Xorg crashed, I had to reconfigure it by Xorg -configure, and lost my old config files. SHAME ON ME.

NOW i find IMPOSSIBLE to have the 3D acceleration I had with feisty.

I read every HOWTO in this board, without any result.

fglrx don't work - the package from gutsy repositories refuses to load giving strange libc6 error, and the ATI proprietary package, prepared in form of .deb package don't work. 

Can someone help please?

p.s. I SINCERELY HOPE UBUNTU is not going to become the new "gentoo" - following new releases without ensuring the compatibility with the past :( I think a bit of more testing before releasing will be a better solution for the next time :!

---

