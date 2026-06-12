---
title: "How do i access my ubuntu machine from the Internet"
date: 2009-03-22
forum: Networking &amp; Wireless
---

### Post by Avinash.Rao on 2009-03-22
Dear All,

I am using Ubuntu Studio 8.04 on AMD 64-bit with 2 nic's, one connected to the local network and the other connected to the Internet Broadband modem.

My requirement is to connect to this server from the internet, from outside the office. I tried using teamviewer through Wine from a Ubuntu desktop, but it didnt work! Is it mandatory to have a public IP to connect from the internet?? Or is there any other method through which i can connect to my server. 

My server runs the following services.

1) Squid Proxy
2) Samba as PDC + Wins
3) LTSP 
4) DHCP Server

Kindly help
Avinash

---

### Post by Avinash.Rao on 2009-03-23
:)

---

### Post by Bachstelze on 2009-03-23
> **Avinash.Rao said:**
> Is it mandatory to have a public IP to connect from the internet??

Yes, just like it's mandatory to have a post address if you want to recieve mail, or a telephone number if you want to recieve phone calls.

---

### Post by BkkBonanza on 2009-03-23
You can't have an internet connection without a public ip... so you must have one. It could by dynamic and change on you, but yes, you gotta have one.

Try bringing up a page like checkmyip.org from inside your network and it will tell you your ip. But having an ip is not enough to make your servers visible to the public. You will also have to forward a port on your router. And if your ip is dynamic then you will need to use a service like dyndns.org to keep a domain name pointed to your changing ip. Several thinsg need to be in place just to get visible, and then once visible it's wise to secure things so your not too visible.

---

### Post by Avinash.Rao on 2009-03-28
Thanks for the reply.

Let me see how i can get this done.

---

