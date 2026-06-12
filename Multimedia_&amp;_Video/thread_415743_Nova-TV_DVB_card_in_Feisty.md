---
title: "Nova-TV DVB card in Feisty"
date: 2007-04-20
forum: Multimedia &amp; Video
---

### Post by Verlaine on 2007-04-20
After upgrading I found that my TV card was not being found by Mythtv. The card I have is the conexant chipset  and was found again by running.

sudo modprobe cx88-dvb
Hope this helps anyone with the same problem.

---

### Post by *desk* on 2007-04-27
Thank you so much Verlaine......I have been trying for ages to get my TV to work since I changed to Feisty.
I'm using Kaffeine but I had the same problem......not any more, it's now working great, thanks again.

---

### Post by *desk* on 2007-04-29
Although running:-
 "sudo modprobe cx88-dvb" does make Kaffeine acknowledge DVB, it only lasts until I power down. I need to re-introduce the command when I power up again......how do I get over this problem?

---

### Post by re-cre8 on 2007-04-30
Thanks to Verlaine, -got dvb working and have set system to Hibernate which solves the problem.

---

### Post by el1 on 2007-05-06
> **Verlaine said:**
> After upgrading I found that my TV card was not being found by Mythtv. The card I have is the conexant chipset  and was found again by running.

sudo modprobe cx88-dvb
Hope this helps anyone with the same problem.

thanks :) now it works again.

---

### Post by Verlaine on 2007-05-11
> ***desk* said:**
> Although running:-
 "sudo modprobe cx88-dvb" does make Kaffeine acknowledge DVB, it only lasts until I power down. I need to re-introduce the command when I power up again......how do I get over this problem?

Edit your /etc/modules and add
```
cx88_dvb
```

---

