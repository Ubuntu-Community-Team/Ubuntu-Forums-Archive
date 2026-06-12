---
title: "Backend/frontend not communicating"
date: 2010-03-27
forum: Mythbuntu
---

### Post by meanmrmustard on 2010-03-27
After installing the Karmic version on my frontend only machine it no longer sees the Jaunty backend.

The "schema" is a different version on the two machines.
What needs to be updated on the Jaunty machine (or downgraded on the Karmic) that will allow them to see each other?
Is it the database that causes the conflict?

Karmic on the FE/BE is not an option.

---

### Post by ian dobson on 2010-03-27
Hi,

Every time there's new version of mythtv the dev's update the database schema (to include new setup uptions for new functions).

All mythtv systems that communicate with each other (Backend/Slave Backen/Frontend) must run the same version of mythtv and can only communicate with the same database version.

If you can't upgrade your backend then you'll have to downgrade your frontend or atleast the mythtv version running on the frontend.

Check what version of mythtv is running on your backend (0.21) and install the same version on your fronetnd. I think Karmic is using version 0.22, I'm not 100% sure.

Regards
Ian Dobson

---

### Post by klc5555 on 2010-03-27
You can download the Jaunty mythtv (0.21) packages from packages.ubuntu.com They'll run fine on Karmic.

If all you need is a remote frontend with no backend of any sort, then the critical packages are  mythtv-common and mythtv-frontend. The mythtv themes, plugins, and such-like are optional.

You'll need to uninstall _all_ the mythtv 0.22 packages from your Karmic machine, using synaptic or similar, then install mythtv-common and mythtv-frontend (0.21) using the GDebi installer. You may have to go back to the Jaunty section of packages.ubuntu.com to pick up a couple of small library packages to meet a dependency or two to get the main two packages installed. Once the packages are installed, "mythfrontend" from the prompt will fire it off and you can commence configuring, assuming the backend has been set up properly to accept connections.

You will also need to _lock_ the older mythtv 0.21 packages at some point using the lock function in Synaptic, so that every time Update Mangler pops up it doesn't try to upgrade your older mythtv packages to the current ones.

Or alternatively you can just download the Jaunty version of mythbuntu from the distribution archive section at ubuntu.com [http://cdimage.ubuntu.com/mythbuntu/releases/9.04/release/](http://cdimage.ubuntu.com/mythbuntu/releases/9.04/release/)

This is likely to be a simpler and more hassle-free solution, since Jaunty is still supported, and seems to be a more mature and solid version than Karmic. Unless your machine has ATI Radeon graphics --then sticking with Karmic 10.04 plus Mythtv 0.21 might be your easier option.

---

### Post by meanmrmustard on 2010-03-27
Thanks to you both for your replies.

With Lucid so near now it makes more sense to just go back to Jaunty for the FE machine.
Still, I appreciate the information!

Cheers

---

