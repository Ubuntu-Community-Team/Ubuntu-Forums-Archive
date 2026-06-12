---
title: "midi-keyboard to control amarok and/or KMix"
date: 2008-10-07
forum: Multimedia Software
---

### Post by Capoeira on 2008-10-07
is this possible?

i have an USB-midi-Keyboard.

can i use it to control volume, change title in amarok, ect.?

---

### Post by Capoeira on 2008-10-07
ok, i should have posted this in Multimedia & video too. i thougt there was no extra catagory.

---

### Post by Stochastic on 2008-10-07
Moved thread to Multimedia & Video for you.

My gut instinct on this one says that it's pretty difficult to do, unless a plugin-script exists to do such a thing.  There are USB volume knobs on the market, but I've never looked into the linux support on the matter.

---

### Post by Capoeira on 2009-06-17
(would be better placed in multimedia-production perhaps?! since midi is more a production-feature)

still hoping to find a way

perhaps it is possible to control amarok with jack-transport? since it is possible to control jack-transport with midi. (with jackctlmmc: [http://sourceforge.net/project/showfiles.php?group_id=245788](http://sourceforge.net/project/showfiles.php?group_id=245788))

---

### Post by raboofje on 2009-06-17
I mocked up a solution based on aseqdump, a little bit of perl, and amarok's dbus interface. See the thread over at [http://www.linuxmusicians.com/viewtopic.php?f=4&t=1518](http://www.linuxmusicians.com/viewtopic.php?f=4&t=1518)

---

