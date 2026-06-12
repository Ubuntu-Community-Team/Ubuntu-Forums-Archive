---
title: "static ip cannot connect to internet"
date: 2012-04-29
forum: Networking &amp; Wireless
---

### Post by Ericyue on 2012-04-29
hi,

i want to make my machine's ip address to become static, but when i put it to static, it cannot connect to internet . can i know is where i configure wrong ? 

i have right click the wireless icon -> edit connections -> wireless -> choose my wireless -> then go IPv4 -> click add -> set my ip to 192.168.1.104 , netmask to 255.255.255.0 gateway to 192.168.1.1 . 


can anyone tell me what is the problem about ? thanks .

---

### Post by iponeverything on 2012-04-29
connect the normal way using DHCP, go to connection information and make sure that the static your is in the same range.

---

### Post by marinara on 2012-04-30
you have to buy static ips.  you can't just tell ubuntu to use a static ip.  you might look into no-ip.org

---

### Post by lisati on 2012-04-30
I think the OP wants a static private IP address on their local network. 

My preference is to tell my router to reserve a particular IP address for a particular machine, and leave the default settings on the PC well alone. This is partly because it's sometimes easier, and partly because it can help avoid IP address conflicts if I connect one of my laptops to someone else's network.

---

### Post by Ericyue on 2012-05-01
hi , thanks to all the people who reply ...

i now want have a router which will give all the machines private ip (192.168...) 

the gateway is 192.168.1.1
and the subnet mask is 255.255.255.0


i want to set my ubuntu machine to let it have a static ip because i am doing a project which will transfer file to this machine based on ip so i nid to make it static. 


the ip address start from 192.168.1.100 .  So i set my ip to become 192.168.1.104 and subnet mask is 255.255.255.0 and gateway is 192.168.1.1

i dunno y when i set it to static, i can't using internet . i believe that my ip configuration is not wrong. 

Can anyone tell me what is the problem of that ? 

thanks in advance ..

---

### Post by marinara on 2012-05-02
you can't set it to static.  it does not work that way.  it really does not work that way.  go talk to the router [I]Manufacturers if you dont believe me
[/I]

---

### Post by iponeverything on 2012-05-02
> **marinara said:**
> you can't set it to static.  it does not work that way.  it really does not work that way.  go talk to the router [I]Manufacturers if you dont believe me
[/I]

bad advice abounds.

---

### Post by kalehrl on 2012-05-02
Have you entered your router ip in /etc/resolv.conf?
The syntax is:
```
 nameserver 192.168.x.x
```

---

### Post by SeijiSensei on 2012-05-02
Assign a static address that's outside the range of addresses being distributed by DHCP.  If you don't do this, you create the possibility of an address conflict on the network.  So if the router is assigning addresses in 192.168.1.100-199, give your machine an address like 192.168.1.50.

You'll need to set the default gateway to 192.168.1.1 and, as kalehrl says, point your DNS at that address as well.

Once you've assigned the address make sure you can ping the router with "ping 192.168.1.1".

---

### Post by chili555 on 2012-05-02
> **marinara said:**
> you can't set it to static.  it does not work that way.  it really does not work that way.  go talk to the router [I]Manufacturers if you dont believe me
[/I]Untrue. I use static IPs and have so on many routers for many years.

---

### Post by Ericyue on 2012-05-06
thanks for alll for the reply .. 

[SeijiSensei]("http://ubuntuforums.org/member.php?u=698195") : i have set it like the way u say but i still cannot connect to internet when i set ip to static . i have attached the image for my router setting and also the internet connection setting . please have a look and give me advice .. thanks in advance

---

### Post by ammofreak on 2012-05-07
Hi ):P
Did you set you DHCP Reservation on the router to 192.168.1.50 along with host name & MAC? And, for now, until IPv6 becomes prominent, I set it to Ignore. Hope this helps...:)

---

### Post by Dennis N on 2012-05-07
> **Ericyue said:**
> .. i have set it like the way u say but i still cannot connect to internet when i set ip to static . i have attached the image for my router setting and also the internet connection setting . please have a look and give me advice .. thanks in advance

Since you selected manual configuration, you need to fill in a DNS server IP address in the box - the computer needs to know where to send the IP address request - use either the gateway (router) or another DNS server, such as Google DNS for example.

Google DNS servers: fill in 8.8.8.8, 8.8.4.4

---

