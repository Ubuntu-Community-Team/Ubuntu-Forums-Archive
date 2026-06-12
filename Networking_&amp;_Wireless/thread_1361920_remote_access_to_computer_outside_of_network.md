---
title: "remote access to computer outside of network"
date: 2009-12-22
forum: Networking &amp; Wireless
---

### Post by severemacaw on 2009-12-22
I am not a guru but I am trying to help a friend install linux host with vista virtual via virtual box. I am looking to access his machine remotely to configure virtual machine for him. Is this possible? If so, any info on how to do so would be greatly appreciated. Thanks

---

### Post by ant2ne on 2009-12-22
> **severemacaw said:**
> I am not a guru but I am trying to help a friend install linux host with vista virtual via virtual box. I am looking to access his machine remotely to configure virtual machine for him. Is this possible? If so, any info on how to do so would be greatly appreciated. Thanks
are you accessing the vista OS or the linux OS? The vista OS can be accessed via logmein.com. I don't know if there is a similar service for linux.

---

### Post by pricetech on 2009-12-22
SSH to remote in to his Linux box.

---

### Post by pricetech on 2009-12-22
SSH to remote in to his Linux box.

But if it works for him like it worked for me, you won't need to.  It just plain worked.

---

### Post by severemacaw on 2009-12-22
> **pricetech said:**
> SSH to remote in to his Linux box.

But if it works for him like it worked for me, you won't need to.  It just plain worked.
how do you ssh into another linux machine? forgive me I have only been using ubuntu for a few months. Thank you for your help. do i need his router info or to open a pin hole in his firewall to access it? He is not computer savvy in any way so Im trying to do most of it for him.

---

### Post by Iowan on 2009-12-23
I suspect the router will need to port forward the SSH connection (port 22 or a non-standard of your choice... to inconvenience the script-kiddies). 
It's also possible that the SSH-server may need to be installed on his machine. (The SSH client is probably pre-installed)

---

### Post by ant2ne on 2009-12-25
most ISP block ports 22 & 23, so you'll need some sort of NAT or VPN to ssh through the internet. I suppose you could install webmin on the remote box then forward port 80 in your router. Which may end up more work than it is worth. I find it hard to believe that there is no logmein service for linux boxes. maybe something that uses ssh via a web gui. I used logmein to fix a friends PC the other day.

---

