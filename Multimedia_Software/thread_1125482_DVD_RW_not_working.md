---
title: "DVD RW not working"
date: 2009-04-14
forum: Multimedia Software
---

### Post by S.nazari on 2009-04-14
I have a dvd rw that is attached to my computer. It works in Win XP with BurnforFree program. But doesn't in ubuntu. I'm using kubuntu but I don't think that is the problem. I have used gnomebaker and k3b but neither show any effect. 
Can anyone help. 
Thanks

---

### Post by SunnyRabbiera on 2009-04-14
Actually it might very well be KDE 4, it has had some issues with audio CD playback and maybe this is another flaw.

---

### Post by S.nazari on 2009-04-15
Now its not detecting anything I put into the driver. Its like its not even connected to this machine. Also k3b taks a long time to load up.

---

### Post by mrowth on 2009-04-15
I have, or used to have, problems with optical drives myself when I don't add "noapic" to my kernel boot parameters (in /boot/grub/menu.lst). Did you try that? Just a wild guess, but who knows. 

Using "noapic" once did somehow stop the nvidia driver from working at all *without* "noapic", so now I'm dependent on it. 

Haven't tried it without "noapic" on Intrepid yet though.

---

### Post by S.nazari on 2009-04-16
I will try that, I have not put in there a SATA DVD RW which can not be booted from as the bios doesn't allow it. I will try my luck with noapic. Do I add this at the end of the first kernel entry ?

---

### Post by S.nazari on 2009-04-16
I have done that but there is no use. There are still read errors and there is and error in k3b on the sata drive that the drive is in use. I'm getting the message that Cdrecord has no permission to open the device.

---

### Post by mrowth on 2009-04-17
Yes, you add it to the kernel line, like so:

kernel    /boot/vmlinuz-2.6.27-11-generic root=UUID=... ro quiet vga=773 noapic 

You can also press "e" when the GRUB menu appears on boot-up and then edit the lines manually for just that one session without actually modifying menu.lst.

Sorry it didn't help. I don't really know anything else to try. You could try searching for more info on libata and possible ways to use the older IDE drivers again. Not that that seemed to make a difference when I tried. Out of my league here.

(Something else's weird about CD/DVD drives here: For example, my current drive stopped working on the first or second day until I used the Windows firmware updater. And 80-wire cables work as 40-wire cables. Oh, and SATA never worked. Can't boot off it either so I don't care for it that much.)

---

