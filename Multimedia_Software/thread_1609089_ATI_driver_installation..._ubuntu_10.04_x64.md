---
title: "ATI driver installation...? ubuntu 10.04 x64"
date: 2010-10-29
forum: Multimedia Software
---

### Post by Sagacious on 2010-10-29
ok so i have a clevo x8100 laptop with two 5780's in crossfire. Im not exactly sure where to check in linux but i remember im using the fglrx drivers...which from what i understand are the crappy "safe" drivers. I've downloaded the latest linux x64 drivers for the card... 

do i need to uninstall the old drivers first before i attempt to install the new one? also, if i do need to uninstall the old one, do i need to disable all my compiz special effects too? I could just see that creating a problem. im afraid im ruining my ubuntu install now that i've got everything configured the way i want minus the video drivers. if anyone has any good experience with this please let me know... thanks.

---

### Post by Sagacious on 2010-11-01
*bump* anyone?

---

### Post by 3Miro on 2010-11-01
fglrx are proprietary ATI drivers and they are the only ones officially supported by Ubuntu.

If you are going to play with the driver, you should disable the fglrx first. Go to System -> Admin -> Hardware and deactivate the driver (then reboot). If 3D acceleration is disabled, then compiz will simply give way to metacity, so there is nothing to do there.

Installing drivers from the ATI web-page or wherever you got them is a potentially tricky business. Make sure you read carefully and remember what you do so you can undo changes if you have to.

---

### Post by Sagacious on 2010-11-01
ok, gotcha.. I've got two questions though.

aren't fglrx drivers vastly inferior performance wise in comparison to the latest on ati's website? in other words isn't the driver upgrade something that people normally do? I don't want to go playing with it if it isn't going to make a big difference

secondly, does crossfire capability even work with fglrx drivers? I see the option in catalyst and it lets me select it but every time i restart to apply changes it goes back to "disabled"

---

