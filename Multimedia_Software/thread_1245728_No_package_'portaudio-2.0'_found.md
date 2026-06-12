---
title: "No package 'portaudio-2.0' found"
date: 2009-08-20
forum: Multimedia Software
---

### Post by victorbstan on 2009-08-20
I'm trying to install guvcview-src-1.1.3.tar.gz 1.1.3

from:

[http://developer.berlios.de/project/showfiles.php?group_id=8179](http://developer.berlios.de/project/showfiles.php?group_id=8179)

I hear its something to have when dealing with web cams...

but I get this error when trying to ./configure

```

No package 'portaudio-2.0' found

```

Alternativley I found instructions to installing it through ubuntu's package mannager at 

[http://guvcview.berlios.de/downloads.html](http://guvcview.berlios.de/downloads.html)

and as such it worked, so this isn't an emergency, but i'm quite puzzled, i've searched around the web and there's no such thing as: 'portaudio-2.0'

---

### Post by Yellow Pasque on 2009-08-20
You probably needed to install libportaudio-dev

---

### Post by ForgivenByJC on 2010-01-29
I had the same issue with gnaural.  The libportaudio-dev package did not work.

As counterintuitive as it sounds, installing **portaudio19-dev** solved this for me.  Counterintuitive because it is asking for "2.0" and this is marked "19."  Hope this helps somebody.

John

---

### Post by Bartje on 2011-09-11
Worked for me too, when trying to build the latest and greatest Denemo :-)

---

### Post by jacintodavila on 2011-12-01
It must be a sad coincidence: the program name is portaudio-2.0, bu the version is 19!..

 checking for module 'portaudio-2.0'
--   found portaudio-2.0, version 19

---

