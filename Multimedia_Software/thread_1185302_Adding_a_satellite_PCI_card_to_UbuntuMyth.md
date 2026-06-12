---
title: "Adding a satellite PCI card to Ubuntu/Myth"
date: 2009-06-12
forum: Multimedia Software
---

### Post by MartyBuntu on 2009-06-12
Right now I have a Hauppauge PVR-150 card in my Kubuntu/Myth 7.10
setup, but I'll be re-doing that system to Mythbuntu 9.04 when my satellite card I purchased arrives.

Anyone have any experience with satellite cards in MythTV/Ubuntu?

The card I'm getting is a **VisionPlus VP1020A** DVB-S Satellite Card.

---

### Post by MartyBuntu on 2009-06-15
bump

---

### Post by pauna on 2009-06-16
> **MartyBuntu said:**
> 
Anyone have any experience with satellite cards in MythTV/Ubuntu?

The card I'm getting is a **VisionPlus VP1020A** DVB-S Satellite Card.

I've got a freeview DVB-S card in my MythBuntu 8.04 box and it works just fine. 

I don't have direct experience whether your particular card works, but according to [this]("http://www.linuxtv.org/wiki/index.php/Twinhan_VP-1020A") it should work ok although the corrupted EEPROM issue looked interesting.

Anyway, you just need to put it in your box, boot and check with dmesg that your kernel recognized it. If it did, you hook it up to your dish and go to MythTV configuration to create a new input device and give details.

---

### Post by MartyBuntu on 2009-06-17
I just received the card yesterday. I am going to do the dish setup tomorrow and the Mythbuntu installation this weekend. I'll let you know how it turns out.

---

### Post by TKBuisan on 2009-07-10
An update on the Sat Card set up?
Thanks,
TKBuisan

---

