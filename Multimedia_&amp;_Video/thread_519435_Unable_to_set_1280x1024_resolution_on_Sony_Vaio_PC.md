---
title: "Unable to set 1280x1024 resolution on Sony Vaio PCG-FX900"
date: 2007-08-07
forum: Multimedia &amp; Video
---

### Post by josuna on 2007-08-07
I recently installed Ubuntu 7.04, yes I made the leap to the Linux world :) 
I am unable to set 1280x1024 resolution on my Sony Vaio PCG-FX900 computer. When I installed Ubuntu I had to use the alternative intall disk since all I would get was a black screen when I ran the live CD. So I manage to install it and when the laptop booted up for the first time again, a black screen. I modified my xorg.conf file and removed the 1280x1024 setting from it so that it would default to the next lower and finally I was able to get a screen. Also, a strange behavior is that I can't see the splash screen, my computer boots up and I get a blank screen and then the login screen. How can I fix this? I want to use 1280x1024. I have attached a copy of my hardware components list and xorg.conf file. 

Thanks in advance!

---

### Post by pmagill on 2007-08-07
Alright I had a search around for you and I think what you need is the 915resolution driver fix...
I cannot be sure but I think your card is covered (Intel Corporation 82815 CGC)
Check this wiki for further instructions [https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0012b0864e7183632e672b122a1ba09ed9b4dcb6](https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0012b0864e7183632e672b122a1ba09ed9b4dcb6)

---

### Post by josuna on 2007-08-08
Thanks for the tip, I tried this but it does not detect my video hardware ... I guess I might just be out of luck.... maybe I'll go back to windows because I just don't like the resolution.

---

### Post by pmagill on 2007-08-12
you always give up so easily ;)

---

