---
title: "wireless wont work on satelitte pro l40 - aetheros 5700eg"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by mark_andrew_robinson on 2009-01-31
have search hi and low to solve my aetheros issue and everything seems to crash my pc to the piont were I have to re-install ubuntu. 

I have a satelitte pro l40 with an aetheros 5700eg wireless card and im running ubuntu 8.10 i have no way of using internet on pc with ubuntu. can anyone help?

Regards

---

### Post by DroKZ on 2009-01-31
Hello Mark,

Did you already found this solution?
[http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899)

It worked like a charm on my Fujitsu with Atheros card.

Kind regards,
Jos

---

### Post by mark_andrew_robinson on 2009-01-31
thanks for reply but cant get on the internet on the pc with ubuntu on it.

Regards 
mark

---

### Post by DroKZ on 2009-01-31
And what if you download all these files and put them on a usb to that other pc?

---

### Post by mark_andrew_robinson on 2009-01-31
the closest i've come to making it work is:

i downloaded madwifi 0.9.4 and copied it from a usb stick into the /usr/src folder and decompressed the tarbell.

i change directory to: /usr/src/madwifi-0.9.4

which is fine

then i try to make the drivers

sudo make clean -> works fine
sudo make -> the first time it prompted to remove old drivers which i did but it comes up with make: *** [modules] Error 2
sudo make install ->which comes up with make: *** [install-modules] Error 1

i seem to be getting close but have got a feeling i'm missing something stupidly simple ](*,)!!

any ideas??

---

### Post by Reiger on 2009-01-31
Yes. There is another thread on the same forum page which brings up some useful ideas/pointers/links: [http://ubuntuforums.org/showthread.php?t=1056146](http://ubuntuforums.org/showthread.php?t=1056146).

---

