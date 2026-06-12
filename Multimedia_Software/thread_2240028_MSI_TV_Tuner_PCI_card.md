---
title: "MSI TV Tuner PCI card"
date: 2014-08-17
forum: Multimedia Software
---

### Post by gordie692 on 2014-08-17
Hey guys I posted this awhile ago but didn't get an answer I have a MSI tv tuner pci card and I'm running W7 because I can't fine a software to run it in Ubuntu I run my satellite through it and if I can get Ubuntu to work I'd just go Ubuntu but I'm just googling answers how to run this card through linux

---

### Post by Yellow Pasque on 2014-08-18
"MSI Tuner card" is vague. Do you at least know what chipset/driver it uses? Give the lspci info for it:
```
sudo update-pciids
lspci -k
```

---

### Post by gordie692 on 2014-08-18
thats what you type in terminal
is there anything in the software center

---

### Post by Yellow Pasque on 2014-08-18
> thats what you type in terminal
Yes, please give the output from those commands.

> is there anything in the software center 
Possibly, but until we know what kind of card you have, it's impossible to give advice.

---

### Post by gordie692 on 2014-09-18
Thanks I typed it in but what software do you you use to watch tv after typing this command

---

### Post by Vladlenin5000 on 2014-09-21
> **gordie692 said:**
> Thanks I typed it in but what software do you you use to watch tv after typing this command

Again, [COLOR=#000000]**_please_ give the output from those commands**. Is it so hard to understand that a) those commands will identify your hardware and b) nobody can give you any help without knowing how the hardware is being recognized.[/COLOR]

---

### Post by deadflowr on 2014-09-21
> **gordie692 said:**
> Thanks I typed it in but what software do you you use to watch tv after typing this command

Well, as stated it would be helpful to know the card. But that said, TV watching programs include me-tv, tvtime(which stinks sometimes) mythtv(slightly complex) and for me lately, kaffeine. The problem I have with kaffeine, though, is that it's a kde app and as such brings in a bunch of kde dependencies.
But outside of kde dependencies I find kaffeine to be outstanding and I would highly endorse it because it works well, and is super simple to understand.

---

