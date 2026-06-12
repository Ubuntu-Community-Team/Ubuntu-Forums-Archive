---
title: "Wont play any media and wont update"
date: 2011-10-09
forum: Multimedia Software
---

### Post by jochba2 on 2011-10-09
i tried running banshee and it will open but when i try to play a song it wont start playing. i tried a video. same thing. i tried updating and i get this error:

W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) natty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783

please help

---

### Post by vajorie on 2011-10-10
The gpg error shouldn't be a problem, if I remember it correctly. It's just telling you that you have unauthenticated stuff in your apt settings (namely, the medibuntu repo). 

As for the banshee thing, try running

```

banshee --debug

```

from a terminal and pasting the output here (only the output when you hit play and it doesn't). It's most probably a problem with the codecs, so a quick

```

sudo apt-get install ubuntu-restricted-extras

```

should fix it.

---

