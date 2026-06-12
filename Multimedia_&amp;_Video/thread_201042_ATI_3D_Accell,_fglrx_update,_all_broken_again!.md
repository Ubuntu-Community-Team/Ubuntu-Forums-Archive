---
title: "ATI 3D Accell, fglrx update, all broken again!"
date: 2006-06-21
forum: Multimedia &amp; Video
---

### Post by bohboh on 2006-06-21
My system updated itself, to which i clicked install without checking to see what it was installing ](*,) , alas all my past days effort to get ati radeon 9200 pro with 3d accelleration was wasted. I managed to get it to work but the update broke it again. 

fglrxinfo is back to MESA and fps is between 100 - 200.

How can i undo the update and fix this?

---

### Post by glotz on 2006-06-21
Do you have the restricted (meta) package installed? It would automatically update in sync with your kernel.

---

### Post by bohboh on 2006-06-21
[QUOTE=glotz]Do you have the restricted (meta) package installed? It would automatically update in sync with your kernel.[/QUOTE]

I uninstalled linux-restricted-modules-2.6.15-25-386  and went to reinstall them as per a thread regarding this issue.

I get :

```

linux-restricted-modules-2.6.15-25-386:

Package linux-restricted-modules-2.6.15-25-386 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list
```

How do i reinstall it? I have reinstalled it many times before but for some reason i have started getting this.

FIXED: Needed to enable repos in synaptic

---

### Post by glotz on 2006-06-21
I bet you'd do better with the 686 kernel, unless you really are on *ye olde legacy* hardware! See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

And, what you installed is a single real package, that won't upgrade. Uninstall it and install the meta package,  linux-restricted-modules-386 (or ...-686 when you've seen the light about kernels... :) )

And it won't break no more in the foreseeable (is that a word?) future!

EDIT: typ0s

---

### Post by bohboh on 2006-06-21
[QUOTE=glotz]I bet you'd do better with the 686 kernel, unless you really are on *ye olde legacy* hardware! See [http://www.ubuntuforums.org/showthread.php?t=85917](http://www.ubuntuforums.org/showthread.php?t=85917)

And, what you installed is a single real package, that won't upgrade. Uninstall it and install the meta package,  linux-restricted-modules-386 (or ...-686 when you've seen the light about kernels... :) )

And it won't break no more in the foreseeable (is that a word?) future!

EDIT: typ0s[/QUOTE]

Ok, i have installed K7 linux image, (athlon xp) and have uninstalled my restricted modules, what is the exact name of the ones i need for 686? tried and couldnt find linux-restricted-modules-686

Edit: found it, needed my version (uname -r)

---

### Post by bohboh on 2006-06-21
Sorted! Hoooray!

---

### Post by glotz on 2006-06-21
:)

---

### Post by bohboh on 2006-06-21
Is there a way i can lock the version to prevent any further updates?

---

### Post by Galban on 2006-06-21
[QUOTE=bohboh]Is there a way i can lock the version to prevent any further updates?[/QUOTE]

To blok fglrx to be updated, open Synaptic, search for fglrx. Left click on xorg-driver-fglrx just to mark it, then on the Package Menu make chek up on "Lock Version". Same thing for fglrx-control and all other already installed fglrx's related package.

---

