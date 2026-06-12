---
title: "Sony Ericsson Phones and MTP"
date: 2008-07-27
forum: Multimedia Software
---

### Post by oronte on 2008-07-27
I'm using Hardy 64 bit and my brother's Walkman phone is correctly recognised as a digital music player, but my P990 is recognised as a 'removable hard disk'. The implication is that it won't work in Rhythmbox and Banshee (it kind of works in Amarok, but I'd rather use Rhythmbox). How do I mount it as a 'digital music player'? I assume any solution for a non-Walkman phone would apply.

---

### Post by oronte on 2008-08-12
Anyone?

---

### Post by aquamammal on 2008-09-15
I have the same problem.

I just got a Sony Ericsson 760, and it's not even showing up on my computer.

Using Hardy.

Thanks.

---

### Post by oronte on 2008-09-15
> **aquamammal said:**
> I have the same problem.

I just got a Sony Ericsson 760, and it's not even showing up on my computer.

Using Hardy.

Thanks.

No you don't. If your phone is a W760 then when you do connect this will not be a problem. Hardy should recognise it, try putting it in Mass Storage mode before you connect, you may need to format your memory stick first (you can do this from the options menu on your phone). Also if you're using Bluetooth try connecting with the USB cable. Finally when you connect check the system log and see if it comes up.

---

### Post by aquamammal on 2008-09-16
Haha, yeah, I tried what you said before. This is what popped up in my log.

Sep 16 09:09:51 Weapon kernel: [15962.429521] end_request: I/O error, dev sdb, sector 120025
Sep 16 09:09:51 Weapon kernel: [15962.429552] sd 13:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 16 09:09:51 Weapon kernel: [15962.429558] end_request: I/O error, dev sdc, sector 32
Sep 16 09:09:51 Weapon kernel: [15962.429632] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 16 09:09:51 Weapon kernel: [15962.429637] end_request: I/O error, dev sdb, sector 120080
Sep 16 09:09:51 Weapon kernel: [15962.429647] sd 13:0:0:1: [sdc] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 16 09:09:51 Weapon kernel: [15962.429652] end_request: I/O error, dev sdc, sector 32
Sep 16 09:09:51 Weapon kernel: [15962.429868] sd 13:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
Sep 16 09:09:51 Weapon kernel: [15962.429874] end_request: I/O error, dev sdb, sector 120081
Sep 16 09:09:51 Weapon kernel: [15962.431285] scsi 13:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
Sep 16 09:09:51 Weapon kernel: [15962.431293] end_request: I/O error, dev sdb, sector 120088

Something like it. The whole error stuff is much longer.

I'm going to try to make the blue tooth work, but there are issues with the pass code~ argh. 

******* MTP.

---

### Post by aquamammal on 2008-09-16
Never mind. I think the send function is find. I just can't connect because of the passcode. 

Anyways, it's more forum searching now.

I want to use the USB though.

---

