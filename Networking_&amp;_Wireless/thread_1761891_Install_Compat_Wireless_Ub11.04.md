---
title: "Install Compat Wireless Ub11.04"
date: 2011-05-18
forum: Networking &amp; Wireless
---

### Post by Morce on 2011-05-18
I have been trying to install compat wireless, because my internet drops when the download speed is to high (around 700kb\s), but when i activate the ath9k driver the computer just freezes ...

Does anyone know what i can do to have this working?
I'm installing according to [http://wireless.kernel.org/en/users/Download](http://wireless.kernel.org/en/users/Download)

Thank you.

---

### Post by jawilljr on 2011-05-18
Did you install the bleeding edge version? If so, try the latest stable version.

Jerry

---

### Post by Morce on 2011-05-18
thank you for the fast reply.

I tried with the stable version and got the same problem. as soon as i do the "modprobe atk9" the OS freeze's... 

Any other solution ?

Thank You.

---

### Post by mcmxxx on 2011-05-24
I would try using a build from early April. I had the same issue and that seemed to resolve it except every now and then the wireless driver stops responding and I lose internet, but with a 'modprobe -r ath9k' and then 'modprobe ath9k' it will come back on. 

quite annoying... looking to see if an older build is more stable.

---

