---
title: "windows backup convert on linux"
date: 2020-06-25
forum: Multimedia Software
---

### Post by T6&amp;sfpER35% on 2020-06-25
OK so i have found this old DVD that I've forgotten about with a backup of photos that I've created YEARS ago on a windows PC with program Nero.
Now if i pop this disk into the DVD drive i cant do anything with it ,it seems it needs the Nero program again to restore the files.
Is there anything on Linux i can use to restore the backup or must i do it on  a windows PC ?


[FONT=garamond][COLOR=#800000]*Thanks!*[/COLOR][/FONT]

---

### Post by CelticWarrior on 2020-06-25
A DVD made with Nero says nothing about the actual content.

Nero can do a data DVD with the photo files within and that would be readable in any OS.

What are the file formats there? What do you see in Files?

---

### Post by T6&amp;sfpER35% on 2020-06-25
please see some screenshots

[ATTACH=CONFIG]286321[/ATTACH][ATTACH=CONFIG]286322[/ATTACH]


excuse the quality,don't know why its looking so crap now

file format is xxxxxx.jpg.nco

---

### Post by deadflowr on 2020-06-25
Try renaming the .nco extension to something like .zip.
Then try extracting it.
try for one, then if successful try for all.
Ubuntu file roller should be installed with zip support, if not you can always try and install and use the unzip package.

---

### Post by CelticWarrior on 2020-06-25
It's a Nero BackItUp proprietary format.

Try the suggestion above first because it's the simplest. It may not work though.
Next try installing the full (GUI) 7-Zip utility and then try opening the nba/nco files with it. This suggestion comes from this [old question at Nero forum]("http://forum.nero.com/nero_eng/topics/how_do_i_recover_older_nero_backitup_files_from_cds_and_where_can_i_get_the_old_versions_of_backitup").

---

