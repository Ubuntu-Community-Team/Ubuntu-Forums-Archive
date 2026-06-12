---
title: "WiFi connects to the wrong ESSID"
date: 2009-05-06
forum: Networking &amp; Wireless
---

### Post by WitchCraft on 2009-05-06
Hi, question:

I use the gnome network manager applet (standard) to switch my wireless networks.

My two networks have ESSID
```

UnencrypedNetwork
4322 1276

``` 

and according to 
```

iwlist eth0_rename scanning | grep "ESSID" | sed 's/ESSID://;s/\"//g;s/^\s*//g;s/\s*$//'

```

This is correct. 4322 1276 is a wireless modem and Unenc... is a wirless router connected to a cable modem.

Now when I am with a laptop nearby and want to join "Unencrypted Network", then that works, but when I want to join "4322 1276" it ends up joining "Unencrypted Network"...

what's wrong (it works on windows...)?
Can I do it manually on the command line? How?

---

