---
title: "No libcec support"
date: 2012-04-14
forum: Mythbuntu
---

### Post by simbloke on 2012-04-14
Hi,

I just upgraded to 0.25 in the hope of getting HDMI CEC support as listed under the 'Key New Features' on the Mythbuntu site but it doesn't seem to be compiled in.

Anyone know if this is coming soon?

Sim

---

### Post by daveg on 2012-04-14
I was hoping the exact same thing too :-(

---

### Post by nickrout on 2012-04-14
what exactly were you expecting to see? Is there some functionality in your menus that doesn't work?

Have you read the tickets referred to in the release notes?

---

### Post by simbloke on 2012-04-14
> **nickrout said:**
> what exactly were you expecting to see? Is there some functionality in your menus that doesn't work?

Have you read the tickets referred to in the release notes?

The Myth TV packages do not depend on libcec and libcec is not in the mythbuntu repos (as far as I can see).

The cec-client will turn on my TV and select the appropriate input, MythTV does not.

The point is mute for me now as my adapter has died (again) :-(

Sim

---

### Post by tgm4883 on 2012-04-14
libcec1 is only available in precise. We're currently looking at backporting libcec1 to previous releases, but that takes time. The build process doesn't allow for having a build dependency for one release that isn't available on others, so it's disabled across the board. In other words, it's coming

---

### Post by simbloke on 2012-04-14
> **tgm4883 said:**
> libcec1 is only available in precise. We're currently looking at backporting libcec1 to previous releases, but that takes time. The build process doesn't allow for having a build dependency for one release that isn't available on others, so it's disabled across the board. In other words, it's coming

Oh I see, no problem. I updated MythTV in advance of updating to precise, which will be here soon enough anyway.

Sim

---

