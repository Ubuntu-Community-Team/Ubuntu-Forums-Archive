---
title: "help with patching bluetooth-alsa"
date: 2005-12-23
forum: Multimedia &amp; Video
---

### Post by dannemil on 2005-12-23
I am able to get my Jabra BT200 headset to connect to my PC. I can even ping the headset and get replies. What I can't do is hear anything on the headset once it is paired with the PC. I read that I need to patch the kernel with the bluetooth-asla patch and recompile the kernel. I am not experienced enough to go through these steps, so if anyone is willing to walk me through them in detail, I would much appreciate it.

Jim

---

### Post by gcain on 2005-12-26
Are you certain you have winamp (or whatever is playing the sound) configured right?
I got it wrong the first few times...

Try simply cating a binary file to the /dev/dsp1 device, it will only play garbage, but at least it's sound and a hint in the right direction.
Don't forget to have btsco -v YOUR_BT_MAC_ADDRESS running in a console somewhere.

---

