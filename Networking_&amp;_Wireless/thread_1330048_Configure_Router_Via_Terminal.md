---
title: "Configure Router Via Terminal"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Shamess707 on 2009-11-18
Is it possible to edit my router's settings via the terminal in Ubuntu? I have a linksys WRT110.

Thanks

---

### Post by dmizer on 2009-11-18
> **Shamess707 said:**
> Is it possible to edit my router's settings via the terminal in Ubuntu? I have a linksys WRT110.

Thanks

No. According to the specs on that router, you can only configure it via HTTP, HTTPS, or UPnP. Some routers allow configuration via tellnet, but the wrt110 does not unless you're running alternative firmware.

---

### Post by Shamess707 on 2009-11-18
Well that is a shame, Thank you very much.

---

### Post by Shamess707 on 2009-11-18
Alright lets say I have a WRT54Gv6 that is running DD-WRT firmware? I am attempting to follow there wiki but it appears to be missing some steps

---

### Post by Iowan on 2009-11-18
> **Shamess707 said:**
> Is it possible to edit my router's settings via the terminal in Ubuntu? I'm curious why you'd want/need to. There are text-mode browsers (like **elinks**). I managed to use **elinks** with phpMyAdmin on my server - but it wasn't a pleasant experience.

---

### Post by dmizer on 2009-11-18
> **Shamess707 said:**
> Alright lets say I have a WRT54Gv6 that is running DD-WRT firmware? I am attempting to follow there wiki but it appears to be missing some steps

The DD-WRT wiki is very thorough: [http://www.dd-wrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line](http://www.dd-wrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line)

---

### Post by Shamess707 on 2009-11-19
> **dmizer said:**
> The DD-WRT wiki is very thorough: [http://www.dd-wrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line](http://www.dd-wrt.com/wiki/index.php/Telnet/SSH_and_the_Command_Line)




I attempted to follow that page but under my services tab there is no Enable SSHd option. I am running version 24 of dd-wrt. I apologize for continuing the issues I realize that this is in fact a Ubuntu forum.



I am more just curious about the issues, it is not really a necessity

---

### Post by dmizer on 2009-11-19
> **Shamess707 said:**
> I attempted to follow that page but under my services tab there is no Enable SSHd option. I am running version 24 of dd-wrt. I apologize for continuing the issues I realize that this is in fact a Ubuntu forum.



I am more just curious about the issues, it is not really a necessity

Indeed, you're better off taking this discussion over to the DD-WRT community because they're more likely to give you specific help. I have no experience with DD-WRT, so all I can do is point you at the Wiki.

---

