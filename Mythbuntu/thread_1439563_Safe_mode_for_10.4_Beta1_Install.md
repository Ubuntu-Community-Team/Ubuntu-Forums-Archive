---
title: "Safe mode for 10.4 Beta1 Install"
date: 2010-03-26
forum: Mythbuntu
---

### Post by davefor on 2010-03-26
I am trying to install 10.4 Beta 1. I noticed that there is no option F4
to select safe mode. With 9.10 I needed to select this because I don't have a monitor
connect I use a nvidia card svideo out to TV. I tried adding vga=vesa to the boot string
but that didn't work

---

### Post by superm1 on 2010-03-26
> **davefor said:**
> I am trying to install 10.4 Beta 1. I noticed that there is no option F4
to select safe mode. With 9.10 I needed to select this because I don't have a monitor
connect I use a nvidia card svideo out to TV. I tried adding vga=vesa to the boot string
but that didn't work

Now the driver in use is the 'nouveau' driver by default.  It has kernel mode setting support.  if this doesn't work,  try hitting F6 and choosing "nomodeset"

---

### Post by davefor on 2010-03-27
I tried the F6 option nomodeset. I now get to see the ubuntu 10.4 boot screen
but then it exits with errors init: ureadahead-other main process (1557) terminated with status 4

---

### Post by mgrusin on 2010-07-17
Hello, I think I'm having the same problem.  Did you find a fix?

Thanks very much, -Mike.

---

### Post by superm1 on 2010-07-17
If that alone did not work, try also adding xforcevesa as an additional parameter to the nomodeset that was previously added.

---

### Post by mgrusin on 2010-07-19
"nomodeset" eventually worked for me. (My install .iso wasn't working correctly as I had put it on an USB stick rather than a real CD).

Thanks!

---

