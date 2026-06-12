---
title: "how to set 3g or hsdpa with mobile broadband?"
date: 2010-01-13
forum: Networking &amp; Wireless
---

### Post by Zack_PSP on 2010-01-13
hey guys. i have both a vodafone and 3 mobile broadband dongles. they both work out of the box, however i am only getting gprs, while i can get 3g/hsdpa using my windows box. is there any gui configuration manager or terminal commands i can use to set it to 3g/hsdpa only? im running ubuntu 9.10. thanks for any help!

---

### Post by alexfish on 2010-01-13
hi

this site is worth a vistit

[http://www.pcurtis.com/ubuntu-mobile.htm#at_commands](http://www.pcurtis.com/ubuntu-mobile.htm#at_commands)

---

### Post by Zack_PSP on 2010-01-13
The guide seems a bit outdated however and not very specific on the key points. Anything else ? 

I have googled for ages but am failing to find updated info.

---

### Post by alexfish on 2010-01-13
> **Zack_PSP said:**
> The guide seems a bit outdated however and not very specific on the key points. Anything else ? 

I have googled for ages but am failing to find updated info.

there are various factors involved  IE:limitations set but your service provider

the easiest route is to have them unlocked ; also if your service provider has a slow server try open servers ; the guide I have shown you will lead you in the right direction

some service providers have  tools available from the windows setup, there is a clue


Until the the Service Providers provide the same Tools in Linux then you will have to rely on the AT commands

[PDF] [B][*At Commands* Manual]("http://www.sics.se/%7Ebg/GC75-AT-Commands-R2A.pdf")

[/B][PDF] **[*AT Command Reference*]("http://www.sierrawireless.com/documents/support/2130213_GSM_AT_Command_Ref_r3.2.pdf")**

---

### Post by pdc on 2010-01-14
I have found wvdial very useful; George Vitas has posted what works for him as a wvdial.conf file; and it similarly worked for me; 

> sudo apt-get install wvdial and that I believe should cope with dependencies

If I leave you to check this out if you want to

---

