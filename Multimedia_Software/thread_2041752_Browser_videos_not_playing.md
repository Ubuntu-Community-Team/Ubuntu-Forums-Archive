---
title: "Browser videos not playing"
date: 2012-08-13
forum: Multimedia Software
---

### Post by Dumpy Dumpster on 2012-08-13
I had to re-install Ubuntu 10.04 and now Firefox 14.0.1 will not play any on line videos.  Lots of 'googling' seemed to throw up problems with the Flash Player of which I now have the latest version.
Any solutions? - some suggest downgrading the Flash Player to an older version, but I do not know how to do that.

Incidentally, my Windows 7 works fine (sorry about that!) and is running the same Firefox and Flash Player combination as I have in 10.04.  So some adjustment is needed to the OS?

---

### Post by ajgreeny on 2012-08-13
What video card do you have in the machine?

I have an ATI 9200SE and that will not work at all with the latest version of flash, 11.2.202.

In order to get anything at all with flash I have downgraded to flash 11.1.102-63.  You can get that version and instructions for it at [Flash 11.1.102.63]("http://ubuntuforums.org/showthread.php?t=1953796")

---

### Post by Dumpy Dumpster on 2012-08-13
Good evening ajgreeny and thanks for your reply.
My card is ATI Radeon 7000 series so the problem may lie here.
Have copied and extracted the file and got the 'libflashplayer.so' file.   But here I falter:  'copy the file libflashplayer.so and paste into ~/.mozilla/plugins/. To see that directory under your home, you need to show hidden files. You can do that in Nautilus by hitting CTRL+H.'
I cannot see the file '~/.mozilla/plugins/' anywhere!
It also seem that Flash-Aid has been removed by the author.
Bit more help needed if you could be so kind!

---

### Post by ajgreeny on 2012-08-13
> **Dumpy Dumpster said:**
> Good evening ajgreeny and thanks for your reply.
My card is ATI Radeon 7000 series so the problem may lie here.
Have copied and extracted the file and got the 'libflashplayer.so' file.   But here I falter:  'copy the file libflashplayer.so and paste into ~/.mozilla/plugins/. To see that directory under your home, you need to show hidden files. You can do that in Nautilus by hitting CTRL+H.'
I cannot see the file '~/.mozilla/plugins/' anywhere!
It also seem that Flash-Aid has been removed by the author.
Bit more help needed if you could be so kind!
You may well be correct about the ATI card similarity being the problem, as all the instances of the new flash not working at all have been with ATI cards of differing models.

Assuming you can find the folder **.mozilla** in your home, you can just make the new **plugins** folder manually then copy the libflashplayer.so file into that folder.  You can easily check the version of flash you then have by typing **about:plugins** in the firefox addressbar.

---

### Post by Dumpy Dumpster on 2012-08-13
You are a hero, ajgreeny!
I created the folder as you suggested, copied in the 'libflashplayer.so' file.  It was there in 'about:plugins', so I then disabled the version 11.2.202, and all is now working.
Thanks again!

---

### Post by ajgreeny on 2012-08-13
Wonderful !!

---

