---
title: "ATI 9550 AGP on Gutsy"
date: 2007-11-28
forum: Multimedia &amp; Video
---

### Post by Gzus666 on 2007-11-28
ok, fresh install of Gutsy a few days ago. got my network up today, and i followed this guide for the video card:[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

when i try to do the restricted drivers method, it tells me i need to fix the dependency. when i run:  sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable

not sure why it wants an old version of a C++ compiler, anyone got any ideas here?

---

### Post by Gzus666 on 2007-11-28
anyone have any ideas?

---

### Post by Gzus666 on 2007-11-28
Still trying to pin this one down with no luck, anyone?

---

### Post by Yellow Pasque on 2007-11-28
what happens when you do :
```
sudo apt-get install libstdc++5
```
?

---

### Post by Gzus666 on 2007-11-29
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate

is output on that command. so, it seems i need to get rid of a dependency between them since it doesnt seem to exist, right? bear with me, still getting used to Linux file system, and how it manages things.

---

### Post by Gzus666 on 2007-11-29
well, did some package manager searching, getting a feel for things. what im seeing here is i have libstdc++6 rather than 5 already built in. why is this trying to use an older compiler? the only thing i could think i would have to do would be change the dependency from trying to use 5, over to 6. would this be something possible? im not sure where dependencies are stored and changed at this point. if someone could point me in the right direction, i could probably figure this out

---

### Post by Gzus666 on 2007-11-29
ok, now in the package manager i see the fglrx dependencies, and it wants that older compiler. i assume this was overlooked when they changed to the new version of Ubuntu...any way to either change this dependency to the new version, or get the old version?

---

### Post by Gzus666 on 2007-12-01
anyone? still fighting with this, ive tried a bunch of other things, and still no luck

---

### Post by devosion on 2007-12-01
I noticed in the second error message you are getting a call to what I assume is a cdrom drive. When you reinstalled Gutsy did you check the software sources and make sure at least the first 4 were checked?

---

### Post by Talon2 on 2007-12-01
> **Gzus666 said:**
> anyone have any ideas?

I run  a ati 9600 agp.

Why is it you are trying to install the binary blob from ati?  The open source radeon driver works very well here.  Even Compiz by default.

---

### Post by Gzus666 on 2007-12-01
well, i have to install the driver, as what is there does not let me use compiz in any way. im betting what you think was working as radeon was actually it getting the driver on its own when you enable the card. unfortunately mine wont do that, since it has a compiler that doesnt match the one i have.

---

### Post by Gzus666 on 2007-12-01
just realized i forgot state im using 64 bit version

---

### Post by Gzus666 on 2007-12-01
tried installing the old gcc 3.3 package, and it stated i could not run both at the same time. still no luck with this

---

### Post by Gzus666 on 2007-12-01
ok, i have an idea, need to see if im on the right track here. if i make a fake file for the lib it needs, the link it to the new lib i have, would this help? i need help figuring out the correct name for the old one, as i have tried a few times, and havent been successful

---

