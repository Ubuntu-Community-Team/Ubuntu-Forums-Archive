---
title: "Problem: Adding Location launcher to Main Menu"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Splat_NJ on 2011-01-24
I'm trying to add a location (OOffice spreadsheet) to the Accessories submenu on the Main Menu. I've repetitively tried it but it never shows up, even after a reboot. I've done it before but that was weeks ago. Is this something now changed or not working for NN11.04? Thanks.

---

### Post by mc4man on 2011-01-24
You should probably click on the little 'report abuse' under your name (can be used for 'good' things ) and ask that your thread be moved to the natty dev. thread
[http://ubuntuforums.org/forumdisplay.php?f=394](http://ubuntuforums.org/forumdisplay.php?f=394)
Likely people are using the gnome-panel login  and could help..

---

### Post by Splat_NJ on 2011-01-24
Moved it. Thank you.

---

### Post by mc4man on 2011-01-24
I don't use the panel login too much but it appears you can't use a location in edit menus atm. (nothing is created

You can use location for a desktop launcher or in edit menus use 'Applicaton' instead of 'Location', that should work.
So - 
command  /location

Ex. (if I'm getting what you want ) in screen

---

### Post by Splat_NJ on 2011-01-25
I had tried that but got an error about couldn't launch the file. "Failed to execute child process "/home/splat/Documents/Fracts-Decimals.xls" (Permission denied)"
Yet, I do have ownership of the file.

---

### Post by Splat_NJ on 2011-01-25
OK, using the Application selection and giving the full path with the executable works: 
ooffice -calc /home/splat/Documents/Fraction-decimal.xls

I thought I had tried that but anyway, thank you. So, trying to add a "Location" using the "Main Menu" editor does not work att.

---

