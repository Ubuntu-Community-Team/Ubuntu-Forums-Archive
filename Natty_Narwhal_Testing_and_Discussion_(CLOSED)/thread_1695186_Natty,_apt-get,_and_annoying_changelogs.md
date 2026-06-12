---
title: "Natty, apt-get, and annoying changelogs"
date: 2011-02-25
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by msp3k on 2011-02-25
Dear Ubuntu gurus,

I've been working on poring my packages to natty, in preparation for the upcoming release.  One of the things I have noticed recently is that apt-get, when called from the command line to perform upgrade or dist-upgrade, keeps displaying changelog text in a pager and waiting for me to exit the pager before continuing the upgrade.

This is a royal pain in the rear for my automated scripts.

This didn't used to be the behavior.
How do I turn this off?

Thanks in advance

---

### Post by msp3k on 2011-02-25
Think I figured it out: --quiet seems to do the trick.  Changelog information is still printed to the screen, but no human interaction is required.

---

### Post by uRock on 2011-02-25
It is always best to ask about Natty in the Natty forum.

Moved to NNT&D.

---

