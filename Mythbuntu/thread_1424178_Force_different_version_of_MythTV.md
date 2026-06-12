---
title: "Force different version of MythTV"
date: 2010-03-07
forum: Mythbuntu
---

### Post by stormb on 2010-03-07
Dear all,

Hope you can possibly help me. Here's the scenario - I've got an existing MythTV set up using Mythbuntu 9.10 (a FEBE and another FE). It's using the default version of Myth included with that 9.10 (0.22+fixes).

I've just discovered Lubuntu 10.04 alpha 3 which nicely installs on my Eee PC 2G Surf (and not many distros do!).

I had hoped I would just be able to 'apt-get install mythtv-frontend' to use my little Eee as a frontend, but unfortunately it appears to have installed a far newer version of MythTV than I want, and claims the DB schema is 10 versions newer.

Is there an easy way to force my Lubuntu 10.04 install to use the same version of Myth that is on my network?

Thanks in advance,

Will

---

### Post by klc5555 on 2010-03-07
If all you want on the 10.04 machine is a frontend, then it should only have mythtv-common and mythtv-frontend on it; no backend or database should be needed.

Otherwise, with alpha code, you're lucky if anything runs at all. But if really necessary, it's also possible (but not certain) that 10.04 may be able to install and run the older .deb packages from 9.10.

To do so, if the 10.04 machine is intended to function as a frontend, remove its current version of mythtv, and then download the Karmic versions of mythtv-common and mythtv-frontend from packages.ubuntu.com with your browser. Try to install the packages with the Gdebi installer. You might have to go back and get packages for unfulfilled dependencies, if the Gdebi installer finds any. The older packages may or may not install ; the installed packages may or may not run. If they run, configure the frontend as you would any remote frontend, and you may be lucky.

If the older packages run satisfactorily, you'll need to lock them by using the Synaptic package manager, so that the machine doesn't try to replace them with the current version every time you do an update.

---

