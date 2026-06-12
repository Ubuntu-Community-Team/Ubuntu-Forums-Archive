---
title: "Movie Player won't play audio CD's."
date: 2008-07-20
forum: Multimedia Software
---

### Post by johnnyhop on 2008-07-20
A new install of Xubuntu on a 1999 vintage PIII. Its a 600mHz processor with 512mb RAM. Movie Player opens upon loading major label audio CD's but the tracks don't load and an error pops up, "An error occurred--Location not found." Mp3's, ogg's and wav's do play and data CD's will mount. Installed VLC which will play audio CD's. Would prefer to configure Movie Player to play CD's or as an alternative prevent Movie Player from opening when an audio CD is inserted

---

### Post by fred.warren on 2008-08-02
Hi I just solved this problem myself and will be filing a bug report.

Thunar has the association for audio cds cdda:/ instead of the proper cdda:// and for dvds as dvd:/ instead of dvd://

To correct this do the following
[LIST=1]
[*]Open Thunar (Can be found on the Menu under Accessories)
[*]From the menu at the top of Thunar select **_E_dit**
[*]From the **_E_dit** menu select **Pr_e_ferences**
[*]From the **File Manager Preferences** dialog, click on the tab labeled **Advanced**
[*]From the **Advanced** tab click on the blue linked word **Configure**
[*]From the **Removable Drives and Media** dialog, click on the tab labeled **Multimedia**
[*]From the **Multimedia** tab for the **Audio CDs _C_ommand** locate the entry **totem cdda:/**
[*]Change that to **totem cdda://**
[*]From the **Multimedia** tab for the **Video CDs/DVDs C_o_mmand** locate the entry **totem dvd:/**
[*]Change that to **totem dvd://**
[*]Close all dialogs and exit Thunar
[*]Insert your CD or DVD and enjoy
[/LIST]

---

### Post by johnnyhop on 2008-08-23
Thank you.  I'm a step closer to the total fix and thanks to you leading me to the configuration file, am mow able to prevent Movie Player from opening when inserting a CD which is plan B.  Now the error message upon inserting the CD is "Could not open location. You may not have permission to open the file."  I couldn't find the file system location of CDDA* to attempt to manage attributes and am clueless as to why I as the system install user wouldn't have permission. The error message suggeestion is likely not the cause.

---

