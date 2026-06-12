---
title: "ip static problem (ask)"
date: 2009-06-11
forum: Networking &amp; Wireless
---

### Post by -genin- on 2009-06-11
hi all...
I got problem with my networking connection...
How can I set my IP to be static...
everytime I reboot... it set to default...:(:(:(
I confused... 

Sry if I repost... I really really need help...

thanks so much...

---

### Post by MaindotC on 2009-06-11
Try "man interfaces".  There are examples in the man page for setting a static address.

---

### Post by W03L on 2009-06-11
/etc/network/interfaces

iface ethX inet static
address ???.???.???.???
netmask ???.???.???.???
gataway ???.???.???.???
auto ethX

/etc/init.d/networking restart

---

### Post by MaindotC on 2009-06-11
Good job!

---

### Post by -genin- on 2009-06-11
is it necessary to remove the network-manager...??

---

### Post by W03L on 2009-06-11
> **-genin- said:**
> is it necessary to remove the network-manager...??

not necessary, but better to remove

---

### Post by -genin- on 2009-06-11
I dont want get any risks... :(:(

I'll remove it...
but.. what else to remove.. just the network-manager??

---

### Post by MaindotC on 2009-06-11
Why remove network manager?

---

### Post by moe19790 on 2009-06-11
> **-genin- said:**
> I dont want get any risks... :(:(

I'll remove it...
but.. what else to remove.. just the network-manager??

yes why you will remove it?

---

### Post by DGortze380 on 2009-06-11
I have not tested it, but I'm told that network-manager in 9.04 will interfere with /etc/network/interfaces.

It is recommended to use the GUI to configure your static IP ... or ... configure via /etc/network/interfaces ... but not to have both on the same system.

---

### Post by cariboo on 2009-06-11
There are several ways to setup a static ip address. 

[list=1]
[*] This is kind of cludgy, but it works. Uninstall the dhcp3-client package.
[*] Using Network-Manager delete you current connection and create a new one with a static ip address.
[*] Remove network-manager-gnome and replace it with gnome-network-admin
[/list]

---

### Post by DGortze380 on 2009-06-11
IMO, the easiest way on a desktop is:

System -> Preferences -> Network Connections
Highlight your connection
Click Edit
Click IPv4 Settings
Choose Manual
Add an Address, Subnet, Gateway, DNS Addresses
Apply

I didn't need any other changes than those above.

On a server, use /etc/network/interfaces

---

### Post by karhoey on 2009-06-13
But I wonder how to set IPv6 static address? If use the preference > network connection in Ubuntu 9.04, then it has no IPv6 setting; but if I use /etc/networks/interfaces, it come out the SIOCDELRT: No such process error...
:(

---

### Post by DGortze380 on 2009-06-13
> **karhoey said:**
> But I wonder how to set IPv6 static address? If use the preference > network connection in Ubuntu 9.04, then it has no IPv6 setting; but if I use /etc/networks/interfaces, it come out the SIOCDELRT: No such process error...
:(

You're using IPv6?? Why?

Your IPv6 Address should be static, as it's based on your MAC Address. If your hardware and driver support it, you should have an address. 

```

ifconfig

```

---

### Post by karhoey on 2009-06-14
hmm, I get a dual-stack connection from my ISP. I get a IPv4 address and IPv6 address. So I have to set them static. This is ok to set the IPv4 static and I can access to Internet using IPv4. 
But the problem is how can I use that IPv6 protocol? I should be able to access ipv6.google.com if I got the dual-stack right? But so far I cant get it..
Anyone know its reason? Thanks..

---

### Post by Iowan on 2009-06-14
**ifconfig** apparently offers an option to set IPv6 address - This came from the **man** page:>        **add addr/prefixlen**
              Add an IPv6 address to an interface.


---

### Post by karhoey on 2009-06-16
Ok, thanks guy.
 
But still I have a problem !! My ISP provide dual-stack, then I had given 2 IP address, one is IPv4 and the another one is IPv6. Both are public/global IP address (as they said to me). But the problem is after I ifconfig my IPv6 into the same ethernet interface with IPv4, I able to go kame.net see the turtle swim only but I can not access to ipv6.google.com.. 
 
Why be like that, pls give me some idea, thankssssss

---

