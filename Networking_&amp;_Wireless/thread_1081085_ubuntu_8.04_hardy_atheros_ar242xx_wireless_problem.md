---
title: "ubuntu 8.04 hardy atheros ar242xx wireless problem"
date: 2009-02-26
forum: Networking &amp; Wireless
---

### Post by un84 on 2009-02-26
ubuntu 8.04 hardy heron
atheros ar242xx wifi

ndiswrapper & windows wifi driver


machine hangs after 3 mins if wireless is enabled.
Installation process:

I disabled default driver for wifi driver, installed madwifi and it does not work, so i tried ndiswrapper using winxp inf file, it works but the machine hangs 3min after it connects to a wireless network

i also read a post here in ubuntuforums.org pointing to a special driver from madwifi.org for ath242xx wireless but all these links are dead. Thats why i had no choice but to use windows driver.

Please help

---

### Post by Reiger on 2009-02-26
You have read about ath5k. If you are willing to update to Intrepid Ibex the ath5k driver should work, just install the linux backport modules.

---

### Post by binbash on 2009-02-26
Please read my blog post here : 

[http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html](http://ubuntushell.blogspot.com/2009/02/how-to-get-your-atheros-ar242x-working_25.html)

That is how i got it working.Feel free to Pm me, comment or write here : )

---

