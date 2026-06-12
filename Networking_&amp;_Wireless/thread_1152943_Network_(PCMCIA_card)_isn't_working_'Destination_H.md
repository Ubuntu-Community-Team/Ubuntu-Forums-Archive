---
title: "Network (PCMCIA card) isn't working 'Destination Host Unreachable'"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by benAmi on 2009-05-08
Hi,

I try using Ubuntu 8.04 on an old computer (Sony Vaio). Ubuntu is installed and every configured correctly (at least to my knowledge). The only thing that, beside the USB, doesn't work is the PCMCIA ethernet card (Model net-LYNX LM560). It seems that the card is installed correctly in the system and 'ifconfig eth0' shows nothing strange.

ping computername or ping localhost works. Pinging any other computer doesn't work. Error message: Destination Host Unreachable. I double checked all settings and I am pretty sure they are correct.

Only hind is a 'cat /var/log/messages', which tells me after a ping attempt: "... kernel: [...] eht0: trigger_send() called with the transmitter busy".
If I remove the PCMCIA card I get the same behaviour. 

Sorry that I can't send log files but I don't have any working connection to that computer ;)

Any suggestions?

Thanks a lot!

---

### Post by superprash2003 on 2009-05-08
you may not be getting an ip.. post output of ***ifconfig*** from the terminal

---

