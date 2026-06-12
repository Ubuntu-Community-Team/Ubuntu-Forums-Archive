---
title: "wired connection problem"
date: 2010-08-06
forum: Networking &amp; Wireless
---

### Post by 562sparky562 on 2010-08-06
hello,

i'm having problems connecting to the internet unless i manually enter the IP info.

automatic DHCP does not work.

I'm on a dual boot machine vista/ubuntu 10.04 LTS

connecting to the internet through a lynksys wireless g router and a cable modem.

please help 

thanks

---

### Post by dineshs on 2010-08-07
> **562sparky562 said:**
> 
i'm having problems connecting to the internet unless i manually enter the IP info.
thanks
You mean you have to run ifconfig command everytime you start?You can configure NM .Have you tried that?

---

### Post by 562sparky562 on 2010-08-07
i fixed it.

uninstalled network manager and installed wicd network manager and rebooted.

i don't have to type in manually the ip address netmask and dns because it appears dhcp is now working. =)

---

