---
title: "no sound in ubuntu 9.10 x64 in gateway 6860fx"
date: 2009-11-13
forum: Multimedia Software
---

### Post by drcarlos23 on 2009-11-13
Please help! everything works fine but i have no sound! It has always worked for me in previous version of ubuntu, but now i have no sound. Can you guys help me in fixing this?

---

### Post by Ulysses361 on 2009-11-13
Please send us output from step 3 and step 4 from this procedure:

[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by loungedaddy on 2009-11-19
I have the same issue. No sound on Gateway laptop, only w/ Ubuntu 9.10

Posted here: [https://answers.launchpad.net/ubuntu/+question/90907]("https://answers.launchpad.net/ubuntu/+question/90907")

Everything else is fine though, and I am loving the latest distro  :)

---

### Post by DeusExM1 on 2009-11-21
lounge daddy had his issue resolved in the thread he posted. My friend has that laptop also, so i suppose I may try to get him to get Ubuntu now.

---

### Post by chuckaluck on 2009-11-21
I had the same problem. Thix fix worked for me.
code:
1.$ alsamixer -D hw:0

This will bring up a bunch of bars representing all of the mixer tracks available on the hardware device.* After turning all of these up to 100% and exiting alsamixer (press ESC), everything was working perfectly again.

Hope this helps

---

