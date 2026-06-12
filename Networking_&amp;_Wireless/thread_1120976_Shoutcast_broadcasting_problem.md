---
title: "Shoutcast broadcasting problem"
date: 2009-04-09
forum: Networking &amp; Wireless
---

### Post by da_velos_code on 2009-04-09
Hello all,

I'm facing some problems with shoutcast broadcasting radio and I'd appreciate any help.

I have installed **sc_serv_1.9.8_Linux** and **ices-0.4 ** in order to make my own internet radio station.

It works perfectly with [http://localhost:8000](http://localhost:8000) on my pc, but I'd like my music to be listened by other computers as well.

I try [http://xxx.xxx.xxx.xxx:8000](http://xxx.xxx.xxx.xxx:8000) where xxx.xxx.xxx.xxx is my current IP but it doesn't seem to work. Any ideas/suggestions about how I'll make it works?

I use Ubuntu8.10 and a modem/router BaudTec.

Thank you in advance.

---

### Post by jpeddicord on 2009-04-09
> **da_velos_code said:**
> 
I try [http://xxx.xxx.xxx.xxx:8000](http://xxx.xxx.xxx.xxx:8000) where xxx.xxx.xxx.xxx is my current IP but it doesn't seem to work.

You set that in the Shoutcast config? In that case, try 0.0.0.0, which is a special IP (or lack of) that allows all others to access it.

---

### Post by da_velos_code on 2009-04-09
> **jacobmp92 said:**
> You set that in the Shoutcast config? In that case, try 0.0.0.0, which is a special IP (or lack of) that allows all others to access it.


Where exactly do I have to set it in config?
Could you explain further the special IP 0.0.0.0?

Thanx a lot!!O:)
dvc

---

