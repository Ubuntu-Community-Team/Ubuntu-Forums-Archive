---
title: "(solved) Grub: change setting in /etc/default/grub but has no effect"
date: 2023-01-27
forum: MINT
---

### Post by Kris_M on 2023-01-27
Mint 21.1 Cinnamon
trying to change boot order of grub menu.
/etc/default/grub: change GRUB_DEFAULT=0 to 3 or saved but has no effect.
followed by:
```
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo update-grub
```

Have 2 mint and 1 win ptns

-- ThinkPad P15s-Gen1-20T4-002KUS, i7-10510U, UEFI/GPT, 16GB, Sammy 970 EVO Plus 500GB M.2.
- others -
-laserjets: HP M254dw color, HP P1606dn.  Epson Perfection 2480 flatbed scanner -

---

### Post by Kris_M on 2023-01-28
Never mind - I was changing it in the wrong Mint.

---

### Post by deadflowr on 2023-01-28
*Thread moved to **MINT***

---

