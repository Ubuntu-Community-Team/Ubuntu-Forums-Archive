---
title: "Ubuntu 12.04 and WPA2 router"
date: 2013-05-06
forum: Networking &amp; Wireless
---

### Post by EquuaPotesta on 2013-05-06
Fresh install of Ubuntu 12.04 today, tried connecting to my wireless with a WPA2.  Anytime I'm prompted to enter the pass phrase for the WPA2 protected router, it automatically acts as if the password type is WEP.

When I attempt to edit the connection, and force it to use WPA2 and the passcode i enter, it comes back with just and endless loop of attempting to connect, then prompting for a WEP code.

Any ideas?  I've seen some people have this issue on previous versions of Ubuntu but never found a solution

In the meantime I've basically just setup a guest network that hides the SSID and uses a WEP key until I can fix this issue.

Thanks guys

---

### Post by voipster on 2013-05-07
What hardware are you installed on?

---

### Post by EquuaPotesta on 2013-05-07
Here's my laptop:
[http://www.cnet.com/laptops/asus-x83vb-x2/4505-3121_7-33496180.html](http://www.cnet.com/laptops/asus-x83vb-x2/4505-3121_7-33496180.html)

Seems pretty standard to me but maybe I'm missing something

---

### Post by squakie on 2013-05-07
Can we see a couple of screen shots - particularly the prompt for the WPA2 key and the WEP key.    Does it actually say WPA2 or WEP?  If it truly is saying WEP, and if stops in an endless loop if you try WPA2 and comes back to WEP, I would suspect that perhaps your router is actually set for WEP, not WPA2.  You need to log in to the router, check the encryption, then change it to WPA/WPA2 and be sure to verify the password, then try it again.  Also, if there is anyone else using the router, be aware that you'll mess them up if you change things on the router.

---

### Post by EquuaPotesta on 2013-05-07
Sorry I'm just getting back to this (been a busy day)

Anyway here's the screenshots I've taken for this:

Find attached screenshots showing I am in fact using WPA security and that Ubuntu won't let me type in the 9 digit pass code because it doesn't fit the WEP formatting.

It just won't acknowledge that it's WPA rather than WEP

---

### Post by Bucky Ball on 2013-05-07
Please attach large images rather than putting them in the body of your post. Cheers. ;)

---

### Post by EquuaPotesta on 2013-05-07
Those take up my entire screen. They're hosted on imgur at: [http://i.imgur.com/gSkun1G.png](http://i.imgur.com/gSkun1G.png) and [http://i.imgur.com/LKcvpEF.png](http://i.imgur.com/LKcvpEF.png)

---

### Post by Gadgetech on 2013-05-08
It's possible that the Linux driver for your wireless card only supports WEP. You should be able to see what wireless chipset is used on you laptop by entering the following terminal command:
```
lspci
```

Once you know the wireless chipset, someone may be able to help.

---

### Post by EquuaPotesta on 2013-05-10
I assume I'd be looking at the "network controller" section of that printout.

"Intel Corporation WiFi Link 5100"

---

### Post by Bucky Ball on 2013-05-10
Now try this, it will tell us more:

```
sudo lshw -C network
```

PS: I have edited your post with the large screenshots; they are now attached and text edited accordingly. Have mercy on those with a small bandwidth (there are other reasons for not posting large images in the body of the post). Thanks. ;)

---

### Post by EquuaPotesta on 2013-05-15
Hey guys, it was something to do with the drivers released with ubuntu. I wiped and reloaded with Mint 14 and it works like a charm.

thanks anyway guys

---

### Post by Bucky Ball on 2013-05-15
Great news. Please mark thread as solved to help others by editing first post, click Go Advanced and change the title prefix to [SOLVED]. Thanks.

---

