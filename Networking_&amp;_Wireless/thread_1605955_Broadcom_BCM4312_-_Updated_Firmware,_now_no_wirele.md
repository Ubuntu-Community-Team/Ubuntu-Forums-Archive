---
title: "Broadcom BCM4312 - Updated Firmware, now no wireless in Windows"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by Imizael on 2010-10-25
I just tried 10.10, and aside from the ever-present wireless issues, I was okay with it.  Unfortunately, I require wireless access to work, and it didn't work out.  I removed the Ubuntu partition, fixed the Windows bootloader, and booted back into Windows to find that wireless no longer works.

Now, when I was in Ubuntu, I installed firmware-b43-lpphy-installer.  I suspect that installing that overwrote whatever I had before as far as firmware goes, and the driver I have in Windows doesn't work.  Now, when I say "doesn't work", I actually mean "detects and installs properly per Device Manager, but doesn't actually detect or connect to wireless networks."

I'm going to try using a liveUSB installation to reinstall the default firmware... if I can figure out what that is.  I looked for a Windows firmware installer for the BCM4312 chip, but I can't find one.  Running the manufacturer installer (Dell Inspiron 1564) worked, but didn't get any different results.

Does anyone have any suggestions?

---

### Post by Imizael on 2010-10-25
I'm cross-posting this to the Dell forums and the Laptop support forums, as well as the general forums.  If this is against the rules, feel free to remove the offending threads.

I just tried 10.10, and aside from the ever-present wireless issues, I was okay with it. Unfortunately, I require wireless access to work, and it didn't work out. I removed the Ubuntu partition, fixed the Windows bootloader, and booted back into Windows to find that wireless no longer works.

Now, when I was in Ubuntu, I installed firmware-b43-lpphy-installer. I suspect that installing that overwrote whatever I had before as far as firmware goes, and the driver I have in Windows doesn't work. Now, when I say "doesn't work", I actually mean "detects and installs properly per Device Manager, but doesn't actually detect or connect to wireless networks."

I'm going to try using a liveUSB installation to reinstall the default firmware... if I can figure out what that is. I looked for a Windows firmware installer for the BCM4312 chip, but I can't find one. Running the manufacturer installer (Dell Inspiron 1564) worked, but didn't get any different results.

Does anyone have any suggestions?

---

### Post by Imizael on 2010-10-25
I'm cross-posting this to the Dell forums and the wireless support forums, as well as the general forums.  If this is against the rules, feel free to remove the offending threads.

I just tried 10.10, and aside from the ever-present wireless issues, I was okay with it. Unfortunately, I require wireless access to work, and it didn't work out. I removed the Ubuntu partition, fixed the Windows bootloader, and booted back into Windows to find that wireless no longer works.

Now, when I was in Ubuntu, I installed firmware-b43-lpphy-installer. I suspect that installing that overwrote whatever I had before as far as firmware goes, and the driver I have in Windows doesn't work. Now, when I say "doesn't work", I actually mean "detects and installs properly per Device Manager, but doesn't actually detect or connect to wireless networks."

I'm going to try using a liveUSB installation to reinstall the default firmware... if I can figure out what that is. I looked for a Windows firmware installer for the BCM4312 chip, but I can't find one. Running the manufacturer installer (Dell Inspiron 1564) worked, but didn't get any different results.

Does anyone have any suggestions?

---

### Post by Megaptera on 2010-10-26
Hi,
This first link is specific for 10.10and  Dell, hope it helps? Don't worry that it says Dell mini

[http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html](http://www.ubuntumini.com/2010/10/broadcom-wireless-driver-fix-in.html)

---

### Post by s.fox on 2010-10-26
Please do not create 3 threads on the same topic. 

Threads merged.

---

### Post by ugm6hr on 2010-10-27
> **Imizael said:**
> I just tried 10.10, and aside from the ever-present wireless issues, I was okay with it. 

What wifi issues?
My Mini has the same card (I presume):
```
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
```
It works well if you use the ubuntumini link Megaptera gave in 10.10. The other driver (b43) appears to work well initially, but intermittently disconnects.

As far as I know, the firmware makes no changes to the hardware at all - so it should have no effect on Windows.

Perhaps point 9 in this link might be of relevance? [http://ubuntuforums.org/showthread.php?p=5024425#post5024425](http://ubuntuforums.org/showthread.php?p=5024425#post5024425)
Although a re-installed Windows should be able to fix its own ridiculous setting.

---

### Post by bobmartens on 2010-11-01
accidental reply, soory

---

