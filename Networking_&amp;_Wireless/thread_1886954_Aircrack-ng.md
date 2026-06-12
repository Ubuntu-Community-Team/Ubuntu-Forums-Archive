---
title: "Aircrack-ng"
date: 2011-11-25
forum: Networking &amp; Wireless
---

### Post by Alphamonkey on 2011-11-25
Well, this may sound weird but I was running fedora previously and had been playing around with backtrack5 on my USB drive. Well fedora was giving me problems with certain programs so I decided to go back to Ubuntu because I like the Ubuntu forums better for help. Well my internet is really slow so I decided to just install back track and then upgrade the kernel from there. Now I have 11.10 installed.
        
       The problem I am having is that I can not get aircrack-ng to work. I keep getting an error saying:

aircrack-ng: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory

airmon-ng works fine in order to enable monitor mode and everything was working fine before I upgraded the kernel. I have tried reinstalling aircrack-ng since then with apt-get and also I purged it with apt-get and installed it again. I still am getting the same error. If anyone knows how to fix this error please let me know. If you need anymore information I will be glad to give it.

Thanks.

---

### Post by Dangertux on 2011-11-25
> **Alphamonkey said:**
> Well, this may sound weird but I was running fedora previously and had been playing around with backtrack5 on my USB drive. Well fedora was giving me problems with certain programs so I decided to go back to Ubuntu because I like the Ubuntu forums better for help. Well my internet is really slow so I decided to just install back track and then upgrade the kernel from there. Now I have 11.10 installed.
        
       The problem I am having is that I can not get aircrack-ng to work. I keep getting an error saying:

aircrack-ng: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory

airmon-ng works fine in order to enable monitor mode and everything was working fine before I upgraded the kernel. I have tried reinstalling aircrack-ng since then with apt-get and also I purged it with apt-get and installed it again. I still am getting the same error. If anyone knows how to fix this error please let me know. If you need anymore information I will be glad to give it.

Thanks.

Have you tried making sure libssl is installed?

```

sudo apt-get update && sudo apt-get install libssl0.9.8 libssl-dev

```

That will probably fix it.

---

### Post by Alphamonkey on 2011-11-25
Well, after doing that aircrack-ng worked however airodump-ng didn't lol. I did another reinstall and now everything seems to be working fine. Thanks you very much for your help. Still new to operating linux don't know what I would do without the forums. Thanks again.

---

