---
title: "Can i actually test unity on ati pci-e card?"
date: 2011-01-08
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ELD on 2011-01-08
So as usual with later versions of Ubuntu the catalyst amd/ati drivers don't support Ubuntu Unity yet.

Is there a way for me with this hardware to be able to actually test Unity?

---

### Post by coffeecat on 2011-01-08
What card do you have? Unity/Natty works just fine with the open-source ATI driver with my Radeon HD4350 card. Posting from Unity/Natty desktop now.

---

### Post by ELD on 2011-01-08
On an AMD5770, my packages are out of date by 5 days though updating now.

I installed catalyst drivers as it didn't work before but i'm pretty sure they don't work with the newer xorg so i will probably need to revert right?

---

### Post by coffeecat on 2011-01-08
To be honest, I don't know. I've seen varying reports about the performance of the OS driver with the 5*** series - but that was with Maverick. The OS ATI driver *ought* to be better in Natty, but whether that's so with your card...

---

### Post by rajeev1204 on 2011-01-13
> **ELD said:**
> So as usual with later versions of Ubuntu the catalyst amd/ati drivers don't support Ubuntu Unity yet.

Is there a way for me with this hardware to be able to actually test Unity?


Unity wont work with the catalyst driver.The open source drivers will get you unity.Iam not sure if those work with the latest 5000 series cards though.

And with a new version of xorg coming, i think proprietary drivers wont work for either nvidia or ATI unless nvidia have already patched their driver.

But as far as ATI is concerned, some of those gentoo or arch guys will patch the fglrx drivers soon like last time .

---

### Post by efflandt on 2011-01-13
You cannot install proprietary drivers on a live iso on CD or USB.  But default ATI drivers work for Unity in Natty with legacy ATI cards (like X1300 on an old PC).  I don't have any newer ATI cards.

nvidia-current works with Natty Unity in a regular installation.  Although, text consoles (tty) are often messed up with nvidia drivers (login in lower right of screen 3-1/2 lines from bottom) maybe because my nvidia model is too new to be recognized by kernels.

---

