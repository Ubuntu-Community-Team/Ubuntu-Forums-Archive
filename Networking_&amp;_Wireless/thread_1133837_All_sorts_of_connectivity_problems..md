---
title: "All sorts of connectivity problems."
date: 2009-04-23
forum: Networking &amp; Wireless
---

### Post by Johanne on 2009-04-23
Hi !
Just got ubuntu last night, and now I've been looking around without any luck. I've got an Acer Aspire 5310, ubuntu 8.10 an the wireless card is an AR242x 802.11abg wireless pci express adapter (says ubuntu).
I found a thread with a description on how to do, but nothing worked.
 
Anyone who can help with detailed 'How to'-guides ?
 
Thank you
- Johanne

---

### Post by Tobi-fp on 2009-04-23
I believe i can help, got the aspire one with the same card in it (i believe)..
it is an Atheros card, right?
anyways, i just did:

System -> administration -> hardware drivers, i turned of the driver and did in terminal:

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)

tar -xzf madwifi-hal-0.10.5.6-current.tar.gz

cd madwifi-hal-0.10.5.6*/

make

sudo make install

sudo modprobe ath_pci

and restarted it..


Anyways, you might be better of just upgrading to 9.04 now that its out.. That mght have fixed the bug :D

---

### Post by Johanne on 2009-04-23
Odense ! Hallelujah... Someone from Denmark :P
Anyhow - It's still screwing with me, and I can't download 9.04... I'm borowing the schools computers

---

