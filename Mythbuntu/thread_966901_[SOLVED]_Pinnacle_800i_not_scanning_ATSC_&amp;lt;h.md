---
title: "[SOLVED] Pinnacle 800i not scanning ATSC &amp;lt;help!&amp;gt;"
date: 2008-11-01
forum: Mythbuntu
---

### Post by lionsnob on 2008-11-01
Hi all,

Just upgraded from 8.04 to 8.10 via Update Manager.  With the new kernel, I was anxious to try my two new 800i's out.  I have two pchdtv 5500s that I am replacing.  I heard that the tuner on the 800i was superior.

Anyhow, I 
1) put the 800i in a PCI slot
2) downloaded the firmware from [here]("http://www.steventoth.net/linux/xc5000/")
3) extracted the firmware and copied it to /lib/firmware
4) rebooted 
5) added the card in MythTV as a DVB card
6) scanned for ATSC channels and got nothing.

Any ideas?  I can't figured out what step I missed.  Is there "stuff" leftover from the 8.04.1 install that may be interfering?

Thanks!

---

### Post by lionsnob on 2008-11-01
> **lionsnob said:**
> Hi all,

Just upgraded from 8.04 to 8.10 via Update Manager.  With the new kernel, I was anxious to try my two new 800i's out.  I have two pchdtv 5500s that I am replacing.  I heard that the tuner on the 800i was superior.

Anyhow, I 
1) put the 800i in a PCI slot
2) downloaded the firmware from [here]("http://www.steventoth.net/linux/xc5000/")
3) extracted the firmware and copied it to /lib/firmware
4) rebooted 
5) added the card in MythTV as a DVB card
6) scanned for ATSC channels and got nothing.

Any ideas?  I can't figured out what step I missed.  Is there "stuff" leftover from the 8.04.1 install that may be interfering?

Thanks!

I've attached the output of dmesg in case that is helpful.

---

### Post by lionsnob on 2008-11-02
Solved - apparently the card does not like the signal timeout of 3000ms.  Changed it to 3250 and things are peachy now.

---

