---
title: "Nvidia + wine + Warcraft"
date: 2007-04-24
forum: Multimedia &amp; Video
---

### Post by celettu on 2007-04-24
Wasn't sure if I'd post this here or in Gaming and leisure, but I'm pretty sure the culprit is the nvidia driver.

The situation's like this: I had Warcraft 3 working perfectly with wine 0.9.34 (Automatix version) with Edgy, and the nvidia-glx packages which contained the 8776 driver. After the upgrade to Feisty (and nvidia 9631) my warcraft looks like the attached screenshot. 

Now, that isn't ALL black. There's some green in there, and it still works! At least, the sound is still there I can still move the pointer to the place where I guess the "Quit" button is, and then Warcraft exits without issue.

I've tried different versions of wine from different sources, all with the exact same result, so I don't think it's wine. Other apps like utorrent and Starcraft still work fine.

The only thing I haven't tried yet is installing the 8776 driver, but I'm hesitant to do that because I dread the "kernel module/driver mismatch" error.

I have no other issues with the nvidia driver otherwise...but I haven't finished the campaign yet, and I LOVE that game!

Edit: screenshot didn't get added, it's [here]("http://users.fulladsl.be/spb22501/warcraft.png").

---

### Post by celettu on 2007-04-28
Okay, I solved it. As I thought, the offender was the NVidia driver (9631), and judging from these forums I'm not the only one who has trouble with it.

Found the solution [here]("http://kmandla.wordpress.com/2007/03/25/success-compiling-nvidia-8776-driver-on-feisty-2620-12-386/")

---

