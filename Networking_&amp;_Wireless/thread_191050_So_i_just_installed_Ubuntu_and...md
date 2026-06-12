---
title: "So i just installed Ubuntu and.."
date: 2006-06-07
forum: Networking &amp; Wireless
---

### Post by Skythe on 2006-06-07
I have 2 issues :)

First, i'm unsure how to configure my modem correctly to access the internet. I installed ubuntu dual-boot with windows but as anticipated from.. using the liveCD i couldn't access the internet. I'm with an Australian ISP.. Telstra Bigpond.. i've searched around for a few forum posts but i'm still quite confused as how to work it. I have ADSL, and the modem i use to connect is a SpeedTouch 530 which is connected to my computer via USB. I installed it with windows using the mandatory installation CD that was included (which obviously has no linux support..) and i tried using the ubuntu setup client-whatsit but got stuck on my ISP phone number [-( 

Issues 2 is to do with the fact that i cannot view or edit the partitions i created when installing ubuntu. I partitioned my 40GB HDD into linux/windows and left my 80GB one with all my files on it but now i can't access the 80 from ubuntu :(

Anyhow, any help would be greatly appreciated.

---

### Post by jbrader on 2006-06-07
What filesystem is the 80 gig?

---

### Post by Skythe on 2006-06-07
NTFS. 

I remember being able to access all my files when i tried a linspire liveCD :/

---

### Post by Skythe on 2006-06-07
I managed to get all my partitions/etc working correctly from ubuntu (how can i make my ubuntu partition viewable in windows?).

So now. the only problem is #1. Getting the internet working. Any ideas?

---

### Post by jbrader on 2006-06-07
Windows can't see ext3 partitions by itself, there are 3rd party solutions for fixing that (like [this one]("http://e2fsprogs.sourceforge.net/ext2.html") though I don't know how well it will work). As to your modem problem I'm afraid I havn't got the foggiest as I'm on cable, you could try searching the forums for "winmodem" though.

---

