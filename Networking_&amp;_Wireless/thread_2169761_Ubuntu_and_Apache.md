---
title: "Ubuntu and Apache"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by josh18 on 2013-08-23
Hi All, 
New here so I apologize if this is in the wrong place or wrong forum entirely. 
Have been using Ubuntu on and off for a few years, recently decided to convert my home server over to it. This runs a basic web server (HFS under wine),Serviio , teamspeak and a few other game related things. 

I am wanting to setup a Apache reverse proxy with SSL (self signed) to encrypt the traffic from hfs and serviio.
I haven't really used apache before and am having real trouble setting it up. 

If anyone can point me in the right direction or give me a detailed guide on how to do this I'd be very grateful.
HFS runs on port 8080 and serviio on 23424
Apache is running on 80

I have a dynamic name service setup

I want to be able to access [https://mydomain.com](https://mydomain.com) and have that proxy to the HFS server on port 8080. and then access [https://mydomain.com/mediabroswer](https://mydomain.com/mediabroswer) and that proxy to 23424. I also want it to force SSL so that all clients that connect have to use SSL even though serviio does not.
Sorry if this doesn't make sense

Many thanks

---

