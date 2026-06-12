---
title: "Hardy static wireless ip"
date: 2010-03-27
forum: Networking &amp; Wireless
---

### Post by nnomad on 2010-03-27
Hi all. Very recent convert. Dual booting on 4 pc's and trying to convert 4 family and friends. All is good and loving Ubuntu. Fixed most problems by reading this great forum! I don't usually post in forums as spending time reading and doing it yourself you learn more and faster, don't like being spoon fed. Can't seem to fix this one though. Static wireless ip works fine till reboot then I have to re-enter WPA key and click ok in NM, yet key is sent at renewal cycle. Only have a problem at boot. Is NM not sending WPA Key at boot?

Ubuntu 8.04.4 LTS. WRT54G will not assign IP by MAC addy. Thanks in advance.
Can't wait to try Lucid!

---

### Post by chili555 on 2010-03-28
I think Wicd will do so. If these are stay-at-home desktop machines, I wonder why you need Network Manager when manual configuration will do so well. Maybe family and friends don't need or want to be writing configuration files, but if this is a set it and forget it situation, maybe once, by you, is enough.

I wonder if you have edited your connection in Network Manager to ask it to connect automatically. See attached and ignore the 'Manual' part.

---

### Post by R.Bucky on 2010-03-28
It may be a work around for you, but you could also try only allowing know MAC addresses instead of WEP or WPA, which are easily cracked in Linux. I only have wireless in my home for a couple of iPhones and restrict access to our MAC's.

---

### Post by kestrel1 on 2010-03-28
Personally I would upgrade from hardy. It is two years old now & 9.10 may work a bit better with wireless. Trying out Lucid beta 1 at present & so far it is good. Only a few small problems, but it is a beta.

---

### Post by nnomad on 2010-03-28
chili555: Sadly there is no auto/man in my NM but WICD did the trick. Thanks for taking the time to reply.

R.Bucky: If I use MAC filtering Ubutu machine steels windows ip on boot?

Kestrel1: Yes was going to clean install 9.10 but may as well wait for lucid.

Thanks all for taking the time and replying to my post.

---

### Post by kestrel1 on 2010-03-28
> **nnomad said:**
> chili555: Sadly there is no auto/man in my NM but WICD did the trick. Thanks for taking the time to reply.

R.Bucky: If I use MAC filtering Ubutu machine steels windows ip on boot?

Kestrel1: Yes was going to clean install 9.10 but may as well wait for lucid.

Thanks all for taking the time and replying to my post.
Yes Lucid is looking real good and the wait until April 29th can't come soon enough. Even Beta 1 is great.

---

