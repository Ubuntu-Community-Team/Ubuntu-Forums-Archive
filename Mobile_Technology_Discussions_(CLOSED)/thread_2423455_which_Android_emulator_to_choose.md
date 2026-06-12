---
title: "which Android emulator to choose"
date: 2019-07-23
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Skaperen on 2019-07-23
i have been looking at a lot of online descriptions of various Android emulators.  but i want one that actually runs the real OS images that are normally run on Android ARM CPUs, as opposed to the one i looked at a few years ago that did some kind of x86 based fakery that didn't use real ARM code.  it should be an emulator of actual ARM-based Android hardware with the ability to use selected files for any read-only memory and preload an OS from the upgrade images people can download for their devices.  none of the emulators i have seen described get detailed enough to know what they really do in this respect.

---

### Post by #&amp;thj^% on 2019-07-23
You never mentioned which you have looked at, so I'll just post a link to 10 emulators.
Bare in mind the term "Emulators" is just that.
[https://www.ubuntupit.com/top-android-emulators-for-linux-to-enjoy-android-apps-in-linux/](https://www.ubuntupit.com/top-android-emulators-for-linux-to-enjoy-android-apps-in-linux/)

---

### Post by Skaperen on 2019-07-24
that's actually one of the sites i already looked at.   too many people out there play loose with terminology.  the term "emulator" has been used with things that are not machine level emulators.  many of them are just an implementation of the API allowing app developers to compile their code on an x86 and run their tests there.

i've spent much time trying get things working for some project in the past only to find all that time was wasted because it really wasn't what they described.  so i've learned to get enough details to prove something is the case before spending any time on it.

---

### Post by ligernam on 2019-08-04
what do you think about Bluestack emulator?

---

### Post by Skaperen on 2019-08-04
at the moment i think nothing of it.  i need to find it first.

---

### Post by Skaperen on 2019-08-04
found it.  reading about it.  while it would certainly be emulating the ARM instruction set as it runs actual apps that run on Android, the technical descriptions, though vague (as if written by a semi-technical person), it seems to suggest it is emulating the Android OS itself, not the machine.  what i am wanting is like the "system" versions of QEMU, e.g. an emulator that can run the OS.  in this case i want to run the Android OS itself, simulating a telco service with only internet (using the host internet).  i want to be able to run different versions of the Android OS (a few in parallel if i have enough resources).

---

### Post by bijayalaxmi1808 on 2019-10-01
Android Studio has it's own built-in emulator where you can choose any device type such as: screen size, etc. to emulate Android on that device.

Typically there are many [Android emulators available for Windows]("https://www.cyanogenmods.org/best-android-emulators-for-windows-pc/") which will allow you to run Android and can be installed as a windows application. But from your last reply it appears to be you wanted to install Android on a virtual machine or something similar, correct me if I am wrong.

Can you please share the link which you said you "found it", so that I can also go thorughand understand new possiblities of Android emulator usage?

---

### Post by Skaperen on 2019-10-03
Genymotion might be a true hardware emulator.  this page just doesn't have enough detail to know.  what might help is a different name for the hardware platform that the Android OS is intended (distributed) to run on.  then i would search for an emulator of that platform name.  i read, somewhere, that someone ported some version of Debian to smartphone hardware.  a proper emulator could run that.

---

### Post by bernard010 on 2019-11-28
**Thanks for the web link '1fallen' posted. **I found Anbox. . works with games on other OS's.
Thank You very much.

---

### Post by Skaperen on 2019-11-28
does Anbox work with any app you install?  can it do an upgrade to a new version of Android itself by just doing the same steps as would be done on a phone?

---

