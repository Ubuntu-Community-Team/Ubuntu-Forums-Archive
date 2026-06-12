---
title: "Software Center Oddity"
date: 2011-01-11
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ratcheer on 2011-01-11
So, I just had to reinstall Natty. Yesterday, prior to the reinstall, I had installed Flash Player by downloading the .deb from Adobe, double-clicking it, Software Center came up, and I clicked the Install button. It worked like a charm.

Today, after reinstalling Natty, I tried to install it the same way. But, after clicking Install and giving it my password, it went back to the state of it still needing to be installed. I tried again with the same result. I re-downloaded the .deb file and still got the same result. I verified that it was not installed by examining my browser plugins.

Finally, I installed it manually with "sudo dpkg -i". That worked, successfully.

Any idea why I could install this file in Software Center yesterday, but not today?

Thanks,
Tim

---

### Post by ratcheer on 2011-01-11
Well, alrighty then.

Tim

---

### Post by efflandt on 2011-01-11
I have not used Software Center much yet because I am used to using Synaptic.  From that you can usually get flash by installing flashplugin-installer, or ubuntu-restricted-extras, which includes flash among other things.

But since I am running 64-bit, and 32-bit flash with the wrapper gives me some log errors, I typically install ubuntu-restricted-extras, uninstall flashplugin-installer, and then manually install real 64-bit libflashplayer.so after extracting it from the adobe tar.gz download.

I did try Software Center when it came up automatically when downloading 64-bit Hulu Desktop, but Software Center just came up with its general categories, not that file specifically.  I had to search Software Center to find Hulu Desktop when it was not in any of the categories I looked in.

---

### Post by mc4man on 2011-01-11
Just did a fresh install from .iso d'ed today and sc seems to not want to install any 'outside' .deb, not just adobe's flashplayer 
(though will install packages from the repo's

gdebi is faster and does work, am going to rebuild aptdaemon w/ a slight change and see if that's the reason (though not likely in this instance of a dl'ed .deb


Edit: it appears to be crashing ( and no apport though never have seen any yet when not root ), though it does work fine on a 1 week old install.

---

### Post by ratcheer on 2011-01-12
Thanks, guys. So, it would seem that .deb file installation through Software Center is currently broken.

efflandt, I usually install Flash Player in Firefox by clicking the presented link when Flash Player is first needed. But, that has been broken in Natty (apturl, probably due to the Ubuntu Firefox extension). Maybe it is fixed, now, but I had gotten used to downloading and installing the .deb file.

Tim

---

