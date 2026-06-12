---
title: "need help with a static IP"
date: 2009-10-27
forum: Networking &amp; Wireless
---

### Post by a cup of tea on 2009-10-27
I wanted to set it up so that one of my computers has a static IP, so that I can forward a port to it. I don't know what I did wrong, but now I can't even get it back to the way it was and can't get eth0 working (it was working fine before I did this). 

Help? :(

---

### Post by amingv on 2009-10-27
Please, elaborate on what steps you took to set up the static IP so we can see if it can be reverted or corrected.
Did you edit any config file or used the network manager?
Did you remember to provide an address to your default gateway and dns servers (these often need to be set manually when setting an static IP).

---

### Post by a cup of tea on 2009-10-27
Sorry I didn't elaborate more. I tried using network manager. I thought I couldn't get it working again after that (when I posted), but I was able to get a connection after that, just not static. After that, I tried editing /etc/network/interfaces, and I've added:

```
auto eth0
iface eth0 inet static
address 192.168.2.139
netmask 255.255.255.0
gateway 192.168.2.1
```

192.168.2.1 is the IP address of my router. I know that's kinda odd.

It still didn't work. I then read something that said to uninstall network-manager. Since nothing else worked...I did uninstall network-manager, and now I can't figure out how to get it back because I can't get a connection on that computer. ](*,) I am able to connect to that computer with SSH, from this computer, so I'm sure I just need to find out how to get network-manager from this computer to that one so I can install it there. That won't solve the issue of not having internet through a static IP on that computer though.

I don't have a DNS server.

---

### Post by Iowan on 2009-10-27
Hopefully, you picked an IP address outside the range of your DHCP server... Another option is to set up the DHCP server to issue a static lease - based on MAC address. Machine gets same address, but benefits from other DHCP features (like DNS servers). 

Can you **ping** your router from this machine (by address or name)? How about internet? If address works, but name fails, the DNS server needs to be set up differently (*/etc/resolv.conf*)

---

### Post by a cup of tea on 2009-10-27
I am able to ping my router, but I can't ping the internet.

I don't know what the name of my router is, I just ping it by its address. I think I must have resolv.conf set up wrong, but I don't know what I'm supposed to have there.

---

### Post by Iowan on 2009-10-27
> **a cup of tea said:**
> I am able to ping my router, but I can't ping the internet. Can't ping internet by address? Try 74.125.45.100. You could post your */etc/resolv.conf* - or use OpenDNS (208.67.222.222 and 208.67.220.220)
... or both.

---

### Post by a cup of tea on 2009-10-27
\\:D/

It works now. Even after I tried it with the Open DNS ones, it still didn't work, and I realized I had a typo in the word nameserver. Thank you for your help. Yay!

---

