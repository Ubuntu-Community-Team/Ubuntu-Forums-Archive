---
title: "Upgraded - belkin wireless PCMCIA wont work"
date: 2006-06-17
forum: Networking &amp; Wireless
---

### Post by Gsyman on 2006-06-17
Upgraded to 6.06 on my Dell inspiron 5100. All worked fine before in Breezy, but now I have no network as the Belkin F5D6020u Ver2 card won't function.
Anything I can try, or do I need a different card?
Thanks.

---

### Post by miceagol on 2006-06-17
I would suggest a clean install of Dapper Drake, it [solved my problems]("http://ubuntuforums.org/showthread.php?t=193197"). Or if you can manage it without a clean install: Remove ndiswrapper, blacklist the buillt-in bcm43xx-driver in Dapper Drake and reinstall ndiswrapper from the beginning.

Check the above link on how to blacklist.

---

