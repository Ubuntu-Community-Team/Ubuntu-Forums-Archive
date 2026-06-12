---
title: "How to get my ATi Radeon HD3850 to work?"
date: 2009-04-26
forum: Multimedia Software
---

### Post by nukenah on 2009-04-26
Installed Ubuntu like half an hour back. I did some [reading]("https://help.ubuntu.com/community/BinaryDriverHowto") and read that my card (ATi Radeon HD3850) should be supported by the open RadeonDriver. I suppose my card is not being supported since I can't enable Visual Effects.

I tried "Sytem > Administration > Hardware Drivers" and at first it just showed "No proprietary drivers..." and there was nothing else in the window, just some blank panels where my card should've been. On next run, it did detect but when it started downloading, it didn't get past 0% and then I had an error about some crashed backend. To try and remember the error and post here I ran Hardware Drivers again and this time it's just stuck at "Searching for available drivers..." and doesn't get past there.

What do I do about this?

PS. My network is completely fine. I have been surfing, downloading and installed p7zip and unrar using the terminal.

---

### Post by khelben1979 on 2009-04-26
Go to the ATi website and download the latest drivers from there. Make sure to follow all the instructions step by step and you should have no problems.

The open source ATi drivers isn't very impressive when it comes to speed... :-k

---

### Post by nukenah on 2009-04-26
Thanks! I didn't anticipate for them to have Linux drivers on their web-site.

82MB. Even the Windows driver was like 15MB. :|

---

### Post by Melcar on 2009-04-26
The open source drivers only have 2D and Xv support for that particular card.  If you want 3D you're going to have to use fglrx.  Jaunty comes with the 9.4 Catalyst driver, which is the latest at the moment; all you need to do is activate the drivers using the Hardware Drivers interface (Administration > Hardware Drivers).

---

### Post by markbuntu on 2009-04-26
Before you try to do anything run update manager and make sure you have all the updates. After updating hardware manager should show an available driver if you are using 8.10 or 9.04.

---

### Post by nukenah on 2009-04-27
> **Melcar said:**
> Jaunty comes with the 9.4 Catalyst driver, which is the latest at the moment; all you need to do is activate the drivers using the Hardware Drivers interface (Administration > Hardware Drivers).

I ran Hardware Drivers again and it finally worked, thanks a lot!

---

### Post by espmartin on 2009-04-27
My Hardware Drivers shows "No proprietary drivers" ;-/

Here's what lspci shows:
> martin@ubuntu:~$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV516 [Radeon X1300/X1550 Series] [1002:7183]
martin@ubuntu:~$ 

Any thoughts?

---

### Post by nukenah on 2009-04-27
> **espmartin said:**
> My Hardware Drivers shows "No proprietary drivers" ;-/

Here's what lspci shows:

Any thoughts?
lspci did detect the card for me too, but after several restarts, Hardware Drivers automatically installed the driver. Weird. :\

---

