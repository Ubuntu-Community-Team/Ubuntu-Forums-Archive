---
title: "Medibuntu no valid OpenPGP data"
date: 2009-01-21
forum: Multimedia Software
---

### Post by PoopyTheJ on 2009-01-21
I'm trying to add the medibuntu repo's and I've tried a number of commands and they all give me a pgp key error. This command wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
 gives gpg: no valid OpenPGP data found can anyone assist?

---

### Post by MrWES on 2009-01-21
> **PoopyTheJ said:**
> I'm trying to add the medibuntu repo's and I've tried a number of commands and they all give me a pgp key error. This command wget -q [http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg](http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg) -O- | sudo apt-key add -
 gives gpg: no valid OpenPGP data found can anyone assist?

This is from:

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")



```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by PoopyTheJ on 2009-01-21
Also running sudo apt-get update gives this

W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) hardy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

---

### Post by PoopyTheJ on 2009-01-21
thanks that appears to have fixed the authentication problem, but I'm still getting 
W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg](http://medibuntu.sos-sts.com/repo/dists/hardy/Release.gpg)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_US.bz2](http://medibuntu.sos-sts.com/repo/dists/hardy/non-free/i18n/Translation-en_US.bz2)  Could not resolve 'medibuntu.sos-sts.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


Any ideas?

---

