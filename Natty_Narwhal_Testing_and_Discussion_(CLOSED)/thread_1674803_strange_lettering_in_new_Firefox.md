---
title: "strange lettering in new Firefox"
date: 2011-01-24
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ecr959 on 2011-01-24
Hi everybody.

    This just started happening between yesterday and today.  I made sure that the character set was "western"  and "iso 8859"  but this still happens even after closing FF and then restarting it.  Any ideas or hints how to tackle this ?

I SOLVED IT.  Preferences-Content-languages  had something like chrome//global/locale  or something similar.   I added English to that list and moved it to the top of the list.  quit FF and then re-opened,  and now the problem is gone.   

Thank you, tekstr1der.

---

### Post by tekstr1der on 2011-01-24
See Here (specifically posts #4 & #5):

[http://ubuntuforums.org/showthread.php?t=1539731](http://ubuntuforums.org/showthread.php?t=1539731)

---

### Post by ecr959 on 2011-01-24
Thanks,  tekstr1der.

I found the problem in the Preferences-Content-Language section.

---

