---
title: "[SOLVED] DViCO Dual Digital 4 - IR Issues"
date: 2008-03-06
forum: Mythbuntu
---

### Post by nasha on 2008-03-06
Hey guys,
I have a very strange problem... I gave up attempting to get my IR working, because no matter what it just wasnt showing up in dmesg.
The other day, i had the card out of my backend and in another machine to test the IR under Windows... Worked fine.
I put the card back into my backend, and all of a sudden IR shows up in dmesg! All was great, i had a remote... for a few days.
My problem now is, i have no IR again!

If anybody has any suggestions, or anything i would really appreciate it :)
Thanks in advance,
Nasha

---

### Post by kreegor on 2008-03-16
My brother in law is having a similar issue. He has managed to apply updates etc to get the card and the remote working but as soon as he reboots his machine the settings go away and he has to reconfigure it all again.

Does anyone know how to fix this?

---

### Post by nasha on 2008-03-16
My problem has since been solved... It appears the issue had something to do with a dodgy USB port.
If your brother in law is using ubuntu, and dual digital 4, then installing should be as simple as following the instruction below.
[HTML]https://help.ubuntu.com/community/DViCO_Dual_Digital_4[/HTML]

---

### Post by kreegor on 2008-03-16
Yeah they are the instructions he uses and they work fine. It's just that his remote stops working when he restarts.

---

### Post by nasha on 2008-03-17
Well you need to narrow down why its not working... Is lircd running on boot? Is the settings being overridden?

---

### Post by kreegor on 2008-03-17
Sorry. I should have been more specific. The settings are being overridden. Every time he reboots he basically has to edit the lirc file again. The card works fine on reboot e.g. can view tv on both tuners it is just the remote.

---

### Post by Lem on 2008-03-17
Can you not set the permissions of the lirc file to read only?

---

### Post by kreegor on 2008-03-17
Tried that and it still didn't work. It seems that each time he reboots irw stops working and he has to go through that list of instructions to get it working again.

Not sure if lircd is running on boot. Will have to check later but in case it isn't how do we make it?

---

