---
title: "Nvidia legacy installed, but no GLX."
date: 2007-04-26
forum: Multimedia &amp; Video
---

### Post by tjay on 2007-04-26
Hi everyone.

I've just installed Kubuntu 7.04. Artwork was good, mousewheel works without any tweaking, everything's just beautiful :) Congrats on a very nice release. Unfortunately, I did run into a problem, otherwise I wouldn't be posting here!

The first thing I installed was the nvidia-glx-legacy (7184) package with the Adept Manager. After that X wouldn't start but I edited my xorg.conf so that it read PCI:1:0:0 instaed of PCI:0:5:0 and it worked fine.

Then I tried glxgears but it didn't work. "GLX extension not available on display xxx". So I searched my Xorg.log again and only found 1 error relating to GLX/nvidia: "(EE) GLX is not supported with the Composite extension". Doesn't look to me like it's the problem...

I can't find anything on the forums for nvidia on feisty, and certainly nothing on a working X with missing GLX. The forum search function also seems to be down.

Anyone know's what might be wrong? (with my system not the forum search ;-) )

TJ

---

### Post by Tanker Bob on 2007-04-26
> **tjay said:**
> Hi everyone.

I've just installed Kubuntu 7.04. Artwork was good, mousewheel works without any tweaking, everything's just beautiful :) Congrats on a very nice release. Unfortunately, I did run into a problem, otherwise I wouldn't be posting here!

The first thing I installed was the nvidia-glx-legacy (7184) package with the Adept Manager. After that X wouldn't start but I edited my xorg.conf so that it read PCI:1:0:0 instaed of PCI:0:5:0 and it worked fine.

Then I tried glxgears but it didn't work. "GLX extension not available on display xxx". So I searched my Xorg.log again and only found 1 error relating to GLX/nvidia: "(EE) GLX is not supported with the Composite extension". Doesn't look to me like it's the problem...

I can't find anything on the forums for nvidia on feisty, and certainly nothing on a working X with missing GLX. The forum search function also seems to be down.

Anyone know's what might be wrong? (with my system not the foum search!)

TJ
What video card do you have?  Are you sure that the legacy driver set has the correct driver?  I've found that the only reliable list of supported cards for a particular chipset is in the README for each driver on NVIDIA's website.  Make sure that you match your chipset exactly in the README.  Some of the older cards especially have very similar designations for several variations.

I had this exact problem with my last video card, and it turned out that the support for it had been moved to a different driver package than indicated in the Ubuntu repository description.

---

### Post by tjay on 2007-04-26
Yes, my card is listed in the driver's README (in /usr/share/doc/nvidia-glx-...). It's a Geforce 2 MX.

Incidentally, I see that the README still says I have to remove 'Load "dri"' from my xorg.conf. Is this still required? It's also in the README's Q&A that if X works but OpenGL doesn't, then I should check my xorg.conf, by which I assume they mean this "load dri-load glcore" thing. In any case, I've tried it and it doesn't solve my problem. Rats...

TJ

---

### Post by tjay on 2007-04-26
> **tjay said:**
> So I searched my Xorg.log again and only found 1 error relating to GLX/nvidia: "(EE) GLX is not supported with the Composite extension". Doesn't look to me like it's the problem...

Hmm... Actually it does look like this is my problem. xdpyinfo lists NV-GLX but no GLX. Composite is listed too. How do I turn off the Composite extension? And what applications ill be affected by lack of that extension?

TJ

---

### Post by tjay on 2007-04-26
OK! I've found out from the freedesktop.org, nvidia unix drivers list, and gentoo-wiki websites that driver version 9631 will work with composite extension. And I see that package nvidia-glx in the ubuntu repo is version 9631. Gonna give it a shot now.

---

### Post by tjay on 2007-04-26
Woohoo! It works!!! I had to remove linux-generic and linux-restricted-etc and re-install them. Got that tip from another thread here.

Cheers! :)

TJ

---

