---
title: "Wireless Doesnt turn on in 9.10"
date: 2009-11-16
forum: Networking &amp; Wireless
---

### Post by tpkaznowski on 2009-11-16
Hi i am a Ubuntu Newbie, 
I was currently on *Mint 7* and i decided to move to **ubuntu 9.10** because of a recommendation. when i used *mint 7* my wireless worked perfectly now i have moved over to **ubuntu** it doesn't turn on at all. When i search for it in the terminal it registers as disabled..... and my blue light is turned to orange.......
It doesn't show any networks available and i cant create networks....

Can someone help.....

My wireless is a **broadcom wireless** which is inbuilt in my **Hp pavilion laptop**....
Do i need to get special drivers or something?

Cheers

---

### Post by The Toxic Mite on 2009-11-16
"Broadcom wireless" isn't enough.

Can you go to Applications > Accessories > Terminal, and post the output of the following commands please?

```

lspci
sudo lshw -c network
iwconfig

```

:)

---

### Post by tpkaznowski on 2011-01-17
Hello All, 

I have recently bought a Revo 3700 with linpus linux already installed on it. I really want to install Ubuntu on the machine however I cannot boot from USB at all. I have tried everything.... Linpus looks aweful and it runs awefully.... Please someone help??

Taz

---

