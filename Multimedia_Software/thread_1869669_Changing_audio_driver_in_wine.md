---
title: "Changing audio driver in wine"
date: 2011-10-26
forum: Multimedia Software
---

### Post by PsyclonJohn on 2011-10-26
Hello all!

I just installed wineASIO and was given the directions to change the drivers in winecfg, the problem is... there is no way to change anything in the audio tab. 

Here is a screenshot:
[IMG]http://i39.tinypic.com/r6who7.png[/IMG]

If anyone knows a different way to change the audio drivers in Wine, or knows why this is all blank when it should have a large box to select drivers, please tell!

Thanks,

John

---

### Post by shantiq on 2011-10-26
was given a nice workaround by sgx **[here]("http://ubuntuforums.org/showpost.php?p=11336474&postcount=7")**

> start regedit

wine /home/you/.wine/drive_c/windows/regedit.exe

find this key: HKEY_CURRENT_USER\Software\Wine\Drivers\Audio

and edit the key to be the one you want

Reboot or logout/in, and try winecfg again.
If that does not work, delete the whole key itself.
If it still fails to show the audio tab, install
another wine version.



But for me did not produce anything as key was absent

had to remove wine1.3 and reinstall wine1.2 then options returned

---

