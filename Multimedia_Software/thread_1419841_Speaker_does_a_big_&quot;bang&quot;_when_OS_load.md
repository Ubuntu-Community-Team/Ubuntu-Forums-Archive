---
title: "Speaker does a big &quot;bang&quot; when OS load"
date: 2010-03-02
forum: Multimedia Software
---

### Post by daok on 2010-03-02
I have one of the Logitech 5.1 speakers and everytime I boot on Kubuntu the speakers and the sub does a big "boom". I do not have that problem on WinXp neither with Vista. Any one have an idea?

*Yes I can hear sound from the speakers after but every time I jump 3 feets over my chair because of the boom...

---

### Post by Maheriano on 2010-03-02
This is a result of your sound card turning on with bootup. Most setups will keep the sound card disabled until the operating system loads, and then turn it on to avoid the thump from the sudden jolt on the audio line. Check some settings in your BIOS or even try loading new BIOS drivers, that might help. Otherwise the reason it's not happening in Windows is because the Windows drivers have been designed to boot the computer in such a fashion that the sound card waits before turning on. With Linux this function doesn't seem to be present.

Google your motherboard/sound card model number and see if any other Linux users are having the same issue. Maybe it's a manufacturer issue.

---

