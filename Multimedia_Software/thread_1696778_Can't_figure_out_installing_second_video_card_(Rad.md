---
title: "Can't figure out installing second video card (Radeon 7500 PCI)"
date: 2011-02-27
forum: Multimedia Software
---

### Post by kylegio on 2011-02-27
I have a Radeon 7500 PCI card that i am wanting to use as a second display. 

i simply cant figure out how to activate/configure the card in linux.

going to the "monitors" option in the settings just takes me to an nvidia options pane, which shows my primary video card (Nvidia 7800) but says nothing about the radeon card 

lspci command shows it:
```
lspci -nn | grep VGA
01:07.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV200 QW [Radeon 7500] [1002:5157]
03:00.0 VGA compatible controller [0300]: nVidia Corporation G70 [GeForce 7800 GTX] [10de:0091] (rev a1)

```


any help appreciated

---

### Post by linescanner on 2011-03-02
I am having the same issue.

Did you solve it ?

---

### Post by kylegio on 2011-03-02
did not solve it, doesnt seem like anyone knows

---

