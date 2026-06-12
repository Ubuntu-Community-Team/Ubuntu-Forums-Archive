---
title: "Laptop ---&gt; Xbox 360"
date: 2009-03-06
forum: Networking &amp; Wireless
---

### Post by kaelonlloyd on 2009-03-06
I am a looking for a way to brige my laptop wireless to my xbox 360. I have done this on windows and i have a dual boot for when i'm on xbox, but i would like to make it work on linux so that i don't have to keep swapping OS's. Can anyone tell me how..BTW i'm a complete and utter noob when it comes to linux,

---

### Post by puppywhacker on 2009-03-06
what is the purpose for connecting your laptop to your xbox? is it filesharing or do you want to reach the internet? or what else?

either way your laptop should have an ip address in the same range as your xbox. with the command "mii-tool" or the lights on the network card you can see that ethernet is working (the lowest level of connection)
with the command "ifconfig" or the Network Manager you can see and set addresses. Once this is done you can use SAMBA for filesharing or iptables masquerading for setting up a NAT.

---

