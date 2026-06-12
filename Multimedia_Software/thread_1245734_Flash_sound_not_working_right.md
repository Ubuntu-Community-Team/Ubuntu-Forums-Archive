---
title: "Flash sound not working right"
date: 2009-08-20
forum: Multimedia Software
---

### Post by mechaxl on 2009-08-20
Nevermind, I found this thread: [http://ubuntuforums.org/showpost.php?p=7205818&postcount=6](http://ubuntuforums.org/showpost.php?p=7205818&postcount=6) which solved my problem.


Hey,

So I was listening to pandora.com last night, and it worked great. I came back the next morning, and all of a sudden, flash videos and apps completely do not have sound. It's not a problem with soundcard, pulseaudio etc, as all other apps such as totem/rhythmbox work just fine. Now I remember having to fix this before by installing libflashsupport, and I went to go see if it was still installed. It wasn't installed, and when I went to install it, it had a dependent package that couldn't be installed. I went to check on that one, libgnutls13, and it gives me an error that says this:

Package libgnutls13 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

It looks like there was an updated version (libgnutls26), but libflashsupport doesn't support it, and I can't find an installable libgnutls13.

Does anyone know how I can fix this? I've got Ubuntu 9.04 32-bit btw

---

