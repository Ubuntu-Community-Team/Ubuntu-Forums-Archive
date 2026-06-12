---
title: "nvidia tnt2 drivers?"
date: 2009-01-05
forum: Multimedia Software
---

### Post by Baffo on 2009-01-05
hello,

can you please tell me how i do install drivers for nvidia tnt2 model 64 pro?
im new to linux and want to learn.

thanks everybody.

---

### Post by wolfen69 on 2009-01-05
just go to system>administration>hardware drivers and install.

---

### Post by Baffo on 2009-01-06
**"system>administration>hardware"** is **empty** ?!?

maybe that's because my video card (nvidia tnt2 model 64 pro )isnt recognized ?

what can i do?

---

### Post by wolfen69 on 2009-01-06
go to system>administration>software sources and make sure the universe repo is enabled. then open terminal and: ```
sudo apt-get install envyng-gtk
``` use this app to install your nvidia driver.

---

### Post by Baffo on 2009-01-06
i used envyng, and it installed nvidia drivers glx-71, but on reboot, ubuntu fails to load drivers, telling an error occurred. i had to unistall the drivers..

what to do ?

---

### Post by Baffo on 2009-01-09
any help ?
should i go back to xp ?

---

### Post by overdrank on 2009-01-09
> **Baffo said:**
> any help ?
should i go back to xp ?

Hi and if you are using Intrepid 8.10 I have seen where the old tnt2 cards have issues. Have you tried using Hardy 8.04?

Edit you may also try the xfix option when booting into recovery mode to fix the graphics issue.
Recovery mode is usually the second choice from the grub while booting.

---

### Post by Baffo on 2009-01-09
i have 8.10. 
are you telling me tnt2 cards dont work with 8.10 ?

---

### Post by overdrank on 2009-01-09
> **Baffo said:**
> i have 8.10. 
are you telling me tnt2 cards dont work with 8.10 ?

No, I am saying that I have seen users on the forums that have issue with the older nvidia cards on intrepid.

---

### Post by Baffo on 2009-01-09
have you seen them fix those problems?

---

### Post by overdrank on 2009-01-09
> **Baffo said:**
> have you seen them fix those problems?

Hi and yes some have been fix by the xfix option I posted earlier.

---

### Post by Baffo on 2009-01-09
i'll google it
thanks

---

### Post by nirvblakr on 2009-01-21
Hi!  I have downloaded Elisa Media Center and tried running the program.  A window pops out that 3d acceleration is not enabled thus I cannot use the Media Center.  

My video card is an Nvidia 9600 and I want to activate the 3d acceleration of my video so I can use Elisa.  How can I go about it?  TIA

---

