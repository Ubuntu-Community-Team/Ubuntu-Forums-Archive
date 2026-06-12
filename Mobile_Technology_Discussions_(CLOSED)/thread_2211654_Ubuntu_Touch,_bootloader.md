---
title: "Ubuntu Touch, bootloader"
date: 2014-03-17
forum: Mobile Technology Discussions (CLOSED)
---

### Post by sven.cintern on 2014-03-17
Hi,

I've recently installed ubuntu touch on my phone.. (nexus 4) It was going fine with ubuntu touch working (mostly) correctly etc. 

However, I've turned it on now, and its boot looping. No, problem, right? Except there is. It doesnt have the stock bootloader -Its the ubuntu one, and it doesnt seem to be working correctly. 
I get errors when I try to flash a new image in, and I'm running out of ideas. 
My backup also got corrupted. 

I've tried the factory reset/wipe wipe cache etc from bootloader. 

What can I do now?

Kind regards,

Steve

---

### Post by sven.cintern on 2014-03-17
Edit!!

Im a total idiot....

[I]adb reboot bootloader
[/I]then
[I]ubuntu-device-flash --channel=devel --bootstrap

[/I]From the terminal fixed everything!

LOL

---

### Post by sammiev on 2014-03-17
Thanks for the update, I'm sure it will help others. Please mark this thread as solved. :)

---

