---
title: "Problem with wireless and acpi"
date: 2005-12-16
forum: Networking &amp; Wireless
---

### Post by TiteFleur on 2005-12-16
Hello,
First I'm french so I'm sorry for my bad english.
I've the fast speed clock problem on my laptop, and I've put the option "noapic acpi=off" in my grub, but it's not practical because I need the acpi, for the battery for example...
I've searched a lot about it, and I've found a new solution, it's the option "notimeracpi" (or noapictimer, I don't remember, sorry), and it's very good, the fast speed clock problem is solved, and I've acpi now :)
But a new problem has appeared...
My wireless connection doesn't work now !

It seems to be a problem of irq, so I've added the option "acpi=noirq" in my grub, and it's ok while two seconds, and then nothing runs again.

I don't understand how to do...
I use ndiswrapper for my wireless card.

In another forum I've found that :

[HTML]I was partially right with my last post.
The ndiswrapper and ethernet drivers both use IRQ 10, as does the ATI IXP driver.
Normally, no problems. But if the sound driver grabs the IRQ first,
then something in the kernel throws a hissy fit with ongoing network activity on that same IRQ.
It's really wonky, and I don't understand it, but that's the truth of the matter.
To fix the problem, I had both the 8139too and ndiswrapper drivers load before the ALSA init script ran.
That way, the network driver is always the "primary" owner of the IRQ.
If I'm daring enough, I might delve into the ATI IXP driver code and see why it behaves that way.[/HTML]


But do you think it's my problem ?
And if yes, how to change the order of the beginning of the modules ?
Thanks a lot

Marion

---

### Post by TiteFleur on 2005-12-16
It seems to be ok.
For the one who will be interested by the solution, I've edited the file /etc/modules, and have added in the end :
8139too
ndiswrapper

I boot with the option "noapictimer acpi=off"
My wireless connexion is ok, and I've the acpi :)

---

### Post by almahtar on 2006-02-19
Merci beaucoup, TiteFleur!  Sil vous plait, pardonne mon fautes de grammaire: Je suis Anglais, et j'ais oubliee beaucoups de Francais depuis lycee.

Merci a vous, mon problème est résolu.\\:D/

---

