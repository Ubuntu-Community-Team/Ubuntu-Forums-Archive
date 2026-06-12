---
title: "Karmic: ath5k wifi super slow"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by wannabegeek on 2010-08-10
hi all

I have searched around and know that many people have had problems with the ath5k driver on Lucid, but I am having really slow speeds with karmic...

did lspci  but didn't see the listing for the wifi...I'm using a different machine now since the
other is so slow its hard to do anything with..

Is there a back port I should be using ?

thanks a ton in advance, wifi issues are some of the most frustrating...
wbg

---

### Post by benloyola on 2012-02-15
try this, it worked for me:

Code:
sudo -s

echo "options ath5k nohwcrypt=1" > /etc/modprobe.d/ath5k.conf
and reboot!

---

### Post by oldos2er on 2012-02-15
Closed, necromancy.

---

