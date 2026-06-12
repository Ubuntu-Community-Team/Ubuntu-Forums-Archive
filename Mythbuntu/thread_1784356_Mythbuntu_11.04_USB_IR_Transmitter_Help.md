---
title: "Mythbuntu 11.04 USB IR Transmitter Help"
date: 2011-06-16
forum: Mythbuntu
---

### Post by chrismurf2900 on 2011-06-16
I recently upgraded to Mythbuntu 11.04, had some issues, so installed a fresh copy of Mythbuntu 11.04 to rectify those problems.

I'm trying to setup a USB IR Transmitter with Mythbuntu 11.04, however it is proving to be really difficult.  I keep getting a message when I call the irsend command, "Hardware does not support sending."
The IR Transmitter/Receiver is and Microsoft MCE.  I'm able to use it as a receiver, but haven't been able to trasmit yet.

I know that the drivers are now included in the Linux kernel, which I think is what the problem is I'm having.  I'm just not sure what exact settings I should be utilizing, or even if I'm going through the right process.

If anyone can assist me with this, I'd greatly appreciate it.  I currently can change channels.  Let me know if you need to see any kind of files (like the hardware.conf, etc.)

Thanks in advance for everyone's help!

---

### Post by sponson on 2011-07-03
According to this thread:

[http://ubuntuforums.org/showthread.php?t=789608](http://ubuntuforums.org/showthread.php?t=789608)

If you reverse the sequence of the include statements in /etc/lircd.conf it will clear up the problem.  This is from an older version of Ubuntu but the same problem may persist.

---

