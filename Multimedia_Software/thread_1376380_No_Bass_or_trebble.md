---
title: "No Bass or trebble"
date: 2010-01-09
forum: Multimedia Software
---

### Post by Bigneil on 2010-01-09
I am running Karmic 64bit on a frankenstein desktop. I am using an old Creative Soundblaster card with the live drive front panel. Ever since i started using Karmic i have lost many functions, there are no bass and treble controls, and no other controles other than volume and balance.

Am i missing some vital drivers?

---

### Post by Bigneil on 2010-01-09
quick screenshot

---

### Post by Bigneil on 2010-01-11
?

---

### Post by chkneater on 2010-03-02
How long have you been using Karmic?  Are any drivers listed in use?  What does it say when you do lspci?  Try using alsamixer in a terminal and muting/unmuting certain channels.  Different cards having different adjustments.  Also, make sure PC speaker is muted in alsamixer and you have it turned off in your BIOS also.

---

### Post by kostkon on 2010-03-02
If you want to access your hardware volumes, then you could install the utility
```
gnome-alsamixer
```
Hope that helps.

---

