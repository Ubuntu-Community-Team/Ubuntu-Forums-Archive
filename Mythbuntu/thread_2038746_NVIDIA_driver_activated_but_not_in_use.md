---
title: "NVIDIA driver activated but not in use"
date: 2012-08-07
forum: Mythbuntu
---

### Post by dheianevans on 2012-08-07
Running Natty...

Had updates to download tonight and one of them was the nvidia proprietary driver.

After installing a I rebooted. When I check the additional drivers app it said that my NVIDIA drivers were activated but not in use. Wassup?

---

### Post by phthano on 2012-08-14
I had the same problem on my Asus K50ID some time ago. I removed all nvidia drivers with Synaptic package management. 

Then, I installed again from the terminal. 

Then run:
sudo apt-get install nvidia-current
and then:
sudo nvidia-xconfig

When you install proprietary drivers, you generally need to run the config utility afterwards.

---

### Post by slender on 2012-08-14
Sweet! I've just received my free minecraft giftcode!

>> Minecraftcodes.info <<

---

### Post by lukeiamyourfather on 2012-08-14
What chipset are you using? It might be the driver no longer supports the chipset if the card is pretty old. There's a separate "legacy" driver for older chipsets.

---

