---
title: "BIND9 local zone (LAN pc's)"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by AnvarIT on 2010-02-23
Hello,

I have a little question about setting up a local DNS zone for my internal network.

Situation: 
I want to drop my windows dns box so I installed a Ubuntu Linux on a ALIX board  and on that box I've installed bind9 & webmin (easy GUI)
Now in webmin I configure my outside dns zones for a loopback, example: mail.domainname.com resolves to the local ip of the mailserver. I don't use mailforwarders. And all of these functions work fine.

Now I want to set up my local pc/servers their hostname in bind9
So I've created a new masterzone with the workgroup name I use homenetwork.local, in this zone I've created my hosts and everything works fine. But I also want to connect/ping to a host without typing his full dns name.
So my 1stserver must also be accessible with "1stserver" in stead off "1stserver.homenetwork.local"

Can someone help me out with this,
Thanks
Thomas

---

