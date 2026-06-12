---
title: "No sound in amarok 2"
date: 2009-02-26
forum: Multimedia Software
---

### Post by Tanielo on 2009-02-26
Hi everyone,
I've just installed Amarok 2 on KDE 4, but I get no sound when I try to play mp3 files.

I installed it from repository, and the package amarok-xine that old Amarok used was automatically removed. If I try to install it again apt-get will delete amarok 2 and re-install the old version of amarok.

Also, I can't set the sound engine like i did in the old Amarok because it seems in Amarok 2 you can't change any audio settings (there's no "engine" page in the "settings" windows).

Any suggestion?

Thanks.

---

### Post by markbuntu on 2009-02-26
Amarok2 uses the new Phonon API/sound manager. You can control it from System Settings.

---

