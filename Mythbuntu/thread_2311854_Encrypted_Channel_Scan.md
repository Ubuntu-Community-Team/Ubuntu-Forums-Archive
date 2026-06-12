---
title: "Encrypted Channel Scan"
date: 2016-01-30
forum: Mythbuntu
---

### Post by vs-ruthless on 2016-01-30
Hi,

Having issues scanning for channels with my WinTV NOVA-HD-S2 pci card, I've got a good signal/noise but on the channel scan they are all encrypted.

[B]Program 54050, Encrypted
Transport ID 2104 --Found 26 probable channels[/B]

Any ideas?
[h=1][/h]

---

### Post by lisati on 2016-01-30
It is possible that at least some of them are [pay television]("https://en.wikipedia.org/wiki/Pay_television") channels that require you to pay a fee before you can view them.

---

### Post by vs-ruthless on 2016-01-30
Hi Lisati,

The whole scan is like it, even though I've set the san to unecrypted only.

I've had the card working for years but had to format the HDD as it failed one day and now I just cannot get the thing to work. 

Would the wrong firmware cause this issue?

---

### Post by vs-ruthless on 2016-01-30
Just ran 
scan -x0 /usr/share/dvb/dvb-s/Astra-28.2E | tee channels.conf

And it worked normally found scrambled as well as normall bbc etc

But still wont find channels when scanning with mythtv

---

