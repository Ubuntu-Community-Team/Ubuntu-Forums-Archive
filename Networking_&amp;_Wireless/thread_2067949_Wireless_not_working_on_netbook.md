---
title: "Wireless not working on netbook"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by kamikazeredneck on 2012-10-08
I have a Toshiba NB505 and I have looked everywhere about the wireless not working like mine is and everything I have done doesn't seem to work. I am somewhat new to the ubuntu world so I will probably need step by step instructions.

Thanks so much,

Patrick

---

### Post by albandy on 2012-10-08
> **kamikazeredneck said:**
> I have a Toshiba NB505 and I have looked everywhere about the wireless not working like mine is and everything I have done doesn't seem to work. I am somewhat new to the ubuntu world so I will probably need step by step instructions.

Thanks so much,

Patrick

Connect throught network cable and do the following:

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkms

then restart your computer.

---

