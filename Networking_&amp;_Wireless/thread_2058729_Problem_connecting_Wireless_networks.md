---
title: "Problem connecting Wireless networks"
date: 2012-09-16
forum: Networking &amp; Wireless
---

### Post by lgducalg on 2012-09-16
Hello.

I installed yesterday the available/last version of ubuntu because I will need to work on it for some university courses(Robotics). Hereupon, I have to say I really don't know nothing about this operative system, therefore I need you to explain me very well what to do in a very exaustive way for you  

That said, the problem is:

Ubuntu recognize all wireless conections available but it is not capable of connect to anywhere.

Problem way:

Ubuntu request the router/connection password and it keeps asking for it in of space of few seconds, incapable to connect.
What I think it is in my little knowledge in this area:
Ubuntu don't recognize my wireless driver, or simply don't have available the drivers for it, and and designated a standard driver that is not stable.

Wireless card:
Bigfoot Killer-N 1102

Thx for your time.

> **chili555 said:**
> The Wild Man may be temporarily away. Since this thread is largely about ath5k, I suggest you start your own new thread and include:```
lspci -nn | grep 0280
```

The output for the code you ask:

```
04:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless L
AN adaptor [198c:0030]
```

Thx for your response

---

### Post by chili555 on 2012-09-16
> 04:00.0 Network controller [0280]: Atheros Communications Inc. AR9300 Wireless L
AN adaptor [198c:0030]Please double-check:```
lspci -nn | grep 0280
```I think it might be 1[COLOR="Red"]6[/COLOR]8c:0030.

If so, it's supposed to use the driver ath9k. Please run and post:```
sudo modprobe ath9k
dmesg | grep ath9
lsb_release -d
```Thanks.

---

### Post by lgducalg on 2012-09-17
Chili555 thx for your time, but a friend of mine already solved the problem. I think he just deleted the pre-defined driver and re-installed it again.
I can't explain very well the procedure.
Thank you

---

