---
title: "blacklist instructions for wireless card replacement"
date: 2009-01-15
forum: Networking &amp; Wireless
---

### Post by mfox on 2009-01-15
I just installed a replacement wireless card in my MSI Wind; a Gigabyte GN-WI01GT Atheros. A poster told me to make sure I blacklist ath_pci with this card, but he/she didn't explain how or why, and didn't respond when I queried this advice. I'm wondering if anyone else can explain this to me: what is blacklisting and how do you do it?

---

### Post by alan34 on 2009-01-15
Blacklisting is done to prevent hardware drivers being loaded to the kernel when the computer boots. 

For instance if you are using ndiswrapper to use windows wireless drivers for your card you would blacklist any linux drivers otherwise you would have 2 drivers trying to claim the same hardware with maybe system hangs and crashes.

To blacklist a driver, in a terminal

gksudo gedit /etc/modprobe.d/blacklist      (if not gnome - sudo nano /etc/modprobe.d/blacklist)

When you see the file it is obvious what you need to do which in your case at the end
of the file add this line

**blacklist ath_pci**

save exit and reboot

---

### Post by mfox on 2009-01-16
Thanks for your reply, alan.  I don't know if you can help with this question, but I'm wondering why I would be asked to blacklist this driver since I didn't install any new drivers to work with this card.  The name ath_pci presumably refers to Atheros, but the pci suggests it is being connected by a pci card, which it isn't.  It's an internal wireless card. :confused:

---

### Post by mfox on 2009-01-17
Big mistake; blacklist that driver and my wireless is gone.

---

### Post by alan34 on 2009-01-18
Sorry to hear that but you can delete the line from the /etc/modprobe.d/blacklist file the same way you put it in and reboot and all should be back as before.

I did not see your original thread and as you say why blacklist when you have not installed an additional driver. I can only presume you had some mis-information. By the way that is easy done even with the best intentions to help.

---

### Post by mfox on 2009-01-18
Thanks, Alan.  I did remove the blacklisting and all is as it should be.  I certainly don't blame the poster of this advice; it might be relevant in a different context.  And I did try to contact the person (it was on the MSI Wind forums), but I never heard back from him and no one else on that forum had any information to add.

---

